---
title: Double – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 6273f6c9e71f286bdbebc3fe1953988b43de3101
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663209"
---
# <a name="double-data-type-visual-basic"></a>Double – datový typ (Visual Basic)
Blokování podepsané IEEE – 64bitová (8 bajtů) dvojité přesnosti s plovoucí desetinnou čárkou čísla v rozsahu od - 1.79769313486231570E + 308 do - 4.94065645841246544E-324 pro záporné hodnoty a z 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 pro kladné hodnoty. Dvojitá přesnost – čísla ukládání aproximaci reálné číslo.  
  
## <a name="remarks"></a>Poznámky  
 `Double` Datový typ poskytuje řádově největší a co nejmenší možné číslo.  
  
 Výchozí hodnota `Double` je 0.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Přesnost.** Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají přesnou reprezentací v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Koncové nuly.** S plovoucí desetinnou čárkou datové typy, které nemají žádné vnitřní reprezentaci koncové nulové znaky. Například že nerozlišuje mezi 4.2000 a 4.2. V důsledku toho koncové nulové znaky se nezobrazují při zobrazení nebo tisk hodnoty s plovoucí desetinnou čárkou.  
  
- **Znaky typu.** Přidávání znak typu literálu `R` k literálu se z něj stane `Double` datového typu. Například, pokud je následována celočíselnou hodnotu `R`, hodnota se změní na `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Přidávání znak typu identifikátoru `#` k libovolnému identifikátoru se z něj stane `Double`. V následujícím příkladu je proměnná `num` je zadán jako `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
- **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Double?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Double?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Datový typ Single](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
