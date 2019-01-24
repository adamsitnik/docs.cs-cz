---
title: 'Postupy: Vytváření dotazů s komplexním filtrováním (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 847e50cf0c1cf91f8b731457d351bb0d01d725c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700582"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="44440-102">Postupy: Vytváření dotazů s komplexním filtrováním (C#)</span><span class="sxs-lookup"><span data-stu-id="44440-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="44440-103">Někdy budete chtít napsat LINQ dotazy XML se složitějšími filtry.</span><span class="sxs-lookup"><span data-stu-id="44440-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="44440-104">Například budete muset najít všechny elementy, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="44440-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="44440-105">V tomto tématu poskytuje příklad zápisu dotazů s komplexním filtrováním.</span><span class="sxs-lookup"><span data-stu-id="44440-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44440-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="44440-106">Example</span></span>  
 <span data-ttu-id="44440-107">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut rovná "Přesouvání" a podřízená `State` prvek s hodnotou "USA".</span><span class="sxs-lookup"><span data-stu-id="44440-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="44440-108">Používá vnořené dotaz v `Where` klauzule a `Any` operátor vrátí `true` Pokud kolekce obsahuje všechny prvky v ní.</span><span class="sxs-lookup"><span data-stu-id="44440-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="44440-109">Informace o použití syntaxe dotazů založených na volání metody, naleznete v tématu [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="44440-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="44440-110">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="44440-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="44440-111">Další informace o `Any` operátoru, naleznete v tématu [operace kvantifikátoru (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="44440-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where   
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="44440-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44440-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="44440-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="44440-113">Example</span></span>  
 <span data-ttu-id="44440-114">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44440-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="44440-115">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="44440-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="44440-116">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="44440-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="44440-117">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44440-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="44440-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44440-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="44440-119">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="44440-119">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="44440-120">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="44440-120">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="44440-121">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="44440-121">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
