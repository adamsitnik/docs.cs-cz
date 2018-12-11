---
title: ?? Operator - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 153accdc4995065563b00da0fd62992341c06cf1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241876"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c14e6-103">??</span><span class="sxs-lookup"><span data-stu-id="c14e6-103">??</span></span> <span data-ttu-id="c14e6-104">– Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c14e6-104">Operator (C# Reference)</span></span>
<span data-ttu-id="c14e6-105">`??` Operátor se nazývá operátoru nulového sjednocení.</span><span class="sxs-lookup"><span data-stu-id="c14e6-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="c14e6-106">Vrátí levý operand, pokud hodnota operandu není null; v opačném případě vrátí pravý operand.</span><span class="sxs-lookup"><span data-stu-id="c14e6-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c14e6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c14e6-107">Remarks</span></span>  
 <span data-ttu-id="c14e6-108">Typ povolené hodnoty null představuje hodnotu z domény typu, hodnotu lze také definovat (v takovém případě je hodnota null).</span><span class="sxs-lookup"><span data-stu-id="c14e6-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="c14e6-109">Můžete použít `??` syntaktické expresivity obsluhy se vraťte na příslušnou hodnotu (pravý operand) Pokud levý operand má typ s možnou hodnotou Null, jehož hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="c14e6-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="c14e6-110">Pokud se pokusíte přiřadit typ s možnou hodnotou Null typu hodnotu Null bez použití `??` operátoru, vygeneruje chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c14e6-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="c14e6-111">Pokud použijete přetypování a typ s možnou hodnotou Null není aktuálně definován `InvalidOperationException` , bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c14e6-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="c14e6-112">Další informace najdete v tématu [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c14e6-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="c14e6-113">Výsledek??</span><span class="sxs-lookup"><span data-stu-id="c14e6-113">The result of a ??</span></span> <span data-ttu-id="c14e6-114">operátor není považována za konstantu, i když jsou oba argumenty konstanty.</span><span class="sxs-lookup"><span data-stu-id="c14e6-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c14e6-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c14e6-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c14e6-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c14e6-116">C# Language Specification</span></span>  

<span data-ttu-id="c14e6-117">Další informace najdete v tématu [null operátor sloučení](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c14e6-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="c14e6-118">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="c14e6-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c14e6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c14e6-119">See Also</span></span>

- [<span data-ttu-id="c14e6-120">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c14e6-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c14e6-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c14e6-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c14e6-122">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c14e6-122">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="c14e6-123">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="c14e6-123">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
- [<span data-ttu-id="c14e6-124">Co přesně se pojem "zrušeno" znamenají?</span><span class="sxs-lookup"><span data-stu-id="c14e6-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
