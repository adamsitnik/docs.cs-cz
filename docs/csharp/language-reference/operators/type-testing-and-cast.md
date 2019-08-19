---
title: Operátory typu testování a přetypování – C# reference
description: Přečtěte C# si o operátorech, pomocí kterých můžete kontrolovat typ výsledku výrazu a v případě potřeby ho převést na jiný typ.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 6966d0b7a4f8a96bddb17ce2017fd53fc07ae922
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69572330"
---
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="004f5-103">Operátory testování typů a přetypování (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="004f5-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="004f5-104">K provedení kontroly typu nebo převodu typu můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="004f5-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="004f5-105">[is – operátor](#is-operator): Pokud chcete zjistit, jestli je běhový typ výrazu kompatibilní s daným typem</span><span class="sxs-lookup"><span data-stu-id="004f5-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="004f5-106">[as – operátor](#as-operator)pro explicitní převod výrazu na daný typ, pokud je jeho typ modulu runtime kompatibilní s daným typem</span><span class="sxs-lookup"><span data-stu-id="004f5-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="004f5-107">[operátor přetypování ()](#cast-operator-): k provedení explicitního převodu</span><span class="sxs-lookup"><span data-stu-id="004f5-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="004f5-108">[typeof – operátor](#typeof-operator): pro získání <xref:System.Type?displayProperty=nameWithType> instance pro typ</span><span class="sxs-lookup"><span data-stu-id="004f5-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="004f5-109">is – operátor</span><span class="sxs-lookup"><span data-stu-id="004f5-109">is operator</span></span>

<span data-ttu-id="004f5-110">`is` Operátor zkontroluje, zda je typ modulu runtime výsledku výrazu kompatibilní s daným typem.</span><span class="sxs-lookup"><span data-stu-id="004f5-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="004f5-111">Počínaje C# 7,0, `is` operátor také testuje výsledek výrazu proti vzorci.</span><span class="sxs-lookup"><span data-stu-id="004f5-111">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="004f5-112">Výraz s operátorem testování `is` typu má následující formu.</span><span class="sxs-lookup"><span data-stu-id="004f5-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="004f5-113">kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="004f5-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="004f5-114">`E`nemůže být anonymní metoda nebo výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="004f5-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="004f5-115">`false` `T` Výraz vrátí `true` , pokud výsledek `E` není null a lze jej převést na typ pomocí převodu odkazu, převodu zabalení nebo převodu rozbalení. v opačném případě vrátí. `E is T`</span><span class="sxs-lookup"><span data-stu-id="004f5-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="004f5-116">Operátor `is` nebere v úvahu uživatelsky definované převody.</span><span class="sxs-lookup"><span data-stu-id="004f5-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="004f5-117">Následující příklad ukazuje, že `is` operátor vrátí `true` , pokud typ modulu runtime výsledku výrazu je odvozen z daného typu, to znamená, že existuje převod odkazu mezi typy:</span><span class="sxs-lookup"><span data-stu-id="004f5-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="004f5-118">Následující příklad ukazuje, že operátor `is` vezme v úvahu převody zabalení a rozbalení, ale nebere v úvahu číselné převody:</span><span class="sxs-lookup"><span data-stu-id="004f5-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider numeric conversions:</span></span>

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="004f5-119">Informace o C# převodech naleznete v kapitole [převody](~/_csharplang/spec/conversions.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="004f5-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="004f5-120">Testování typu s porovnáváním vzorů</span><span class="sxs-lookup"><span data-stu-id="004f5-120">Type testing with pattern matching</span></span>

<span data-ttu-id="004f5-121">Počínaje C# 7,0, `is` operátor také testuje výsledek výrazu proti vzorci.</span><span class="sxs-lookup"><span data-stu-id="004f5-121">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="004f5-122">Konkrétně podporuje vzor typu v následujícím tvaru:</span><span class="sxs-lookup"><span data-stu-id="004f5-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="004f5-123">kde `E` je výraz, který vrací hodnotu, `T` je název typu nebo parametr typu a `v` je nová lokální proměnná typu `T`.</span><span class="sxs-lookup"><span data-stu-id="004f5-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="004f5-124">Pokud `E` výsledek je jiný než null a lze jej převést na `T` odkaz, zabalení nebo rozbalení `E is T v` , výraz se vrátí `true` a převedená hodnota výsledku `E` je přiřazena k proměnná `v`.</span><span class="sxs-lookup"><span data-stu-id="004f5-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="004f5-125">Následující příklad ukazuje použití `is` operátoru se vzorem typu:</span><span class="sxs-lookup"><span data-stu-id="004f5-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="004f5-126">Další informace o vzoru typu a dalších podporovaných vzorech naleznete v tématu [porovnávání vzorů s](../keywords/is.md#pattern-matching-with-is)parametrem is.</span><span class="sxs-lookup"><span data-stu-id="004f5-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="004f5-127">as – operátor</span><span class="sxs-lookup"><span data-stu-id="004f5-127">as operator</span></span>

<span data-ttu-id="004f5-128">`as` Operátor explicitně převede výsledek výrazu na daný odkaz nebo typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="004f5-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="004f5-129">Pokud převod není možný, `as` vrátí `null`operátor.</span><span class="sxs-lookup"><span data-stu-id="004f5-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="004f5-130">Na`as` rozdíl od [operátoru přetypování ()](#cast-operator-), operátor nikdy nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="004f5-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="004f5-131">Výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="004f5-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="004f5-132">kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu, vytvoří stejný výsledek jako</span><span class="sxs-lookup"><span data-stu-id="004f5-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="004f5-133">s výjimkou, že `E` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="004f5-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="004f5-134">`as` Operátor zohledňuje pouze odkazy, převody s možnou hodnotou null, zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="004f5-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="004f5-135">`as` Operátor nelze použít k provedení převodu definovaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="004f5-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="004f5-136">K tomu použijte [operátor přetypování ()](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="004f5-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="004f5-137">Následující příklad ukazuje použití `as` operátoru:</span><span class="sxs-lookup"><span data-stu-id="004f5-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="004f5-138">Jak ukazuje předchozí příklad, je nutné porovnat výsledek `as` výrazu s `null` a zjistit, zda převod proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="004f5-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="004f5-139">Počínaje C# 7,0 můžete použít [operátor is](#type-testing-with-pattern-matching) pro testování, zda je převod úspěšný, a pokud je úspěšný, přiřaďte výsledek k nové proměnné.</span><span class="sxs-lookup"><span data-stu-id="004f5-139">Starting with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="004f5-140">Operátor přetypování ()</span><span class="sxs-lookup"><span data-stu-id="004f5-140">Cast operator ()</span></span>

<span data-ttu-id="004f5-141">Výraz přetypování formuláře `(T)E` provádí explicitní převod výsledku výrazu `E` na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="004f5-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="004f5-142">Pokud neexistuje žádný explicitní převod z typu `E` na typ `T`, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="004f5-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="004f5-143">V době spuštění explicitní převod nemusí být úspěšný a výraz přetypování může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="004f5-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="004f5-144">Následující příklad ukazuje explicitní číselné a referenční převody:</span><span class="sxs-lookup"><span data-stu-id="004f5-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="004f5-145">Informace o podporovaných explicitních převodech naleznete v části [explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="004f5-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="004f5-146">Informace o tom, jak definovat vlastní explicitní nebo implicitní převod typu, naleznete v části [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="004f5-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="004f5-147">Další použití pro ()</span><span class="sxs-lookup"><span data-stu-id="004f5-147">Other usages of ()</span></span>

<span data-ttu-id="004f5-148">K [volání metody nebo vyvolání delegáta](member-access-operators.md#invocation-operator-)můžete také použít kulaté závorky.</span><span class="sxs-lookup"><span data-stu-id="004f5-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="004f5-149">Jiné použití závorek je určit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="004f5-149">Other use of parentheses is to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="004f5-150">Další informace naleznete v části [Přidání závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) v článku věnovaném [operátorům](../../programming-guide/statements-expressions-operators/operators.md) .</span><span class="sxs-lookup"><span data-stu-id="004f5-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="004f5-151">Seznam operátorů seřazených podle priority najdete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="004f5-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="004f5-152">typeof – operátor</span><span class="sxs-lookup"><span data-stu-id="004f5-152">typeof operator</span></span>

<span data-ttu-id="004f5-153">`typeof` Operátor získá<xref:System.Type?displayProperty=nameWithType> instanci pro typ.</span><span class="sxs-lookup"><span data-stu-id="004f5-153">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="004f5-154">Argument `typeof` operátoru musí být název typu nebo parametr typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="004f5-154">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="004f5-155">`typeof` Operátor můžete použít také s nevázanými obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="004f5-155">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="004f5-156">Název nevázaného obecného typu musí obsahovat odpovídající počet čárek, což je jedna hodnota, která je menší než počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="004f5-156">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="004f5-157">Následující příklad ukazuje použití `typeof` operátoru s nevázaným obecným typem:</span><span class="sxs-lookup"><span data-stu-id="004f5-157">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="004f5-158">Výraz nemůže být argumentem `typeof` operátoru.</span><span class="sxs-lookup"><span data-stu-id="004f5-158">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="004f5-159">Chcete-li <xref:System.Type?displayProperty=nameWithType> získat instanci pro běhový typ výsledku výrazu, <xref:System.Object.GetType%2A?displayProperty=nameWithType> použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="004f5-159">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of the expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="004f5-160">Testování typu pomocí `typeof` operátoru</span><span class="sxs-lookup"><span data-stu-id="004f5-160">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="004f5-161">`typeof` Použijte operátor ke kontrole, zda typ modulu runtime výsledku výrazu přesně odpovídá danému typu.</span><span class="sxs-lookup"><span data-stu-id="004f5-161">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="004f5-162">Následující příklad ukazuje rozdíl mezi kontrolou typu provedenými s `typeof` operátorem a operátorem [is](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="004f5-162">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="004f5-163">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="004f5-163">Operator overloadability</span></span>

<span data-ttu-id="004f5-164">Operátory, `as`anejsoupřetíženy. `is` `typeof`</span><span class="sxs-lookup"><span data-stu-id="004f5-164">The `is`, `as`, and `typeof` operators are not overloadable.</span></span>

<span data-ttu-id="004f5-165">Uživatelsky definovaný typ nemůže přetížit `()` operátor, ale může definovat vlastní převody typů, které mohou být provedeny výrazem přetypování.</span><span class="sxs-lookup"><span data-stu-id="004f5-165">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="004f5-166">Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="004f5-166">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="004f5-167">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="004f5-167">C# language specification</span></span>

<span data-ttu-id="004f5-168">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="004f5-168">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="004f5-169">Operátor is</span><span class="sxs-lookup"><span data-stu-id="004f5-169">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="004f5-170">Operátor as</span><span class="sxs-lookup"><span data-stu-id="004f5-170">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="004f5-171">Výrazy cast</span><span class="sxs-lookup"><span data-stu-id="004f5-171">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="004f5-172">Operátor typeof</span><span class="sxs-lookup"><span data-stu-id="004f5-172">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="004f5-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="004f5-173">See also</span></span>

- [<span data-ttu-id="004f5-174">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="004f5-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="004f5-175">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="004f5-175">C# operators</span></span>](index.md)
- [<span data-ttu-id="004f5-176">Postupy: Bezpečné přetypování pomocí porovnávání vzorů a operátorů is a as</span><span class="sxs-lookup"><span data-stu-id="004f5-176">How to: safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)