---
title: Where – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 5632e69039baebb3d1f1fd90c04586d9e50fe40f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834501"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="5277d-102">Where – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5277d-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="5277d-103">Určuje podmínku filtrování dotazu.</span><span class="sxs-lookup"><span data-stu-id="5277d-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5277d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5277d-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="5277d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="5277d-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="5277d-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5277d-106">Required.</span></span> <span data-ttu-id="5277d-107">Výraz, který určuje, zda hodnoty pro aktuální položku v kolekci jsou zahrnuty v kolekci výstup.</span><span class="sxs-lookup"><span data-stu-id="5277d-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="5277d-108">Výraz se musí vyhodnotit na `Boolean` hodnotu nebo ekvivalent `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5277d-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="5277d-109">Pokud je podmínka vyhodnocena jako `True`elementu je zahrnut ve výsledku dotazu; jinak vrátí hodnotu, elementu je vyloučen z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="5277d-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5277d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5277d-110">Remarks</span></span>  
 <span data-ttu-id="5277d-111">`Where` Klauzule umožňuje filtrovat dotaz na data tak, že vyberete pouze prvky, které splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="5277d-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="5277d-112">Elementy způsobovat jehož hodnoty `Where` klauzule vyhodnotilo `True` jsou zahrnuty ve výsledku dotazu; další prvky jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="5277d-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="5277d-113">Výraz, který se používá v `Where` klauzule se musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean`, například celé číslo, které se vyhodnotí jako `False` když jeho hodnota je nula.</span><span class="sxs-lookup"><span data-stu-id="5277d-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="5277d-114">Můžete zkombinovat více výrazů v `Where` klauzule pomocí logických operátorů `And`, `Or`, `AndAlso`, `OrElse`, `Is`, a `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="5277d-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="5277d-115">Ve výchozím nastavení, se nevyhodnocují – výrazy dotazů, dokud jsou přístupné – například když jsou vázané na data nebo v iterovaném prostřednictvím `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="5277d-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="5277d-116">V důsledku toho `Where` klauzule není vyhodnocen, dokud dotaz přistupuje.</span><span class="sxs-lookup"><span data-stu-id="5277d-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="5277d-117">Pokud máte hodnoty pro dotaz, který se používají v externí `Where` klauzule, zajistit, aby používal odpovídající hodnotu v `Where` klauzule v době spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="5277d-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="5277d-118">Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="5277d-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="5277d-119">Bude možné volat funkce v rámci `Where` k provedení výpočtu nebo operace na základě hodnot z aktuální prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5277d-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="5277d-120">Volání funkce `Where` klauzule může způsobit provedení okamžitě, když je definována místo při přístupu k dotazu.</span><span class="sxs-lookup"><span data-stu-id="5277d-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="5277d-121">Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="5277d-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5277d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5277d-122">Example</span></span>  
 <span data-ttu-id="5277d-123">Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `cust` pro každou `Customer` objekt `customers` kolekce.</span><span class="sxs-lookup"><span data-stu-id="5277d-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="5277d-124">`Where` Klauzule používá proměnnou rozsahu omezení výstup pro zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="5277d-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="5277d-125">`For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="5277d-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="5277d-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="5277d-126">Example</span></span>  
 <span data-ttu-id="5277d-127">Následující příklad používá `And` a `Or` logické operátory při `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5277d-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="5277d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5277d-128">See also</span></span>

- [<span data-ttu-id="5277d-129">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5277d-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="5277d-130">Dotazy</span><span class="sxs-lookup"><span data-stu-id="5277d-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="5277d-131">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="5277d-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="5277d-132">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="5277d-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="5277d-133">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="5277d-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
