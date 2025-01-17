---
title: Řezy (F#)
description: Přečtěte si, jak používat řezy pro F# existující datové typy a jak definovat vlastní řezy pro jiné datové typy.
ms.date: 01/22/2019
ms.openlocfilehash: 2f7b87cda87aad1fdac05b4e14b16f454f8c0461
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733373"
---
# <a name="slices"></a>Řezy

V F#je řez podmnožinou datového typu. Aby bylo možné převzít řezy z datového typu, musí datový typ definovat buď metodu `GetSlice`, nebo v [rozšíření typu](type-extensions.md) , které je v oboru. Tento článek vysvětluje, jak vzít řezy z existujících F# typů a jak definovat vlastní.

Řezy se podobají [indexerům](./members/indexed-properties.md), ale místo toho, aby vydávaly jedinou hodnotu z podkladové datové struktury, poskytují více.

F#v současné době má vnitřní podporu pro vytváření řezů řetězců, seznamů, polí a 2D polí.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Základní řezy se F# seznamy a poli

Nejběžnější typy dat, které jsou rozdělené, jsou F# seznamy a pole. Následující příklad ukazuje, jak to provést se seznamy:

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

Pole řezů je stejně jako v seznamech řezů:

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a>Vytváření řezů multidimenzionálních polí

F#podporuje multidimenzionální pole v F# základní knihovně. Stejně jako u jednorozměrného pole mohou být také užitečné řezy multidimenzionálních polí. Zavedení dalších dimenzí však vyžaduje mírně odlišnou syntaxi, takže můžete pořizovat řezy konkrétních řádků a sloupců.

Následující příklady ukazují, jak vytvořit řezy 2D pole:

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

F# Základní knihovna nedefinuje`GetSlice`pro 3D pole. Pokud chcete rozdělit takové nebo jiné pole více dimenzí, je nutné definovat člena `GetSlice` sami.

## <a name="defining-slices-for-other-data-structures"></a>Definování řezů pro jiné datové struktury

F# Základní knihovna definuje řezy pro omezené sady typů. Pokud chcete definovat řezy pro více datových typů, můžete tak učinit buď v samotné definici typu, nebo v rozšíření typu.

Tady je příklad, jak můžete definovat řezy pro třídu <xref:System.ArraySegment%601>, abyste umožnili pohodlné manipulaci s daty:

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Použít vkládání k zamezení zabalení, pokud je to nezbytné

Pokud definujete řezy pro typ, který je ve skutečnosti strukturou, doporučujeme, abyste `inline` `GetSlice` člen. F# Kompilátor optimalizuje volitelné argumenty a vyloučí případné přidělení haldy jako výsledek vytváření řezů. To je důležité pro vytváření řezů, jako je například <xref:System.Span%601>, které nelze přidělit haldě.

```fsharp
open System

type ReadOnlySpan<'T> with
    // Note the 'inline' in the member definition
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a>Viz také:

- [Indexované vlastnosti](./members/indexed-properties.md)
