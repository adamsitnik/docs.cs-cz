---
title: Výkon zřetězených dotazů (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 1301a8142ab1a8f793dc30f37c50aa45c2cd9a2a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484112"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="b3858-102">Výkon zřetězených dotazů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b3858-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b3858-103">Jednou z vašich nejdůležitějších výhod LINQ (a LINQ to XML) je, že zřetězených dotazů můžete provádět i pomocí jediného dotazu větší a složitější.</span><span class="sxs-lookup"><span data-stu-id="b3858-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="b3858-104">Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj.</span><span class="sxs-lookup"><span data-stu-id="b3858-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="b3858-105">Například v následujícím jednoduchého kódu `query2` má `query1` jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="b3858-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 <span data-ttu-id="b3858-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b3858-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="b3858-107">Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="b3858-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
- <span data-ttu-id="b3858-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Osy je v podstatě stejný výkon jako iterace propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="b3858-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="b3858-109"><xref:System.Xml.Linq.XContainer.Elements%2A> je implementován jako iterátor s odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="b3858-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="b3858-110">To znamená, že nemusí nějakou práci navíc iterace propojeného seznamu, například přidělování objekt iterátoru a sledování stavu spuštění.</span><span class="sxs-lookup"><span data-stu-id="b3858-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="b3858-111">Tuto práci je možné rozdělit do dvou kategorií: práce, která se provádí v době iterátor nastaven a práce, která se provádí při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="b3858-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="b3858-112">Nastavení je malý, pevné množství práce a práci při každé iteraci je přímo úměrný počtu položek v kolekci zdroje.</span><span class="sxs-lookup"><span data-stu-id="b3858-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
- <span data-ttu-id="b3858-113">V `query1`, `where` klauzule dotazu pro volání způsobí, že <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3858-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="b3858-114">Tato metoda je také implementováno jako iterátor.</span><span class="sxs-lookup"><span data-stu-id="b3858-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="b3858-115">Nastavení se skládá z vytvoření instance delegáta, který bude odkazovat na výraz lambda, a navíc normální instalace iterátor.</span><span class="sxs-lookup"><span data-stu-id="b3858-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="b3858-116">S každou iterací delegáta je volána k provedení predikát.</span><span class="sxs-lookup"><span data-stu-id="b3858-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="b3858-117">Instalační program práce a práce při každé iteraci je podobný práci během iterace na ose.</span><span class="sxs-lookup"><span data-stu-id="b3858-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
- <span data-ttu-id="b3858-118">V `query1`, klauzule select způsobí, že dotaz tak, aby volání <xref:System.Linq.Enumerable.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3858-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="b3858-119">Tato metoda má stejný profil výkonu, jako <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3858-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
- <span data-ttu-id="b3858-120">V `query2`, obojí `where` klauzule a `select` klauzule mají stejný profil výkonu jako v `query1`.</span><span class="sxs-lookup"><span data-stu-id="b3858-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="b3858-121">Iterace přes `query2` tedy přímo úměrné k počet položek ve zdroji prvního dotazu jinými slovy, lineárním čase.</span><span class="sxs-lookup"><span data-stu-id="b3858-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="b3858-122">Odpovídající příklad jazyka Visual Basic by měla mít stejný profil výkonu.</span><span class="sxs-lookup"><span data-stu-id="b3858-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="b3858-123">Další informace o iterátorech naleznete v tématu [yield](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="b3858-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="b3858-124">Podrobnější kurz na zřetězení dotazů, najdete v tématu [kurzu: Zřetězení dotazů](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b3858-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
