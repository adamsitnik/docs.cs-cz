---
title: Decimal – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 892824b61cfb6a0172361d220c638cab0a78565d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700867"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal – datový typ (Visual Basic)

Obsahuje podepsané 128 hodnoty (16 bajtů) představující 96-bit (12 bajtů) celočíselných čísel, jejichž velikost se škáluje proměnnou výkonem 10. Faktor škálování určuje počet číslic vpravo od desetinné čárky. Rozsah je od 0 do 28. S měřítkem 0 (bez desetinných míst) je největší možná hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E + 28). S 28 desetinnými místy je největší hodnota +/-7.9228162514264337593543950335 a nejmenší nenulová hodnota je +/-0,0000000000000000000000000001 (+/-1E-28).

## <a name="remarks"></a>Poznámky

Datový typ `Decimal` poskytuje největší počet platných číslic pro číslo. Podporuje až 29 platných číslic a může reprezentovat hodnoty převyšující 7,9228 × 10 ^ 28. Je zvláště vhodná pro výpočty, jako je finanční, které vyžadují velký počet číslic, ale nemůžou tolerovat chyby při zaokrouhlování.

Výchozí hodnota `Decimal` je 0.

## <a name="programming-tips"></a>Tipy k programování

- **Číslic.** `Decimal` není datový typ s plovoucí desetinnou čárkou. Struktura `Decimal` obsahuje binární celočíselnou hodnotu společně s bitem znaménka a koeficientem škálování celého čísla, který určuje, jaká část hodnoty je desítková frakce. Z tohoto důvodu jsou hodnoty `Decimal` přesnější reprezentace v paměti než typy s plovoucí desetinnou čárkou (`Single` a `Double`).

- **Předepsané.** Datový typ `Decimal` je nejpomalejší ze všech číselných typů. Před výběrem datového typu byste měli zvážit důležitost přesnosti oproti výkonu.

- **Rozšiřující.** Datový typ `Decimal` se rozšíří na `Single` nebo `Double`. To znamená, že můžete převést `Decimal` na některý z těchto typů bez výskytu chyby <xref:System.OverflowException?displayProperty=nameWithType>.

- **Koncové nuly.** Visual Basic neukládá koncové nuly v literálu `Decimal`. Proměnná `Decimal` však zachovává všechny koncové nuly získané výpočtem. Toto dokládá následující příklad.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  Výstup `MsgBox` v předchozím příkladu je následující:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Znaky typu.** Připojení znaku typu literálu `D` do literálu vynutí jej datový typ `Decimal`. Připojení znaku typu identifikátoru `@` k jakémukoli identifikátoru vynutí `Decimal`.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Decimal?displayProperty=nameWithType>.

## <a name="range"></a>Rozsah
 Je možné, že budete muset použít znak `D`, abyste přiřadili velkou hodnotu proměnné nebo konstantě `Decimal`. Tento požadavek je způsoben tím, že kompilátor interpretuje literál jako `Long`, pokud literální znak typu se neřídí literálem, jak ukazuje následující příklad.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

Deklarace `bigDec1` nevyprodukuje přetečení, protože hodnota, která je přiřazena, spadá do rozsahu pro `Long`. Hodnotu `Long` lze přiřadit proměnné `Decimal`.

Deklarace `bigDec2` generuje chybu přetečení, protože hodnota, která je přiřazena, je pro `Long` příliš velká. Vzhledem k tomu, že číselný literál nemůže být nejdříve interpretován jako `Long`, nelze jej přiřadit proměnné `Decimal`.

U `bigDec3` znak typu literálu `D` vyřeší problém tím, že kompilátor vynutí interpretaci literálu jako `Decimal` namísto jako `Long`.

## <a name="see-also"></a>Viz také:

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Single](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
