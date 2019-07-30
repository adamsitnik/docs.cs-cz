---
title: globální kontextová klíčová slova – C# reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 9a8c7b5134cc29668aae53e8a3f86ddae4c8263a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627679"
---
# <a name="global-c-reference"></a>global (Referenční dokumentace jazyka C#)

Klíčové slovo C# kontextové, pokud je uvedeno před [operátorem::](../operators/namespace-alias-qualifier.md), odkazuje na globální obor názvů, což je výchozí obor názvů pro všechny programy a je jinak bez názvu. `global` Další informace najdete v tématu [jak: Použijte globální alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)oboru názvů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `global` klíčové slovo kontextu k určení toho, že třída `TestApp` je definována v globálním oboru názvů:

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a>Viz také:

- [Obory názvů](../../programming-guide/namespaces/index.md)
