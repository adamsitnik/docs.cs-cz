---
title: Operátory přístupu členů - C# odkaz
description: Další informace o C# operátory, které můžete použít pro přístup ke členům typu.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
ms.openlocfilehash: 921d69e3deb7e5bb5115eb723727462839af9b6b
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65453166"
---
# <a name="member-access-operators"></a><span data-ttu-id="b23eb-103">Operátory přístupu členů</span><span class="sxs-lookup"><span data-stu-id="b23eb-103">Member access operators</span></span>

<span data-ttu-id="b23eb-104">Při přístupu k člena typu můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="b23eb-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="b23eb-105">[`.` (přístup ke členu) ](#member-access-operator-): přístup k oboru názvů nebo typ</span><span class="sxs-lookup"><span data-stu-id="b23eb-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="b23eb-106">[`[]` (element nebo indexovací člen přístup k poli) ](#indexer-operator-): přístup k elementu pole nebo typ indexeru</span><span class="sxs-lookup"><span data-stu-id="b23eb-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="b23eb-107">[`?.` a `?[]` (podmíněné operátory s null)](#null-conditional-operators--and-): k provedení operace přístupu člen nebo element, pouze pokud operand je jiná než null</span><span class="sxs-lookup"><span data-stu-id="b23eb-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="b23eb-108">[`()` (volání) ](#invocation-operator-): volání metody používaná nebo vyvolat delegáta</span><span class="sxs-lookup"><span data-stu-id="b23eb-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="b23eb-109">Operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="b23eb-109">Member access operator .</span></span>

<span data-ttu-id="b23eb-110">Můžete použít `.` token pro přístup k oboru názvů nebo typ, jak ukazují následující příklady:</span><span class="sxs-lookup"><span data-stu-id="b23eb-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="b23eb-111">Použití `.` pro přístup k vnořené oboru názvů v oboru názvů, jako následující příklad [ `using` směrnice](../keywords/using-directive.md) ukazuje:</span><span class="sxs-lookup"><span data-stu-id="b23eb-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="b23eb-112">Použití `.` do formuláře *kvalifikovaný název* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="b23eb-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="b23eb-113">Použít [ `using` směrnice](../keywords/using-directive.md) provést volitelné použijte kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="b23eb-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="b23eb-114">Použití `.` přístup [členy typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, pokud jako ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="b23eb-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="b23eb-115">Můžete také použít `.` k přístupu [– metoda rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b23eb-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="b23eb-116">Indexer operator [].</span><span class="sxs-lookup"><span data-stu-id="b23eb-116">Indexer operator []</span></span>

<span data-ttu-id="b23eb-117">Hranaté závorky, `[]`, se obvykle používají pro přístup k prvkům pole, indexovací člen nebo ukazatel.</span><span class="sxs-lookup"><span data-stu-id="b23eb-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="b23eb-118">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="b23eb-118">Array access</span></span>

<span data-ttu-id="b23eb-119">Následující příklad ukazuje, jak přistupovat k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="b23eb-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="b23eb-120">Pokud pole indexu je mimo hranice odpovídající dimenze v poli, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b23eb-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="b23eb-121">Jak ukazuje předchozí příklad, také použijete hranaté závorky při deklaraci typu pole nebo vytvoření instance pole instance.</span><span class="sxs-lookup"><span data-stu-id="b23eb-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="b23eb-122">Další informace o polích naleznete v tématu [pole](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="b23eb-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="b23eb-123">Přístup indexeru</span><span class="sxs-lookup"><span data-stu-id="b23eb-123">Indexer access</span></span>

<span data-ttu-id="b23eb-124">Následující příklad používá .NET <xref:System.Collections.Generic.Dictionary%602> typu k předvedení přístup indexeru:</span><span class="sxs-lookup"><span data-stu-id="b23eb-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="b23eb-125">Indexery umožňují index instance typu uživatelem definované v podobným způsobem jako indexování pole.</span><span class="sxs-lookup"><span data-stu-id="b23eb-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="b23eb-126">Na rozdíl od indexy pole, které musí být celé číslo, mohou být deklarovány argumenty indexeru být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="b23eb-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="b23eb-127">Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b23eb-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="b23eb-128">Další použití]</span><span class="sxs-lookup"><span data-stu-id="b23eb-128">Other usages of []</span></span>

<span data-ttu-id="b23eb-129">Informace o přístup k prvkům ukazatel najdete v tématu [postupy: přístup k elementu pole pomocí ukazatele](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="b23eb-129">For information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="b23eb-130">Můžete také použít hranaté závorky k určení [atributy](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="b23eb-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="b23eb-131">Podmíněné operátory s Null?.</span><span class="sxs-lookup"><span data-stu-id="b23eb-131">Null-conditional operators ?.</span></span> <span data-ttu-id="b23eb-132">a? []</span><span class="sxs-lookup"><span data-stu-id="b23eb-132">and ?[]</span></span>

<span data-ttu-id="b23eb-133">K dispozici v C# 6 nebo novější, platí null podmíněného operátoru přístupu ke členu `?.`, nebo přístup k prvkům `?[]`, operace svého operandu pouze v případě, že operand vyhodnocen jako jinou hodnotu než null.</span><span class="sxs-lookup"><span data-stu-id="b23eb-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="b23eb-134">Pokud je operand vyhodnocen jako `null`, je výsledek použití operátoru `null`.</span><span class="sxs-lookup"><span data-stu-id="b23eb-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span>

<span data-ttu-id="b23eb-135">Podmíněné operátory s null jsou short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="b23eb-135">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="b23eb-136">To znamená, pokud jedna operace v řetězci Podmíněný člen nebo element přístup operace vrátí `null`, neprovede zbytek řetězce.</span><span class="sxs-lookup"><span data-stu-id="b23eb-136">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="b23eb-137">V následujícím příkladu `B` není vyhodnocen, pokud `A` vyhodnotí jako `null` a `C` není vyhodnocen, pokud `A` nebo `B` vyhodnotí jako `null`:</span><span class="sxs-lookup"><span data-stu-id="b23eb-137">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="b23eb-138">Následující příklad ukazuje použití `?.` a `?[]` operátory:</span><span class="sxs-lookup"><span data-stu-id="b23eb-138">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="b23eb-139">Předchozí příklad také ukazuje využití [operátoru nulového sjednocení](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b23eb-139">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="b23eb-140">Můžete použít poskytnout alternativní výraz k vyhodnocení v případě, že je výsledek operace null podmíněného operátoru nulového sjednocení `null`.</span><span class="sxs-lookup"><span data-stu-id="b23eb-140">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="b23eb-141">Volání delegáta bezpečným pro vlákno</span><span class="sxs-lookup"><span data-stu-id="b23eb-141">Thread-safe delegate invocation</span></span>

<span data-ttu-id="b23eb-142">Použití `?.` operátor pro kontrolu, pokud delegát je jiná než null a vyvolání způsobem bezpečným pro vlákno (například když je [vyvolat událost](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="b23eb-142">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="b23eb-143">Kód následující kód, který použijete v odpovídá C# 5 nebo starším systémem:</span><span class="sxs-lookup"><span data-stu-id="b23eb-143">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="b23eb-144">Operátor vyvolání)</span><span class="sxs-lookup"><span data-stu-id="b23eb-144">Invocation operator ()</span></span>

<span data-ttu-id="b23eb-145">Použít závorky, `()`, aby volal [metoda](../../programming-guide/classes-and-structs/methods.md) nebo vyvolat [delegovat](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="b23eb-145">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="b23eb-146">Následující příklad ukazuje, jak volat metodu, s nebo bez argumentů a vyvolání delegáta:</span><span class="sxs-lookup"><span data-stu-id="b23eb-146">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="b23eb-147">Můžete také použít závorky, při vyvolání [konstruktor](../../programming-guide/classes-and-structs/constructors.md) s [ `new` ](../keywords/new-operator.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="b23eb-147">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="b23eb-148">Další využití)</span><span class="sxs-lookup"><span data-stu-id="b23eb-148">Other usages of ()</span></span>

<span data-ttu-id="b23eb-149">Je také použít k určení pořadí, ve kterém se má vyhodnotit operací ve výrazu závorky.</span><span class="sxs-lookup"><span data-stu-id="b23eb-149">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="b23eb-150">Další informace najdete v tématu [závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) část [operátory](../../programming-guide/statements-expressions-operators/operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="b23eb-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="b23eb-151">Seznam operátorů seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="b23eb-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

<span data-ttu-id="b23eb-152">[Výrazy přetypování](invocation-operator.md#cast-expression), které vyvolat operátor převodu, také pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="b23eb-152">[Cast expressions](invocation-operator.md#cast-expression), which invoke a conversion operator, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="b23eb-153">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="b23eb-153">Operator overloadability</span></span>

<span data-ttu-id="b23eb-154">`.` a `()` nemohou být přetíženy operátory.</span><span class="sxs-lookup"><span data-stu-id="b23eb-154">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="b23eb-155">`[]` Operátor bude také považován za bez přetěžovatelný operátor.</span><span class="sxs-lookup"><span data-stu-id="b23eb-155">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="b23eb-156">Použití [indexery](../../programming-guide/indexers/index.md) pro podporu indexování pomocí uživatelem definovaných typů.</span><span class="sxs-lookup"><span data-stu-id="b23eb-156">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b23eb-157">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b23eb-157">C# language specification</span></span>

<span data-ttu-id="b23eb-158">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="b23eb-158">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b23eb-159">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="b23eb-159">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="b23eb-160">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="b23eb-160">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="b23eb-161">Null – podmíněný operátor</span><span class="sxs-lookup"><span data-stu-id="b23eb-161">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="b23eb-162">Výrazy typu Invocation</span><span class="sxs-lookup"><span data-stu-id="b23eb-162">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="b23eb-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b23eb-163">See also</span></span>

- [<span data-ttu-id="b23eb-164">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b23eb-164">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b23eb-165">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b23eb-165">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b23eb-166">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b23eb-166">C# Operators</span></span>](index.md)
- [<span data-ttu-id="b23eb-167">?? (operátoru nulového sjednocení)</span><span class="sxs-lookup"><span data-stu-id="b23eb-167">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)