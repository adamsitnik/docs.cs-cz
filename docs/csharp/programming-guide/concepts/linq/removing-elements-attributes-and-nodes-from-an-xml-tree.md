---
title: Odebrání elementů, atributů a uzlů ze stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: f3091c3f46d8b3283c961fffd4d1f0ce991083ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711977"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="95d75-102">Odebrání elementů, atributů a uzlů ze stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="95d75-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>
<span data-ttu-id="95d75-103">Můžete upravit stromu XML, odebrání elementů, atributů a dalších typů uzlů.</span><span class="sxs-lookup"><span data-stu-id="95d75-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="95d75-104">Odebrání jeden element nebo jeden atribut z dokumentu XML je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="95d75-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="95d75-105">Ale při odstraňování kolekce elementy nebo atributy, musí nejprve sloučit kolekci do seznamu a pak odstraníte elementy nebo atributy ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="95d75-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="95d75-106">Nejlepší možností je použít <xref:System.Xml.Linq.Extensions.Remove%2A> metodu rozšíření, která to udělal za vás.</span><span class="sxs-lookup"><span data-stu-id="95d75-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="95d75-107">Hlavním důvodem pro to je, že jsou výsledkem většinu kolekce, které se načítají ze stromu XML pomocí odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="95d75-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="95d75-108">Pokud jste není nejprve materializovat je do seznamu, nebo pokud používáte metody rozšíření, je možné se setkat se třídy chyb.</span><span class="sxs-lookup"><span data-stu-id="95d75-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="95d75-109">Další informace najdete v tématu [smíšené deklarativní kód/dnešní kód chyby (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="95d75-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="95d75-110">Následující metody odebrání uzlů a atributy ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="95d75-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="95d75-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="95d75-111">Method</span></span>|<span data-ttu-id="95d75-112">Popis</span><span class="sxs-lookup"><span data-stu-id="95d75-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-113">Odebere <xref:System.Xml.Linq.XAttribute> od svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="95d75-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-114">Odebere podřízené uzly ze <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="95d75-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-115">Odstraní obsah a atributy ze <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95d75-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-116">Odebere atributy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95d75-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-117">Pokud předáte `null` pro hodnotu, pak taky odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="95d75-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-118">Pokud předáte `null` pro hodnotu, pak taky odebere podřízený element.</span><span class="sxs-lookup"><span data-stu-id="95d75-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-119">Odebere <xref:System.Xml.Linq.XNode> od svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="95d75-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="95d75-120">Odebere každý atribut nebo element ve zdrojové kolekci ze svého nadřízeného elementu.</span><span class="sxs-lookup"><span data-stu-id="95d75-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95d75-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="95d75-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="95d75-122">Popis</span><span class="sxs-lookup"><span data-stu-id="95d75-122">Description</span></span>  
 <span data-ttu-id="95d75-123">Tento příklad ukazuje tři přístupy k odebrání prvků.</span><span class="sxs-lookup"><span data-stu-id="95d75-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="95d75-124">Nejprve se odebere jeden element.</span><span class="sxs-lookup"><span data-stu-id="95d75-124">First, it removes a single element.</span></span> <span data-ttu-id="95d75-125">Za druhé, načte kolekci elementů, bude je realizována pomocí <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operátorů a odebere kolekce.</span><span class="sxs-lookup"><span data-stu-id="95d75-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="95d75-126">A konečně, načte kolekci elementů a odebere je pomocí <xref:System.Xml.Linq.Extensions.Remove%2A> – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="95d75-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="95d75-127">Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru, naleznete v tématu [převádění datových typů (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="95d75-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="95d75-128">Kód</span><span class="sxs-lookup"><span data-stu-id="95d75-128">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
    <Child1>  
        <GrandChild1/>  
        <GrandChild2/>  
        <GrandChild3/>  
    </Child1>  
    <Child2>  
        <GrandChild4/>  
        <GrandChild5/>  
        <GrandChild6/>  
    </Child2>  
    <Child3>  
        <GrandChild7/>  
        <GrandChild8/>  
        <GrandChild9/>  
    </Child3>  
</Root>");  
root.Element("Child1").Element("GrandChild1").Remove();  
root.Element("Child2").Elements().ToList().Remove();  
root.Element("Child3").Elements().Remove();  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="95d75-129">Komentáře</span><span class="sxs-lookup"><span data-stu-id="95d75-129">Comments</span></span>  
 <span data-ttu-id="95d75-130">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="95d75-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="95d75-131">Všimněte si, že první podřízený element byl odebrán z `Child1`.</span><span class="sxs-lookup"><span data-stu-id="95d75-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="95d75-132">Všechny podřízené prvky byly odebrány z `Child2` a z `Child3`.</span><span class="sxs-lookup"><span data-stu-id="95d75-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d75-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95d75-133">See also</span></span>

- [<span data-ttu-id="95d75-134">Změna stromů XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="95d75-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
