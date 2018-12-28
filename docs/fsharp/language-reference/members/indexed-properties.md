---
title: Indexované vlastnosti
description: Další informace o indexované vlastnosti v F#, které umožňují pro přístup jako pole k datům seřazené.
ms.date: 10/17/2018
ms.openlocfilehash: 3817290505339803814e981cd5408cd4df6bd283
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611773"
---
# <a name="indexed-properties"></a>Indexované vlastnosti

Při definování třídy, který získává přes seřazených dat, může být někdy užitečné poskytnout indexovaný přístup k těmto datům bez vystavení se základní implementací. Používá se k tomu `Index` člena.

## <a name="syntax"></a>Syntaxe

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Poznámky

Formy syntaxe předchozí ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metodu, mají `get` metoda pouze, nebo mít `set` pouze metody. Můžete také zkombinovat obojí tomu syntaxe uvedená jenom příkaz get a syntaxi pro sadu pouze a vytvoří vlastnost, která má get a set. Tento druhý formulář umožňuje umístit různou přístupností. modifikátorů a vlastností atributy na get a set metod.

Pomocí názvu `Item`, kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost. A *výchozí indexovanou vlastnost* vlastností, která může získat přístup pomocí syntaxe pro pole na instanci objektu. Například pokud `o` je objekt typu, který definuje tato vlastnost syntaxe `o.[index]` slouží k přístupu k vlastnosti.

Syntaxe pro přístup k jiné než výchozí indexovaná vlastnost je k poskytnutí názvu vlastnosti a index v závorkách, stejně jako běžný člen. Například pokud vlastnost `o` nazývá `Ordinal`, psaní `o.Ordinal(index)` k němu přistupovat.

Bez ohledu na to, jaký tvar používáte měli byste použít vždy curryfikované formuláře pro metodu set indexované vlastnosti. Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje definice a používání výchozích a jiné než výchozí indexované vlastnosti, které mají get a set metod.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Výstup

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Indexované vlastnosti v případě více proměnných indexu

Indexované vlastnosti můžou mít více než jeden indexovaná proměnná. Proměnné v takovém případě jsou odděleny čárkami, pokud se vlastnost používá. Metoda set v těchto vlastností musí mít dva curryfikované argumenty, první z nich je řazená kolekce členů obsahující klíče a druhý z nich je hodnota nastavena.

Následující kód ukazuje použití indexovaná vlastnost s několika proměnnými indexu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a>Viz také:

- [Členové](index.md)