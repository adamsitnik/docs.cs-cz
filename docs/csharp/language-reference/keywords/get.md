---
title: Get - C# odkaz
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: e3cd4779b4f865c4c9bb46d4f25819c863de8bc2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240031"
---
# <a name="get-c-reference"></a>get (Referenční dokumentace jazyka C#)

`get` Definuje – klíčové slovo *přistupující objekt* metoda ve vlastnosti nebo indexeru, které vrací hodnotu vlastnosti nebo elementu indexeru. Další informace najdete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../../csharp/programming-guide/indexers/index.md).  
  
Následující příklad definuje i `get` a `set` přístupový objekt pro vlastnost s názvem `Seconds`. Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Často se stává `get` přístupový objekt se skládá z jednoho příkazu, který vrací hodnotu, stejně jako v předchozím příkladu. Od verze C# 7.0, můžete implementovat `get` přístupového objektu jako člena s výrazem v těle. Následující příklad implementuje oba `get` a `set` přístupového objektu jako členy s výrazem v těle.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Pro jednoduché případech, ve kterém vlastnosti `get` a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načtení hodnoty v poli privátní zálohování, můžete využít výhod podpory kompilátor jazyka C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
