---
title: let – klauzule - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 941ad41d75e14420699022a07bd6a3b10d83c896
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243397"
---
# <a name="let-clause-c-reference"></a>let – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu je někdy užitečné ukládat výsledek dílčí výraz. Chcete-li použít v následných klauzulí. Můžete to provedete `let` – klíčové slovo, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu zadáte. Po inicializaci s hodnotou proměnné rozsahu nelze použít pro ukládání hodnoty horní jiný. Nicméně pokud proměnnou rozsahu obsahuje dotazovatelný typ, může být dotazován.

## <a name="example"></a>Příklad

V následujícím příkladu `let` slouží dvěma způsoby:

1. Chcete-li vytvořit Výčtový typ, který je sám možné zadávat dotazy.

2. Povolit dotaz tak, aby volání `ToLower` pouze jednou na proměnnou rozsahu `word`. Bez použití `let`, budete muset volat `ToLower` v každé predikátu v `where` klauzuli.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [Začínáme s dotazy LINQ v jazyce C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [Zpracování výjimek ve výrazech dotazů](../../linq/handle-exceptions-in-query-expressions.md)