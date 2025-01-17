---
title: 'Postupy: Načtení hodnoty elementu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: a7b36ea7bb602c241593da356b87d35baee8163f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253355"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Postupy: Načtení hodnoty elementu (LINQ to XML) (C#)
Toto téma ukazuje, jak získat hodnotu prvků. Existují dva hlavní způsoby. Jedním ze <xref:System.Xml.Linq.XElement> způsobů je přetypování <xref:System.Xml.Linq.XAttribute> nebo na požadovaný typ. Operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ a přiřadí ho k proměnné. Alternativně můžete použít <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> nebo vlastnost.  
  
 C#Nicméně přetypování je všeobecně lepším přístupem. Pokud přetypování elementu nebo atributu na typ s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty prvku (nebo atributu), který může nebo nemusí existovat. Příklad ukazuje poslední příklad v tomto tématu. Nemůžete však nastavit obsah elementu prostřednictvím přetypování, jak můžete prostřednictvím <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti.  
  
## <a name="example"></a>Příklad  
 Chcete-li načíst hodnotu prvku, stačí přetypování <xref:System.Xml.Linq.XElement> objektu na požadovaný typ. Můžete vždy přetypování elementu na řetězec, a to následujícím způsobem:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Příklad  
 Prvky lze také přetypovat na jiné typy než řetězec. Například pokud máte prvek, který obsahuje celé číslo, můžete jej přetypovat na `int`, jak je znázorněno v následujícím kódu:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje operátory explicitního přetypování pro následující datové typy `string`: `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`,, `ulong?`, ,`float` ,,`double?`, ,`decimal?`,,,, ,`TimeSpan?`a `decimal` `DateTime` `DateTime?` `TimeSpan` `double` `float?` `GUID` `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje stejné operátory přetypování pro <xref:System.Xml.Linq.XAttribute> objekty.  
  
## <a name="example"></a>Příklad  
 <xref:System.Xml.Linq.XElement.Value%2A> Vlastnost můžete použít k načtení obsahu prvku:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Příklad  
 Někdy se pokusíte načíst hodnotu prvku, i když si nejste jistí, že existuje. V tomto případě, když přiřadíte přetypováníný element na typ s možnou `string` hodnotou null (nebo jeden z typů s možnou hodnotou null v .NET Framework), pokud element neexistuje, přiřazená proměnná je `null`pouze nastavena na. Následující kód ukazuje, že pokud element může nebo nemusí existovat, je snazší použít přetypování, než aby bylo možné použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 Tento kód generuje následující výstup:  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Obecně lze psát jednodušší kód při použití přetypování k načtení obsahu prvků a atributů.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
