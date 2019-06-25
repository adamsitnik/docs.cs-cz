---
title: 'Postupy: Implementace lehké třídy s automaticky implementovanými vlastnostmi - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 5f3e7b831f701145caa1a4fb50f6bb1a4ece4103
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347759"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="8a4cc-102">Postupy: Implementace lehké třídy s automaticky implementovanými vlastnostmi (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="8a4cc-102">How to: Implement a Lightweight Class with Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="8a4cc-103">Tento příklad ukazuje, jak vytvořit neměnné lehké třídy, která slouží pouze k zapouzdření sadu automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="8a4cc-104">Použijte tento druh konstrukce místo struktury, pokud musíte použít odkazové sémantiky typu.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>  
  
 <span data-ttu-id="8a4cc-105">Neměnné vlastnosti můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="8a4cc-105">You can make an immutable property in two ways:</span></span>
  - <span data-ttu-id="8a4cc-106">Lze deklarovat [nastavit](../../../csharp/language-reference/keywords/set.md) přístupového objektu bude [privátní](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="8a4cc-106">You can declare the [set](../../../csharp/language-reference/keywords/set.md) accessor to be [private](../../../csharp/language-reference/keywords/private.md).</span></span>  <span data-ttu-id="8a4cc-107">Vlastnost je pouze nastavitelné v rámci typu, ale je neměnný spotřebitelům.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-107">The property is only settable within the type, but it is immutable to consumers.</span></span>  
    
    <span data-ttu-id="8a4cc-108">Pokud deklarujete privátní `set` přístupový objekt, nelze použít inicializátor objektu k inicializaci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-108">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="8a4cc-109">Je nutné použít konstruktor nebo výrobní metoda.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-109">You must use a constructor or a factory method.</span></span>  
  - <span data-ttu-id="8a4cc-110">Je možné deklarovat pouze [získat](../../../csharp/language-reference/keywords/get.md) přístupový objekt, takže je vlastnost neměnné všude s výjimkou v konstruktoru typu.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-110">You can declare only the [get](../../../csharp/language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type’s constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a4cc-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a4cc-111">Example</span></span>  
 <span data-ttu-id="8a4cc-112">Následující příklad ukazuje dva způsoby, jak implementovat neměnné třídy, která má automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-112">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="8a4cc-113">Jednotlivé možnosti přinesou deklaruje jednu z vlastností s privátní `set` a jedna z vlastností s `get` pouze.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-113">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="8a4cc-114">První třídy používá konstruktor pouze k inicializaci vlastností a druhá třída používá statický objekt pro vytváření metodu, která volá konstruktor.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-114">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>  
  
```csharp  
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only properties.
    public string Name { get; }
    public string Address { get; private set; }

    // Public constructor.
    public Contact(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }
}

// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// static method and private constructor to initialize its properties.
public class Contact2
{
    // Read-only properties.
    public string Name { get; private set; }
    public string Address { get; }

    // Private constructor.
    private Contact2(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }

    // Public factory method.
    public static Contact2 CreateContact(string name, string address)
    {
        return new Contact2(name, address);
    }
}

public class Program
{
    static void Main()
    {
        // Some simple data sources.
        string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",
                            "Cesar Garcia", "Debra Garcia"};
        string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",
                                "12 108th St.", "89 E. 42nd St."};

        // Simple query to demonstrate object creation in select clause.
        // Create Contact objects by using a constructor.
        var query1 = from i in Enumerable.Range(0, 5)
                    select new Contact(names[i], addresses[i]);

        // List elements cannot be modified by client code.
        var list = query1.ToList();
        foreach (var contact in list)
        {
            Console.WriteLine("{0}, {1}", contact.Name, contact.Address);
        }

        // Create Contact2 objects by using a static factory method.
        var query2 = from i in Enumerable.Range(0, 5)
                        select Contact2.CreateContact(names[i], addresses[i]);

        // Console output is identical to query1.
        var list2 = query2.ToList();

        // List elements cannot be modified by client code.
        // CS0272:
        // list2[0].Name = "Eugene Zabokritski";

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
  
/* Output:  
    Terry Adams, 123 Main St.  
    Fadi Fakhouri, 345 Cypress Ave.  
    Hanying Feng, 678 1st Ave  
    Cesar Garcia, 12 108th St.  
    Debra Garcia, 89 E. 42nd St.  
*/  
```  
  
 <span data-ttu-id="8a4cc-115">Kompilátor vytvoří pole zálohování pro jednotlivé automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-115">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="8a4cc-116">Pole nejsou přístupné přímo ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="8a4cc-116">The fields are not accessible directly from source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a4cc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a4cc-117">See also</span></span>

- [<span data-ttu-id="8a4cc-118">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8a4cc-118">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="8a4cc-119">struct</span><span class="sxs-lookup"><span data-stu-id="8a4cc-119">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)
- [<span data-ttu-id="8a4cc-120">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="8a4cc-120">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
