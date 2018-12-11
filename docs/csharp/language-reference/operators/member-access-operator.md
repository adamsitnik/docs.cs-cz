---
title: . Operator - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: f5048761973e10bec9650469383e2f52cee74da4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235043"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="97ee5-103">.</span><span class="sxs-lookup"><span data-stu-id="97ee5-103">.</span></span> <span data-ttu-id="97ee5-104">– Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="97ee5-104">Operator (C# Reference)</span></span>
<span data-ttu-id="97ee5-105">Tečka – operátor (`.`) se používá pro přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="97ee5-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="97ee5-106">Operátor tečky Určuje typ nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="97ee5-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="97ee5-107">Například operátor tečky slouží k přístupu k určité metody v rámci knihovny tříd rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="97ee5-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="97ee5-108">Představte si třeba následující třídy:</span><span class="sxs-lookup"><span data-stu-id="97ee5-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="97ee5-109">Proměnná `s` se dvěma členy `a` a `b`; pokud ho chcete přistupovat k nim, použijte operátor tečky:</span><span class="sxs-lookup"><span data-stu-id="97ee5-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="97ee5-110">Tečka slouží také k vytvoření kvalifikované názvy, které jsou názvy, které určují obor názvů nebo rozhraní, například, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="97ee5-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="97ee5-111">Using – direktiva provádí některé kvalifikace názvu volitelné:</span><span class="sxs-lookup"><span data-stu-id="97ee5-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="97ee5-112">Ale pokud identifikátor je dvojznačný, musí být kvalifikován:</span><span class="sxs-lookup"><span data-stu-id="97ee5-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="97ee5-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97ee5-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97ee5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="97ee5-114">See Also</span></span>

- [<span data-ttu-id="97ee5-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97ee5-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="97ee5-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="97ee5-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="97ee5-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97ee5-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
