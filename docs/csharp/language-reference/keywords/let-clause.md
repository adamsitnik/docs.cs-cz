---
title: klauzule let – C# reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422702"
---
# <a name="let-clause-c-reference"></a>let – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu je někdy užitečné ukládat výsledek dílčího výrazu, aby jej bylo možné použít v dalších klauzulích. Můžete to provést pomocí klíčového slova `let`, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu, který zadáte. Po inicializaci s hodnotou nelze proměnnou rozsahu použít k uložení jiné hodnoty. Nicméně pokud proměnná rozsahu obsahuje typ Queryable, může se dotazovat.

## <a name="example"></a>Příklad

V následujícím příkladu `let` použít dvěma způsoby:

1. Pro vytvoření vyčíslitelného typu, který se může dotazovat sám na sebe.

2. Chcete-li povolit, aby dotaz vyvolal `ToLower` pouze jednou pro proměnnou rozsahu `word`. Bez použití `let`byste museli volat `ToLower` v každém predikátu v klauzuli `where`.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [Začínáme s dotazy LINQ v jazyce C#](/dotnet/csharp/programming-guide/concepts/linq/)
- [Zpracování výjimek ve výrazech dotazů](../../linq/handle-exceptions-in-query-expressions.md)
