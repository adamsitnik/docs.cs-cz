---
title: BREAK – příkaz - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 18be5171329dd43c419e977a1799e2e72c32404d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727570"
---
# <a name="break-c-reference"></a><span data-ttu-id="e51b2-102">break (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e51b2-102">break (C# Reference)</span></span>

<span data-ttu-id="e51b2-103">`break` Příkaz ukončí nejbližší uzavírající smyčka. nebo [přepnout](../../../csharp/language-reference/keywords/switch.md) příkazu, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="e51b2-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="e51b2-104">Řízení je předáno příkazu, který následuje ukončený příkaz, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="e51b2-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="e51b2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e51b2-105">Example</span></span>

<span data-ttu-id="e51b2-106">V tomto příkladu obsahuje podmíněný příkaz čítač, který se má počítat od 1 do 100; ale `break` příkaz ukončí smyčku po 4 počty.</span><span class="sxs-lookup"><span data-stu-id="e51b2-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="e51b2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e51b2-107">Example</span></span>

<span data-ttu-id="e51b2-108">V tomto příkladu `break` prohlášení se používá pro přerušit ze vnitřní smyčku vnořené a návrat ovládacího prvku na vnější smyčky.</span><span class="sxs-lookup"><span data-stu-id="e51b2-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="e51b2-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e51b2-109">Example</span></span>

<span data-ttu-id="e51b2-110">Tento příklad ukazuje použití `break` v [přepnout](../../../csharp/language-reference/keywords/switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="e51b2-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="e51b2-111">Pokud jste zadali `4`, výstup by měl:</span><span class="sxs-lookup"><span data-stu-id="e51b2-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="e51b2-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e51b2-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e51b2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e51b2-113">See also</span></span>

- [<span data-ttu-id="e51b2-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e51b2-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="e51b2-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e51b2-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e51b2-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e51b2-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="e51b2-117">switch</span><span class="sxs-lookup"><span data-stu-id="e51b2-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
- [<span data-ttu-id="e51b2-118">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="e51b2-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
- [<span data-ttu-id="e51b2-119">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="e51b2-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
