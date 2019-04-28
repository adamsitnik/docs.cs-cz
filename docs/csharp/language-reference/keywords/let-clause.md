---
title: let – klauzule - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 941ad41d75e14420699022a07bd6a3b10d83c896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661253"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="263e6-102">let – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="263e6-102">let clause (C# Reference)</span></span>

<span data-ttu-id="263e6-103">Ve výrazu dotazu je někdy užitečné ukládat výsledek dílčí výraz. Chcete-li použít v následných klauzulí.</span><span class="sxs-lookup"><span data-stu-id="263e6-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="263e6-104">Můžete to provedete `let` – klíčové slovo, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu zadáte.</span><span class="sxs-lookup"><span data-stu-id="263e6-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="263e6-105">Po inicializaci s hodnotou proměnné rozsahu nelze použít pro ukládání hodnoty horní jiný.</span><span class="sxs-lookup"><span data-stu-id="263e6-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="263e6-106">Nicméně pokud proměnnou rozsahu obsahuje dotazovatelný typ, může být dotazován.</span><span class="sxs-lookup"><span data-stu-id="263e6-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="263e6-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="263e6-107">Example</span></span>

<span data-ttu-id="263e6-108">V následujícím příkladu `let` slouží dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="263e6-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="263e6-109">Chcete-li vytvořit Výčtový typ, který je sám možné zadávat dotazy.</span><span class="sxs-lookup"><span data-stu-id="263e6-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="263e6-110">Povolit dotaz tak, aby volání `ToLower` pouze jednou na proměnnou rozsahu `word`.</span><span class="sxs-lookup"><span data-stu-id="263e6-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="263e6-111">Bez použití `let`, budete muset volat `ToLower` v každé predikátu v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="263e6-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="263e6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="263e6-112">See also</span></span>

- [<span data-ttu-id="263e6-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="263e6-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="263e6-114">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="263e6-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="263e6-115">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="263e6-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="263e6-116">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="263e6-116">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="263e6-117">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="263e6-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)