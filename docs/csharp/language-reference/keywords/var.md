---
title: var – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: a523e575f14c88ea385bf115f0b07f54190499a5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633205"
---
# <a name="var-c-reference"></a>var (Referenční dokumentace jazyka C#)

Od Visual C# 3.0, proměnné, které jsou deklarovány v oboru metoda může mít implicitní "typ" `var`. Implicitně typovaná lokální proměnná je tak, jako kdyby měl typ deklarovaný sami, ale kompilátor Určuje typ silného typu. Následující dvě deklarace `i` jsou funkčně ekvivalentní:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Další informace najdete v tématu [implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje dva výrazy dotazu. V prvním výrazu použití `var` je povolené, ale není vyžadováno, protože typ výsledku dotazu může být explicitně nastavená jako `IEnumerable<string>`. Nicméně ve druhém výrazu `var` umožňuje výsledek, který má být kolekci anonymních typů, a název tohoto typu není dostupná s výjimkou samotné kompilátoru. Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek. Všimněte si, že v příkladu 2, `foreach` proměnné iterace `item` musí také být implicitně typované.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
