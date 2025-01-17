---
title: ?? a?? = operátory – C# referenční informace
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 2bd6fe3d2d283e64eebc2251416fa5234e30bdad
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739657"
---
# <a name="-and--operators-c-reference"></a>?? a?? = – operátoryC# (Reference)

Operátor slučování null `??` vrátí hodnotu jeho levého operandu, pokud není `null`; v opačném případě vyhodnotí operand na pravé straně a vrátí jeho výsledek. Operátor `??` nevyhodnotí svůj operand na pravé straně, pokud je levý operand vyhodnocen jako jiný než null.

K dispozici v 8,0 a novějších operátor přiřazení s nulovou hodnotou`??=`přiřadí hodnotu jeho operandu na levý operand pouze v C# případě, že je operand na levé straně vyhodnocen jako`null`. Operátor `??=` nevyhodnotí svůj operand na pravé straně, pokud je levý operand vyhodnocen jako jiný než null.

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

Levý operand operátoru `??=` musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo element [indexeru](../../programming-guide/indexers/index.md) .

V C# 7,3 a starších verzích musí být typ levého operandu operátoru `??` buď [odkazový typ](../keywords/reference-types.md) , nebo [typ hodnoty s možnou hodnotou null](../builtin-types/nullable-value-types.md). Počínaje C# 8,0 je tento požadavek nahrazen následujícím: typ levého operandu operátorů`??`a`??=`nesmí být typ hodnoty, která není null. Konkrétně počínaje C# 8,0 můžete použít operátory slučování s hodnotou null s neomezenými parametry typu:

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

Operátory slučování s hodnotou null jsou asociativní zprava. To znamená, že výrazy ve formuláři

```csharp
a ?? b ?? c
d ??= e ??= f
```

se vyhodnotí jako

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Příklady

Operátory `??` a `??=` mohou být užitečné v následujících situacích:

- Ve výrazech s [operátory podmíněného příznaku?. a? []](member-access-operators.md#null-conditional-operators--and-)můžete použít operátor `??` k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že je výsledek výrazu s operacemi podmíněného hodnoty null `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Když pracujete s [typy hodnot s možnou hodnotou null](../builtin-types/nullable-value-types.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte operátor `??` k určení hodnoty, která se má zadat pro případ, že hodnota typu s možnou hodnotou null je `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> použijte v případě, že hodnota, která se má použít, pokud je hodnota typu s možnou hodnotou null `null` by měla být výchozí hodnotou základního typu hodnoty.

- Počínaje C# 7,0 můžete použít [výraz`throw`](../keywords/throw.md#the-throw-expression) jako pravý operand operátoru`??`, aby byl kód pro kontrolu argumentu výstižnější:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  Předchozí příklad také ukazuje, jak pomocí [členů Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.

- Počínaje C# 8,0 můžete použít operátor`??=`k nahrazení kódu formuláře

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  s následujícím kódem:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Přetížení operátoru

Operátory `??` a `??=` nelze přečítat.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace o operátoru `??` naleznete v části [operátor slučování null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

Další informace o operátoru `??=` najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)
- [?: – operátor](conditional-operator.md)
