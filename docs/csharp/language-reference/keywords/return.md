---
title: Return – příkaz - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 3e89f2f854d1f66ca2d7bf1cfa5a507c267798f8
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422726"
---
# <a name="return-c-reference"></a>return (Referenční dokumentace jazyka C#)

`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí řízení volající metodě. Také může vrátit nepovinnou hodnotu. Pokud je metoda `void` typ, `return` příkaz lze vynechat.

 Pokud je příkaz return uvnitř `try` bloku `finally` bloku, pokud existuje, budou spuštěny před ovládací prvek vrátí volajícímu metody.

## <a name="example"></a>Příklad

 V následujícím příkladu metoda `CalculateArea()` vrátí lokální proměnná `area` jako [double](double.md) hodnotu.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [return – příkaz](/cpp/cpp/return-statement-cpp)
