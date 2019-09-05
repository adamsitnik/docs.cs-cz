---
title: 'Postupy: Zápis dotazů s komplexním filtrováním (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 7759a02c1b9ef0ae0c1af4bfb2600543b21cdf0f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253193"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="2bf12-102">Postupy: Zápis dotazů s komplexním filtrováním (C#)</span><span class="sxs-lookup"><span data-stu-id="2bf12-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="2bf12-103">Někdy budete chtít zapisovat LINQ to XML dotazy se složitými filtry.</span><span class="sxs-lookup"><span data-stu-id="2bf12-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="2bf12-104">Například může být nutné najít všechny prvky, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="2bf12-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="2bf12-105">Toto téma poskytuje příklad zápisu dotazu se složitým filtrováním.</span><span class="sxs-lookup"><span data-stu-id="2bf12-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bf12-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bf12-106">Example</span></span>  
 <span data-ttu-id="2bf12-107">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut se rovná "dodávání" a `State` podřízený element se rovná "ny".</span><span class="sxs-lookup"><span data-stu-id="2bf12-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="2bf12-108">Používá vnořený dotaz v `Where` klauzuli `Any` a operátor vrátí `true` , pokud má kolekce nějaké prvky.</span><span class="sxs-lookup"><span data-stu-id="2bf12-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="2bf12-109">Informace o použití syntaxe dotazů založených na metodách naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2bf12-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="2bf12-110">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2bf12-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2bf12-111">Další informace o `Any` operátoru najdete v tématu [operace kvantifikátoru (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2bf12-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="2bf12-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2bf12-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="2bf12-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bf12-113">Example</span></span>  
 <span data-ttu-id="2bf12-114">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2bf12-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="2bf12-115">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2bf12-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2bf12-116">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Několik nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2bf12-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="2bf12-117">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2bf12-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bf12-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bf12-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="2bf12-119">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="2bf12-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="2bf12-120">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="2bf12-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
