---
title: Uživatelsky definované operátory převodu – C# referenční informace
description: Naučte se definovat vlastní implicitní a explicitní převody typu v C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 25f042dec5fd5594b7e166cc064394e90db01c27
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036120"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Uživatelsky definované operátory převodu (C# referenční)

Uživatelsky definovaný typ může definovat vlastní implicitní nebo explicitní převod z nebo na jiný typ.

Implicitní převody nevyžadují, aby se vyvolala speciální syntaxe, která může nastat v různých situacích, například v přiřazení a volání metod. Předdefinované C# implicitní převody jsou vždy úspěšné a nikdy nevyvolávají výjimku. Uživatelem definované implicitní převody by se měly chovat i tímto způsobem. Pokud vlastní převod může vyvolat výjimku nebo ztratit informace, definujte ji jako explicitní převod.

Uživatelem definované převody nejsou považovány za operátory [is](type-testing-and-cast.md#is-operator) a [as](type-testing-and-cast.md#as-operator) . Použijte [operátor přetypování ()](type-testing-and-cast.md#cast-operator-) pro vyvolání uživatelem definovaného explicitního převodu.

Použijte klíčová slova `operator` a `implicit` nebo `explicit` k definování implicitního nebo explicitního převodu v uvedeném pořadí. Typ, který definuje převod, musí být buď zdrojový typ, nebo cílový typ převodu. Převod mezi dvěma uživatelsky definovanými typy lze definovat v jednom ze dvou typů.

Následující příklad ukazuje, jak definovat implicitní a explicitní převod:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Také použijte klíčové slovo `operator` k přetížení předdefinovaného C# operátoru. Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Operátory převodu](~/_csharplang/spec/classes.md#conversion-operators)
- [Uživatelem definované převody](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Implicitní převody](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Přetížení operátoru](operator-overloading.md)
- [Operátory testování typů a přetypování](type-testing-and-cast.md)
- [Přetypování a převod typu](../../programming-guide/types/casting-and-type-conversions.md)
- [Zřetězené uživatelem definované explicitní převody vC#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
