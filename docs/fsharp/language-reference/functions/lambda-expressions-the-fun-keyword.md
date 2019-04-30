---
title: 'Výrazy lambda: Klíčové slovo fun'
description: Další informace o použití F# "zábavu" – klíčové slovo k definování výraz lambda, který je anonymní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 6ad15173bb8643bff330e3ca3823cba5d43ad445
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941021"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="e2150-103">Výrazy lambda: Klíčové slovo fun (F#)</span><span class="sxs-lookup"><span data-stu-id="e2150-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="e2150-104">`fun` – Klíčové slovo se používá k definování výraz lambda, to znamená, anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="e2150-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2150-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2150-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="e2150-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2150-106">Remarks</span></span>

<span data-ttu-id="e2150-107">*Seznam parametrů* se obvykle skládá z názvů a volitelně typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="e2150-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="e2150-108">Obecně platí *seznam parametrů* může skládat z libovolné F# vzory.</span><span class="sxs-lookup"><span data-stu-id="e2150-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="e2150-109">Úplný seznam možných vzory, naleznete v tématu [porovnávání vzorů](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="e2150-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="e2150-110">Seznam platných parametrů zahrnují následující příklady.</span><span class="sxs-lookup"><span data-stu-id="e2150-110">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="e2150-111">*Výraz* tělo funkce posledního výrazu z nich generuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e2150-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="e2150-112">Příklady výrazů lambda platné patří:</span><span class="sxs-lookup"><span data-stu-id="e2150-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="e2150-113">Používání výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="e2150-113">Using Lambda Expressions</span></span>

<span data-ttu-id="e2150-114">Výrazy lambda jsou zvláště užitečné, pokud chcete provádět operace v seznamu nebo z jiné kolekce a chcete se vyhnout nadbytečné práci spojené se definice funkce.</span><span class="sxs-lookup"><span data-stu-id="e2150-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="e2150-115">Mnoho F# přijmout hodnoty funkcí jako argumenty funkce knihovny, a může být zvláště praktické použití lambda výrazů v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="e2150-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="e2150-116">Následující kód platí pro prvky seznamu výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="e2150-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="e2150-117">V takovém případě anonymní funkce přičte 1 k každý prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="e2150-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="e2150-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2150-118">See also</span></span>

- [<span data-ttu-id="e2150-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="e2150-119">Functions</span></span>](index.md)