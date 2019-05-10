---
title: Operátory porovnání - C# odkaz
description: Další informace o C# operátory porovnání, které vám umožní zkontrolovat pořadí číselné hodnoty.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: ea8d8ab5ac14ec94c647ed33cca6f949a90737bd
ms.sourcegitcommit: dd3b897feb5c4ac39732bb165848e37a344b0765
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2019
ms.locfileid: "64445210"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="1c8a9-103">Operátory porovnání (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="1c8a9-103">Comparison operators (C# Reference)</span></span>

<span data-ttu-id="1c8a9-104">[ `<` (Menší než)](#less-than-operator-), [ `>` (větší)](#greater-than-operator-), [ `<=` (menší než nebo rovno)](#less-than-or-equal-operator-), a [ `>=` () větší než nebo rovno)](#greater-than-or-equal-operator-) porovnání, také známé jako relační, operátory porovnání svých operandů.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="1c8a9-105">Tyto operátory podporují všechny [integrální](../keywords/integral-types-table.md) a [s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md) číselné typy.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-105">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8a9-106">Pro `==`, `<`, `>`, `<=`, a `>=` operátory, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="1c8a9-107">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="1c8a9-108">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="1c8a9-109">Výčtové typy také podporují operátory porovnání.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="1c8a9-110">Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="1c8a9-111">[ `==` a `!=` operátory](equality-operators.md) zkontrolujte, jestli operandy jsou stejné, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="1c8a9-112">Operátor menší než \<</span><span class="sxs-lookup"><span data-stu-id="1c8a9-112">Less than operator \<</span></span>

<span data-ttu-id="1c8a9-113">`<` Operátor vrátí `true` Pokud svůj první operand je menší než svým druhým operandem, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="1c8a9-113">The `<` operator returns `true` if its first operand is less than its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="1c8a9-114">Operátor větší než ></span><span class="sxs-lookup"><span data-stu-id="1c8a9-114">Greater than operator ></span></span>

<span data-ttu-id="1c8a9-115">`>` Operátor vrátí `true` Pokud svůj první operand je větší než jeho druhým operandem, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="1c8a9-115">The `>` operator returns `true` if its first operand is greater than its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="1c8a9-116">Menší než nebo rovno – operátor \<=</span><span class="sxs-lookup"><span data-stu-id="1c8a9-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="1c8a9-117">`<=` Operátor vrátí `true` Pokud svůj první operand je menší nebo rovna svým druhým operandem, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="1c8a9-117">The `<=` operator returns `true` if its first operand is less than or equal to its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="1c8a9-118">Operátor větší než nebo rovna > =</span><span class="sxs-lookup"><span data-stu-id="1c8a9-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="1c8a9-119">`>=` Operátor vrátí `true` Pokud svůj první operand je větší než nebo rovna hodnotě svým druhým operandem, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="1c8a9-119">The `>=` operator returns `true` if its first operand is greater than or equal to its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="1c8a9-120">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="1c8a9-120">Operator overloadability</span></span>

<span data-ttu-id="1c8a9-121">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `<`, `>`, `<=`, a `>=` operátory.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-121">A user-defined type can [overload](../keywords/operator.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="1c8a9-122">Pokud typ jednoho z přetížení `<` nebo `>` operátory, ho musíte přetížení obě `<` a `>`.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="1c8a9-123">Pokud typ jednoho z přetížení `<=` nebo `>=` operátory, ho musíte přetížení obě `<=` a `>=`.</span><span class="sxs-lookup"><span data-stu-id="1c8a9-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c8a9-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c8a9-124">C# language specification</span></span>

<span data-ttu-id="1c8a9-125">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1c8a9-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c8a9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c8a9-126">See also</span></span>

- [<span data-ttu-id="1c8a9-127">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c8a9-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1c8a9-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1c8a9-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1c8a9-129">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c8a9-129">C# Operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="1c8a9-130">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="1c8a9-130">Equality operators</span></span>](equality-operators.md)