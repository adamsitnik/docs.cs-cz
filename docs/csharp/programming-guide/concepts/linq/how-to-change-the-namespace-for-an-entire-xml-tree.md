---
title: 'Postupy: Změnit Namespace pro celý strom XML (C#)'
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 020d072cfb58c90720317734199d241c6892511f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668182"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="54905-102">Postupy: Změnit Namespace pro celý strom XML (C#)</span><span class="sxs-lookup"><span data-stu-id="54905-102">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>
<span data-ttu-id="54905-103">Někdy nutné programově změnit obor názvů pro element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="54905-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="54905-104">Technologie LINQ to XML to výrazně usnadňuje.</span><span class="sxs-lookup"><span data-stu-id="54905-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="54905-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> Vlastnost lze nastavit.</span><span class="sxs-lookup"><span data-stu-id="54905-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="54905-106"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> Vlastnost nelze nastavit, ale můžete snadno zkopírovat do atributy <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, odeberte existující atributy a pak přidejte nové atributy, které jsou v novém požadovaného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="54905-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="54905-107">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="54905-107">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54905-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="54905-108">Example</span></span>  
 <span data-ttu-id="54905-109">Následující kód vytvoří dvě stromů XML v žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="54905-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="54905-110">Poté změní obor názvů všech stromů a kombinuje je do jediného stromu.</span><span class="sxs-lookup"><span data-stu-id="54905-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```csharp  
XElement tree1 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XElement tree2 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace ad = "http://www.adatum.com";  
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="54905-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="54905-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54905-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54905-112">See also</span></span>

- [<span data-ttu-id="54905-113">Změna stromů XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="54905-113">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
