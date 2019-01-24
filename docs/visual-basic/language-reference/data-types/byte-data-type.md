---
title: Byte – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 8c9787d52667dc026d3fe62ac7f4b3de7e838a93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519785"
---
# <a name="byte-data-type-visual-basic"></a>Byte – datový typ (Visual Basic)
Obsahuje 8 bitů (1bajtový) celá čísla bez znaménka, které v rozsahu od 0 do 255.

## <a name="remarks"></a>Poznámky

Použití `Byte` datový typ binární data obsahovat.  
  
Výchozí hodnota `Byte` je 0.

## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarovat a inicializovat `Byte` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál. Pokud celočíselný literál je mimo rozsah `Byte` (tj. Pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 201, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [celé číslo](integer-data-type.md) k `byte` hodnoty.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální. Desítkové literály mají žádná předpona.

Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Tipy pro programování

-   **Záporná čísla.** Protože `Byte` typ bez znaménka, je ho nemůže představovat záporné číslo. Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `Byte`, Visual Basic Převede výraz, který má `Short` první.
  
-   **Převody formátů.** Když jazyka Visual Basic čte nebo zapisuje soubory nebo při volání knihovny DLL, metody a vlastnosti, můžete automaticky převádět mezi datových formátů. Binární data uložená v `Byte` proměnných a polí se zachovají během tyto převody formátů. Neměli byste používat `String` proměnné pro binární data, protože jeho obsah může být poškozen při převodu mezi formáty ANSI a Unicode.

-   **Rozšíření.** `Byte` Datový typ rozšiřuje na `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Byte` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.
  
-   **Znaky typu.** `Byte` nemá žádný – znak typu literálu nebo – znak typu identifikátoru.

-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Byte?displayProperty=nameWithType> struktury.

## <a name="example"></a>Příklad

 V následujícím příkladu `b` je `Byte` proměnné. Příkazy ukazují rozsah proměnné a do něj aplikaci bitové posunutí – operátory.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Viz také:

- <xref:System.Byte?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
