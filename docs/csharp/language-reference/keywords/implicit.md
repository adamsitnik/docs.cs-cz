---
title: implicitní - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: d3e1cb9d6fb37617c6e2aa7070b006c594d39762
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661708"
---
# <a name="implicit-c-reference"></a>implicit (referenční dokumentace jazyka C#)

`implicit` – Klíčové slovo se používá k deklaraci implicitního uživatelem definovaného typu operátoru převodu. Pokud převod je zaručeno, že způsobit ztrátu dat, použijte ji Pokud chcete povolit implicitní převody mezi uživatelem definovaného typu a jiného typu.

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

Odstraněním nepotřebných přetypování implicitní převod může zlepšit čitelnost zdrojového kódu. Ale protože implicitní převody nevyžadují, aby programátoři explicitně přetypovat z jednoho typu na druhý, musí věnovat pozornost zabránit neočekávaným výsledkům. Operátory implicitního převodu by měla obecně platí, nikdy nevyvolají výjimky a tak, aby bylo možné bezpečně bez sledování serverů programátora nikdy dojít ke ztrátě informací. Pokud se operátor převodu nemůže splnění těchto kritérií, by měla být označena `explicit`. Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [explicit](explicit.md)
- [– Operátor (referenční dokumentace jazyka C#)](operator.md)
- [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
