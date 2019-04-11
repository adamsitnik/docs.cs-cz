---
title: Odchylky obecných rozhraní (C#)
ms.date: 04/10/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 5874a39a57f85695bedc3d1ffa61adf19fcdbe37
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480778"
---
# <a name="variance-in-generic-interfaces-c"></a>Odchylky obecných rozhraní (C#)

Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní. Podpora Variance umožňuje implicitní převod z třídy, které implementují tato rozhraní. 

Rovnou začít tématem rozhraní .NET Framework 4, jsou následující rozhraní variant:

- <xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)

- <xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)

- <xref:System.Linq.IQueryable%601> (T je kovariantní)

- <xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní.)

- <xref:System.Collections.Generic.IComparer%601> (T je kontravariantní.)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní.)

- <xref:System.IComparable%601> (T je kontravariantní.)

Od verze rozhraní .NET Framework 4.5, jsou následující rozhraní variant:

- <xref:System.Collections.Generic.IReadOnlyList%601> (T je kontravariantní.)

- <xref:System.Collections.Generic.IReadOnlyCollection%601> (T je kontravariantní.)

Kovariance povoluje metoda může mít více odvozený návratový typ, než je definován parametr obecného typu rozhraní. K ilustraci této funkce kovariance, vezměte v úvahu těmito obecnými rozhraními: `IEnumerable<Object>` a `IEnumerable<String>`. `IEnumerable<String>` Rozhraní nedědí `IEnumerable<Object>` rozhraní. Ale `String` typ dědit `Object` typ a v některých případech můžete chtít přiřadit objekty z těchto rozhraní k sobě navzájem. To je ukázáno v následujícím příkladu kódu.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v C# a v případě `Option Strict` nachází v jazyce Visual Basic. Nyní můžete použít, ale `strings` místo `objects`, jak je znázorněno v předchozím příkladu, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariantní.

Kontravariance umožní metoda může mít typy argumentů, které jsou méně odvozený než je určeno obecný parametr rozhraní. Pro ilustraci kontravariance se předpokládá, že jste vytvořili `BaseComparer` třídy k porovnání instance `BaseClass` třídy. `BaseComparer` Implementuje třída `IEqualityComparer<BaseClass>` rozhraní. Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je kontravariantní, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy. To je ukázáno v následujícím příkladu kódu.

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).

Odchylky obecných rozhraní je podporována pouze pro typy odkazů. Typy hodnot nepodporují variance. Například `IEnumerable<int>` nejde implicitně převést na `IEnumerable<object>`, protože celá čísla jsou reprezentovány hodnotového typu.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Taky je dobré si uvědomit, že jsou stále invariantní třídy, které implementují rozhraní variant. Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List<Object>` k `List<String>`. To je znázorněno v následujícím příkladu kódu.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Viz také:

- [Použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Vytváření variantních obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Obecná rozhraní](../../../../standard/generics/interfaces.md)
- [Odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
