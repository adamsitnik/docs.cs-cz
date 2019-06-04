---
title: 'Postupy: Filtrování názvů elementů (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 18100e1097eca52531d28fac2eb6da18446204ef
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485701"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="d0f6a-102">Postupy: Filtrování názvů elementů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0f6a-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d0f6a-103">Při volání jedné z metod, které vracejí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, můžete filtrovat podle názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="d0f6a-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0f6a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0f6a-104">Example</span></span>  
 <span data-ttu-id="d0f6a-105">Tento příklad načte soubor následníky, které se filtruje tak, aby obsahovala pouze následníky se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="d0f6a-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="d0f6a-106">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="d0f6a-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="d0f6a-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d0f6a-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="d0f6a-108">Jiné metody, které vracejí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekce postupují stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d0f6a-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="d0f6a-109">Jejich podpisy jsou podobné <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0f6a-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="d0f6a-110">Následuje úplný seznam metod, které mají podobné podpisy metod:</span><span class="sxs-lookup"><span data-stu-id="d0f6a-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="d0f6a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0f6a-111">Example</span></span>  
 <span data-ttu-id="d0f6a-112">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d0f6a-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d0f6a-113">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d0f6a-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d0f6a-114">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="d0f6a-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="d0f6a-115">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d0f6a-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0f6a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0f6a-116">See also</span></span>

- [<span data-ttu-id="d0f6a-117">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d0f6a-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
