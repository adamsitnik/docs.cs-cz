---
title: '! (null – striktní) – odkaz C# na operátora'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291723"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null – striktní) – operátorC# (Referenční dokumentace)

K dispozici v C# 8,0 a novějším, unární přípona @no__t operátor-1 je operátor null-striktní. V povoleném [kontextu anotace s možnou hodnotou](../../nullable-references.md#nullable-annotation-context)null použijte operátor null-striktní k deklaraci, že výraz `x` typu odkazu není null: `x!`. Unární předpona `!` operátor je [logický operátor negace](boolean-logical-operators.md#logical-negation-operator-).

Operátor null-striktní nemá žádný vliv na dobu běhu. Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu. V době běhu je výraz `x!` vyhodnocen jako výsledek podkladového výrazu `x`.

Další informace o funkci typů odkazů s možnou hodnotou null naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md).

## <a name="examples"></a>Příklady

Jedním z případů použití operátoru null-striktní je testování logiky ověřování argumentů. Zvažte například následující třídu:

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

Pomocí [testovacího rozhraní MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test logiky ověřování v konstruktoru:

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro předchozí kód: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Při použití operátoru null-striktní můžete kompilátoru sdělit, že se očekává předávání `null` a neměla by se jim upozornit.

Operátor null-striktní můžete použít také v případě, že jednoznačně víte, že výraz nemůže být `null`, ale kompilátor nespravuje pro rozpoznání. V následujícím příkladu, pokud metoda `IsValid` vrátí `true`, jeho argument není `null` a můžete ho bezpečně odkázat:

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro kód `p.Name`: `Warning CS8602: Dereference of a possibly null reference.`.

Pokud můžete upravit metodu `IsValid`, můžete použít atribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) , aby kompilátor věděl, že argument metody `IsValid` nemůže být `null`, pokud metoda vrátí `true`:

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

V předchozím příkladu nemusíte používat operátor null-striktní, protože kompilátor má dostatek informací, aby zjistil, že `p` nelze v příkazu `if` `null`. Další informace o atributech, které umožňují zadat další informace o stavu null proměnné, naleznete v tématu [upgrade rozhraní API s atributy pro definování očekávání null](../../nullable-attributes.md).

## <a name="see-also"></a>Další informace najdete v tématech

- [C#odkaz](../index.md)
- [C#logické](index.md)
- [Kurz: návrh s použitím typů odkazů s možnou hodnotou null](../../tutorials/nullable-reference-types.md)