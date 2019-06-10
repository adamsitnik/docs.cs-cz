---
title: = – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 85182acb84ea79cb00a9edb315c3954f440305f4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758364"
---
# <a name="-operator-c-reference"></a>= – operátor (Referenční dokumentace jazyka C#)

Operátor přiřazení `=` hodnota jeho operandu pravé přiřadí proměnné, [vlastnost](../../programming-guide/classes-and-structs/properties.md), nebo [indexer](../../../csharp/programming-guide/indexers/index.md) element Dal jeho levý operand. Výsledkem výrazu přiřazení je hodnota přiřazená k levý operand. Typ operandu pravé musí být stejný jako typ levý operand nebo implicitně převeditelné na ni.

Operátor přiřazení je asociativní zprava, to znamená, výraz ve tvaru

```csharp
a = b = c
```

je vyhodnocen jako

```csharp
a = (b = c)
```

Následující příklad ukazuje použití operátoru přiřazení k přiřazení hodnot k místní proměnné, vlastnosti a elementu indexeru:

[!code-csharp-interactive[assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a>operátoru přiřazení odkazu

Počínaje C# 7.3, můžete pomocí operátoru přiřazení odkazu `= ref` přiřazení [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnné. Následující příklad ukazuje použití operátoru přiřazení odkazu:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

V případě operátoru přiřazení odkazu typ levého operandu a pravý operand musí být stejné.

Další informace najdete v tématu [Poznámka návrh funkce](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ nejde přetížit operátor přiřazení. Uživatelem definovaný typ však můžete definovat implicitní převod na jiného typu. Tímto způsobem hodnota uživatelem definovaného typu lze přiřadit k proměnné, vlastnosti nebo elementu indexeru jiného typu. Další informace najdete v tématu [implicitní](../keywords/implicit.md) článku – klíčové slovo.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [jednoduché přiřazení](~/_csharplang/spec/expressions.md#simple-assignment) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [ref keyword](../keywords/ref.md)
