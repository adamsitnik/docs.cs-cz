---
title: while C# – referenční informace
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: ab0a8ba0b724757b4f239daf1d3319b989c4531a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421920"
---
# <a name="while-c-reference"></a>while (Referenční dokumentace jazyka C#)

Příkaz `while` spustí příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true`. Vzhledem k tomu, že tento výraz je vyhodnocen před každým spuštěním smyčky, `while` smyčka provede nula nebo vícekrát. To se liší [od smyčky do, která se spouští](do.md) jednou nebo vícekrát.

V jakémkoli okamžiku v rámci bloku příkazu `while` lze rozdělit smyčku pomocí příkazu [Break](break.md) .

Můžete krokovat přímo s vyhodnocením výrazu `while` pomocí příkazu [Continue](continue.md) . Pokud se výraz vyhodnotí jako `true`, vykonání pokračuje v prvním příkazu smyčky. V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.

Můžete také ukončit `while` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje použití příkazu `while`. Vyberte **Spustit** a spusťte ukázkový kód. Potom můžete kód upravit a znovu spustit.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [while](~/_csharplang/spec/statements.md#the-while-statement) v tématu [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [do – příkaz](do.md)
