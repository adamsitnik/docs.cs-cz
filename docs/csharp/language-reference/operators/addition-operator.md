---
title: + Operator - C# odkaz
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 92e20dad8ae6358f71137e955bb80e3641a66a54
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237750"
---
# <a name="-operator-c-reference"></a>+ – operátor (Referenční dokumentace jazyka C#)

`+` Operátor je podporován ve dvou formách: Unární plus operátor nebo operátor binární sčítání.

## <a name="unary-plus-operator"></a>Jednočlenný operátor plus

Unární `+` operátor vrátí hodnotu svého operandu. Podporuje všechny číselné typy.

## <a name="numeric-addition"></a>Číselné sčítání

Pro číselné typy `+` operátor vypočítá součet operandů:

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a>Zřetězení řetězců

Když se jeden nebo oba operandy typu [řetězec](../keywords/string.md), `+` zřetězí řetězcové reprezentace jeho operandy operátoru:

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

Počínaje C# 6, [interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovací řetězce:

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Kombinaci delegátů

Pro [delegovat](../keywords/delegate.md) typy, `+` operátor vrátí novou instanci delegáta, která při vyvolání, vyvolá prvním operandem a poté vyvolá druhého operandu. Pokud kterýkoli z operandů `null`, `+` operátor vrátí hodnotu jiný operand (která může být také `null`). Následující příklad ukazuje, jak mohou být kombinovány delegáty s `+` operátor:

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) jednočlenné a binární `+` operátory. Když binární soubor `+` je operátor přetížen, [operátor přiřazení sčítání](addition-assignment-operator.md) `+=` je také implicitně přetížená.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [unární operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Interpolace řetězců](../tokens/interpolated.md)
- [Postupy: Řetězení více řetězců](../../how-to/concatenate-multiple-strings.md)
- [Delegáti](../../programming-guide/delegates/index.md)
- [Zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md)
