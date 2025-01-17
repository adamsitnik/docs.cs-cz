---
title: '- and-= Operators C# – reference'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: cf642fcac7233d27f2ed9052829c145038e93419
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038875"
---
# <a name="--and---operators-c-reference"></a>-and-= – operátoryC# (referenční informace)

Operátory `-` a `-=` jsou podporovány integrovanými čísly [integrálu](../builtin-types/integral-numeric-types.md) a typy s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .

Informace o aritmetickém operátoru `-` naleznete v tématu [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor odčítání –](arithmetic-operators.md#subtraction-operator--) oddíly v článku [aritmetické operátory](arithmetic-operators.md) .

## <a name="delegate-removal"></a>Odebrání delegáta

Pro operandy stejného typu [delegáta](../builtin-types/reference-types.md#the-delegate-type) operátor `-` vrací instanci delegáta, která je vypočítána takto:

- Jsou-li oba operandy nenulové a seznam vyvolání pravého operandu je správným souvislým podseznamem seznamu volání na levé straně, výsledkem operace je nový seznam vyvolání, který se získá odebráním operandu pravého operandu. položky ze seznamu volání z levého operandu. Pokud se v seznamu operandů na pravé straně shoduje více sousedících podseznamů v seznamu operandů na levé straně, bude odebrán pouze odpovídající podseznam. Pokud je výsledkem odebrání prázdný seznam, výsledek je `null`.

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- Pokud seznam volání na pravé straně operand není správným souvislým podseznamem seznamu vyvolání na levém operandu, výsledkem operace je operand na levé straně. Například odebrání delegáta, který není součástí delegáta vícesměrového vysílání, neprovede žádnou akci a dojde ke změně nezměněného delegáta vícesměrového vysílání.

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Předchozí příklad také ukazuje, že během porovnání instancí delegáta pro odebrání delegáta. Například delegáty vytvořené z vyhodnocení identických [výrazů lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné. Další informace o rovnosti delegátů naleznete v části [operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

- Je-li operand na levé straně `null`, výsledek operace je `null`. Je-li operand na pravé straně `null`, výsledkem operace je operand na levé straně.

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

Chcete-li kombinovat delegáty, použijte [operátor`+`](addition-operator.md#delegate-combination).

Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Operátor přiřazení odčítání-=

Výraz používající operátor `-=`, například

```csharp
x -= y
```

je ekvivalentem

```csharp
x = x - y
```

s výjimkou, že `x` je vyhodnocena pouze jednou.

Následující příklad ukazuje použití operátoru `-=`:

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Operátor `-=` můžete použít také k určení metody obslužné rutiny události, která se má odebrat při zrušení odběru [události](../keywords/event.md). Další informace najdete v tématu [Postup: přihlášení a](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)odhlášení odběru událostí.

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátor `-`. Je-li operátor binárního `-` přetížen, je operátor `-=` také implicitně přetížený. Uživatelsky definovaný typ nemůže explicitně přetížit operátor `-=`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v částech [unárního operátoru minus](~/_csharplang/spec/expressions.md#unary-minus-operator) a [operátoru odčítání](~/_csharplang/spec/expressions.md#subtraction-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Události](../../programming-guide/events/index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [+ a + = – operátory](addition-operator.md)
