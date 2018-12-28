---
title: Odvození typu
description: Zjistěte, jak F# kompilátor odvodí typ hodnoty, proměnné, parametry a návratové hodnoty.
ms.date: 05/16/2016
ms.openlocfilehash: 3e61d5c81fde0a48af66a47745123a842dc04cb1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612787"
---
# <a name="type-inference"></a>Odvození typu

Toto téma popisuje, jak F# kompilátor odvodí typ hodnoty, proměnné, parametry a návratové hodnoty.

## <a name="type-inference-in-general"></a>Odvození typu, obecné

Představu o odvození typu je, že není nutné určit typy F# konstruktory s výjimkou případů, kdy kompilátor nemůže odvodit jednoznačně typ. Vynechání explicitního typu informace neznamená F# je dynamicky zadávaných jazyk nebo hodnoty, které budou v F# jsou slabě typované. F#je staticky psaný jazyk, což znamená, že kompilátor odvodí přesný typ pro každou konstrukci během kompilace. Pokud není k dispozici dostatek informací pro kompilátor k odvození typů každý konstrukce, musíte zadat informace o dalších typu, obvykle tak, že přidáte anotace explicitního typu někde v kódu.

## <a name="inference-of-parameter-and-return-types"></a>Odvozování parametrů a návratové typy

V seznamu parametrů není nutné zadat typ každého parametru. A ještě F# je staticky psaný jazyk a tedy každý hodnotu a výraz jednoznačného typu v době kompilace. Pro tyto typy, které explicitně nezadáte kompilátor odvodí typ na základě kontextu. Pokud typ není jinak zadán, je odvozen je obecný. Pokud tento kód použije hodnotu nekonzistentně, tak, že neexistuje žádné jeden odvodit typ, který splňuje všechna použití hodnoty, že kompilátor nahlásí chybu.

Návratový typ funkce je určen podle typu posledního výrazu ve funkci.

Například v následujícím kódu, typy parametrů `a` a `b` a návratový typ je odvozen bude `int` protože literál `100` je typu `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Odvození typu proměnné můžete ovlivnit tak, že změníte literály. Pokud provedete `100` `uint32` přidáním přípona `u`, typy `a`, `b`, a návratová hodnota jsou odvozena jako `uint32`.

Můžete také ovlivnit odvození typu pomocí jiných objektů, které znamenají omezení typu, například funkcí a metod, které pracují s pouze určitého typu.

Navíc můžete použít anotace explicitního typu funkce nebo metoda parametry a proměnné ve výrazech, jak je znázorněno v následujícím příkladu. Pokud dochází ke konfliktům mezi jiná omezení dojít k chybám.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Můžete také explicitně určit návratové hodnoty funkce tím, že poskytuje anotaci typu všechny parametry.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Běžný případ, kdy je užitečné u parametru anotaci typu je, když je parametr typu objektu a chcete, použijte člena.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Automatická generalizace

Pokud kód této funkce není závislá na typ parametru, kompilátor považuje za parametr je obecný. Tento postup se nazývá *Automatická generalizace*, a může být výkonná Podpora zápisu obecný kód bez zvýšení složitosti.

Například následující funkce kombinuje dva parametry typu do řazené kolekce členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Typ je odvozen bude

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Další informace

Odvození typu je popsána podrobněji F# specifikace jazyka.

## <a name="see-also"></a>Viz také:

- [Automatická generalizace](generics/automatic-generalization.md)