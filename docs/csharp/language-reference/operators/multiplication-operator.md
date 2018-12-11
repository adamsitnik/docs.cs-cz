---
title: '* Operator - C# odkaz'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 24ac4a99c48f1e8204b821bfbf5f7fbc0a2b2f1d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237347"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="67c3d-102">\* – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="67c3d-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="67c3d-103">Operátor násobení (`*`) vypočítá součin z operandů.</span><span class="sxs-lookup"><span data-stu-id="67c3d-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="67c3d-104">Všechny číselné typy obsahuje předdefinované operátory násobení.</span><span class="sxs-lookup"><span data-stu-id="67c3d-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="67c3d-105">`*` slouží také jako operátor zrušení odkazu, který umožňuje čtení a zápis na ukazatel.</span><span class="sxs-lookup"><span data-stu-id="67c3d-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="67c3d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67c3d-106">Remarks</span></span>  
 <span data-ttu-id="67c3d-107">`*` Operátor se používá také, chcete-li deklarovat typy ukazatelů a ke zrušení ukazatele.</span><span class="sxs-lookup"><span data-stu-id="67c3d-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="67c3d-108">Tento operátor jde použít jenom v kontextu unsafe, udávají použití [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo která vyžaduje [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="67c3d-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="67c3d-109">Operátor zrušení odkazu se také označuje jako operátor dereference.</span><span class="sxs-lookup"><span data-stu-id="67c3d-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="67c3d-110">Uživatelem definované typy mohou přetížit binárního souboru `*` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="67c3d-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="67c3d-111">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="67c3d-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67c3d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="67c3d-112">Example</span></span>  
 [!code-csharp-interactive[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="67c3d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="67c3d-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="67c3d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="67c3d-114">See Also</span></span>

- [<span data-ttu-id="67c3d-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67c3d-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="67c3d-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="67c3d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="67c3d-117">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="67c3d-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="67c3d-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67c3d-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
