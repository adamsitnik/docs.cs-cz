---
title: '% – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: a5c12b6683e35cc1ec2d40446dd0ed068c3d2552
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236476"
---
# <a name="-operator-c-reference"></a>% – operátor (Referenční dokumentace jazyka C#)

Operátor zbytku `%` vypočítá zbytek po dělení svůj první operand tak svým druhým operandem.

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `%` operátor. Když `%` je přetížena, [operátor přiřazení zbytku](remainder-assignment-operator.md) `%=` je také implicitně přetížená.

Všechny číselné typy podporují operátor zbytku.

## <a name="integer-remainder"></a>Zbývající celé číslo
  
Pro celočíselné operandy, výsledek `a % b` hodnota vytvořil `a - (a / b) * b`. Znaménko nenulové zbývající je stejný jako první operand, jako v následujícím příkladu:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a>Zbytek s plovoucí desetinnou čárkou

Pro [float](../keywords/float.md) a [double](../keywords/double.md) operandy, výsledek `x % y` pro omezenou `x` a `y` je hodnota `z` tak, aby

- znaménko `z`nenulová, pokud je stejný jako znaménko `x`;
- absolutní hodnota `z` hodnota vytvořil `|x| - n * |y|` kde `n` je největší možné číslo, které je menší než nebo rovna hodnotě `|x| / |y|` a `|x|` a `|y|` jsou absolutní hodnoty `x` a `y`v uvedeném pořadí.

Informace o chování `%` operátor s nekonečnou operandy, najdete v článku [operátor zbytku](~/_csharplang/spec/expressions.md#remainder-operator) část [ C# specifikace jazyka](../language-specification/index.md).

> [!NOTE]
> Tato metoda výpočetních zbytek je obdobou, který používá pro celočíselné operandy, ale se liší od IEEE 754. Pokud potřebujete zbývající operace, která splňuje IEEE 754, použijte <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.

Následující příklad ukazuje chování operátor zbytku pro `float` a `double` operandy:

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

Všimněte si zaokrouhlovací chyby, které mohou být spojeny s typy s plovoucí desetinnou čárkou.

Pro [desítkové](../keywords/decimal.md) operandy, operátor zbytku `%` odpovídá [operátor zbytku](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
