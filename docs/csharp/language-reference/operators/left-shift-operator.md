---
title: '&lt;&lt; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: bd52d86c6ab84364d242e594054cfdd03dcc7e66
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241733"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="28088-102">&lt;&lt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="28088-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="28088-103">Operátor posunutí doleva (`<<`) staffhubu jeho prvního operandu vlevo o počet bitů určený svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="28088-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="28088-104">Musí být typu druhého operandu [int](../../../csharp/language-reference/keywords/int.md) nebo typ, který má předdefinované implicitní převod čísla na `int`.</span><span class="sxs-lookup"><span data-stu-id="28088-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28088-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28088-105">Remarks</span></span>  
 <span data-ttu-id="28088-106">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [uint](../../../csharp/language-reference/keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="28088-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="28088-107">To znamená, že počet skutečné posunutí je 0 až 31 bitů.</span><span class="sxs-lookup"><span data-stu-id="28088-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="28088-108">Pokud je první operand [dlouhé](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="28088-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="28088-109">To znamená že počet skutečné posunutí je 0 až 63 bitů.</span><span class="sxs-lookup"><span data-stu-id="28088-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="28088-110">Všechny nejvyšším bity, které jsou v rozsahu typu prvního operandu po přesun se zahodí a prázdný bity nižšího řádu jsou vyplněny nulami.</span><span class="sxs-lookup"><span data-stu-id="28088-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="28088-111">Operace posunutí nikdy nezpůsobí přetečení.</span><span class="sxs-lookup"><span data-stu-id="28088-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="28088-112">Lze přetěžovat uživatelsky definované typy `<<` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)); typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu `int`.</span><span class="sxs-lookup"><span data-stu-id="28088-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="28088-113">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="28088-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28088-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="28088-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="28088-115">Komentáře</span><span class="sxs-lookup"><span data-stu-id="28088-115">Comments</span></span>  
 <span data-ttu-id="28088-116">Všimněte si, že `i<<1` a `i<<33` poskytují stejný výsledek, protože 1 a 33 mají stejné pět bity nižšího řádu.</span><span class="sxs-lookup"><span data-stu-id="28088-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28088-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="28088-117">See Also</span></span>

- [<span data-ttu-id="28088-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="28088-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="28088-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="28088-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="28088-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="28088-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
