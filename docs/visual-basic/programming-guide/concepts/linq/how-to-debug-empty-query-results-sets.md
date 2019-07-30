---
title: 'Postupy: Ladit prázdné sady výsledků dotazu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 076e7109dc89294ba0c1706bf9a66120e6a0b85d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630975"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="41fb3-102">Postupy: Ladit prázdné sady výsledků dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41fb3-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="41fb3-103">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="41fb3-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="41fb3-104">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů a je dotaz na něj nesprávně.</span><span class="sxs-lookup"><span data-stu-id="41fb3-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="41fb3-105">Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="41fb3-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="41fb3-106">Další informace najdete v tématu [práce s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="41fb3-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>

## <a name="example"></a><span data-ttu-id="41fb3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="41fb3-107">Example</span></span>

<span data-ttu-id="41fb3-108">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="41fb3-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="41fb3-109">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="41fb3-109">This example produces the following result:</span></span>

```
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="41fb3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="41fb3-110">Example</span></span>

<span data-ttu-id="41fb3-111">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.</span><span class="sxs-lookup"><span data-stu-id="41fb3-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="41fb3-112">Řešením je deklarovat a inicializovat globální výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="41fb3-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="41fb3-113">Tím se umístí všechny vlastnosti XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="41fb3-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="41fb3-114">V příkladu nejsou k dispozici žádné další úpravy, aby mohla správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="41fb3-114">No other modifications are required to the example to make it work properly.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="41fb3-115">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="41fb3-115">This example produces the following result:</span></span>

```
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="41fb3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41fb3-116">See also</span></span>

- [<span data-ttu-id="41fb3-117">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41fb3-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
