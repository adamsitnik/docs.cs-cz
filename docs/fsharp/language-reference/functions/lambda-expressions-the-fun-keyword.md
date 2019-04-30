---
title: 'Výrazy lambda: Klíčové slovo fun'
description: Další informace o použití F# "zábavu" – klíčové slovo k definování výraz lambda, který je anonymní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 6ad15173bb8643bff330e3ca3823cba5d43ad445
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941021"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Výrazy lambda: Klíčové slovo fun (F#)

`fun` – Klíčové slovo se používá k definování výraz lambda, to znamená, anonymní funkce.

## <a name="syntax"></a>Syntaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Poznámky

*Seznam parametrů* se obvykle skládá z názvů a volitelně typy parametrů. Obecně platí *seznam parametrů* může skládat z libovolné F# vzory. Úplný seznam možných vzory, naleznete v tématu [porovnávání vzorů](../pattern-matching.md). Seznam platných parametrů zahrnují následující příklady.

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

*Výraz* tělo funkce posledního výrazu z nich generuje návratovou hodnotu. Příklady výrazů lambda platné patří:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Používání výrazů lambda

Výrazy lambda jsou zvláště užitečné, pokud chcete provádět operace v seznamu nebo z jiné kolekce a chcete se vyhnout nadbytečné práci spojené se definice funkce. Mnoho F# přijmout hodnoty funkcí jako argumenty funkce knihovny, a může být zvláště praktické použití lambda výrazů v těchto případech. Následující kód platí pro prvky seznamu výraz lambda. V takovém případě anonymní funkce přičte 1 k každý prvek seznamu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)