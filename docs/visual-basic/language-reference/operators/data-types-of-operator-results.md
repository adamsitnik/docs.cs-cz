---
title: Datové typy výsledků operátoru (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: bc7f29ae0e29a4c2fbfdf2e40d2226e174a06d3a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856044"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Datové typy výsledků operátoru (Visual Basic)
Visual Basic Určuje datový typ výsledku operace na základě datových typů operandů. V některých případech to může být datový typ s větším rozsahem než u obou operandů.  
  
## <a name="data-type-ranges"></a>Rozsahy datového typu  
 Rozsahy relevantních datových typů, od nejmenších po největší, jsou následující:  
  
- [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) – dvě možné hodnoty  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) – 256 možných celočíselných hodnot  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) – 65 536 (6,5... E + 4) možné celočíselné hodnoty  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) – 4 294 967 296 (4.2... E + 9) možné celočíselné hodnoty  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) – 18446744073709551615 (1.8... E + 19) možné celočíselné hodnoty  
  
- [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) – 1,5... e + 29 možné celočíselné hodnoty, maximální rozsah 7.9... e + 28 (absolutní hodnota)  
  
- [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) – maximální rozsah 3.4... E + 38 (absolutní hodnota)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) – maximální rozsah 1.7... E + 308 (absolutní hodnota)  
  
 Další informace o Visual Basic datových typů najdete v tématu [datové typy](../../../visual-basic/language-reference/data-types/index.md).  
  
 Pokud je operand vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md), Visual Basic aritmetické operátory jsou považovány za nulu.  
  
## <a name="decimal-arithmetic"></a>Desítkové aritmetické operace  
 Všimněte si, že datový typ [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) není plovoucí desetinná čárka ani celé číslo.  
  
 `+`Pokud je `/` `–` `*` `Mod` jeden z operandů,,, nebo operace, a druhý `Single` není nebo `Double`, Visual Basic rozšiřuje druhý operand na `Decimal` `Decimal`. Provede operaci v `Decimal`a výsledný datový typ je `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Aritmetické operace s plovoucí desetinnou čárkou  
 Visual Basic provádí většinu aritmetických výpočtů s plovoucí desetinnou čárkou v [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), což je nejúčinnější datový typ pro tyto operace. Pokud je však jeden operand [jediný](../../../visual-basic/language-reference/data-types/single-data-type.md) a druhý `Double`není, Visual Basic provede operaci v. `Single` Rozšiřuje každý operand tak, jak je to nutné pro příslušný datový typ před operací a výsledek má tento datový typ.  
  
### <a name="-and--operators"></a>Operátory/a ^  
 Operátor je definován pouze pro datové typy [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)a [Double.](../../../visual-basic/language-reference/data-types/double-data-type.md) `/` Visual Basic rozšiřuje každý operand tak, jak je to nutné pro příslušný datový typ před operací a výsledek má tento datový typ.  
  
 V následující tabulce jsou uvedeny typy dat výsledků pro `/` operátor. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Libovolný celočíselný typ|  
|`Decimal`|Desetinné číslo|Single|Double|Desetinné číslo|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Libovolný celočíselný typ|Desetinné číslo|Single|Double|Double|  
  
 Operátor je definován pouze `Double` pro datový typ. `^` Visual Basic rozšiřuje každý operand tak, jak je `Double` potřeba před operací, a výsledný datový typ je vždycky. `Double`  
  
## <a name="integer-arithmetic"></a>Aritmetický typ Integer  
 Výsledný datový typ celočíselné operace závisí na datových typech operandů. Obecně platí, že Visual Basic k určení typu výsledných dat používá následující zásady:  
  
- Pokud mají oba operandy binárního operátoru stejný datový typ, výsledek má tento datový typ. Výjimka je `Boolean`, což je `Short`vynuceno.  
  
- Pokud se operand bez znaménka účastní podepsaného operandu, má výsledek podepsaný typ s aspoň jako velký rozsah jako jeden operand.  
  
- V opačném případě má výsledek obvykle větší ze dvou datových typů operandů.  
  
 Všimněte si, že výsledný datový typ nemusí být stejný jako datový typ operandu.  
  
> [!NOTE]
> Výsledný datový typ není vždy dostatečně velký, aby mohl uchovávat všechny možné hodnoty, které jsou výsledkem operace. <xref:System.OverflowException> Výjimka může nastat, pokud je hodnota pro výsledný datový typ příliš velká.  
  
### <a name="unary--and--operators"></a>Unární operátory + a –  
 V následující tabulce jsou uvedeny typy dat výsledků pro dva unární operátory `+` a. `–`  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unární`+`|Krátké|SByte|Byte|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|Unární`–`|Krátké|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
  
### <a name="-and--operators"></a><\<a > > operátory  
 V následující tabulce jsou uvedeny typy dat výsledků pro dva operátory `<<` bitového posunutí a. `>>` Visual Basic zpracovává každý operátor bitového posunutí jako unární operátor na levém operandu (Bitová maska, která se má posunout).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Krátké|SByte|Byte|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
  
 Pokud `Decimal`je `Long`levý operand, `Single`, `Double`nebo `String`, Visual Basic se pokusí ho převést na `Long` před operací a výsledný datový typ je. Pravý operand (počet bitových pozic k posunu) musí být `Integer` nebo typ, který se rozšíří na. `Integer`  
  
### <a name="binary----and-mod-operators"></a>Operátory Binary +, – \*, a mod  
 V následující tabulce jsou uvedeny typy dat výsledků pro `+` binární a `–` operátory a `*` operátory a `Mod` . Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krátké|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`SByte`|SByte|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`Byte`|Krátké|Krátké|Byte|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`UInteger`|Dlouhé|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Desetinné číslo|  
|`ULong`|Desetinné číslo|Desetinné číslo|ULong|Desetinné číslo|ULong|Desetinné číslo|ULong|Desetinné číslo|ULong|  
  
### <a name="-operator"></a>\\ – operátor  
 V následující tabulce jsou uvedeny typy dat výsledků pro `\` operátor. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krátké|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`SByte`|SByte|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`Byte`|Krátké|Krátké|Byte|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UInteger`|Dlouhé|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|  
|`ULong`|Dlouhé|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|  
  
 Pokud je jeden `\` Operand operátoru [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic se pokusí ho převést na [dlouhou dobu](../../../visual-basic/language-reference/data-types/long-data-type.md) před operací a výsledný datový typ je. `Long`  
  
## <a name="relational-and-bitwise-comparisons"></a>Relační a bitové porovnání  
 Datový typ výsledku relační operace (`=`, `<>`, `<` `>`,, `<=`, `>=`) je vždy `Boolean` [logický datový typ](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Totéž platí pro`And`logické operace (, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) na `Boolean` operandech.  
  
 Výsledný datový typ bitové logické operace závisí na datových typech operandů. Všimněte si `AndAlso` , `OrElse` že a jsou definovány `Boolean`pouze pro `Boolean` a Visual Basic před provedením operace převede každý operand podle potřeby.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= a > = operátory  
 Jsou `Boolean`-li oba operandy, Visual Basic `True` považuje být menší `False`než. Pokud číselný typ je porovnán s `String`, Visual Basic se pokusí `String` převést na na `Double` před operací. Operand `Char` nebo`Date` lze porovnat pouze s jiným operandem stejného datového typu. Výsledný datový typ je vždycky `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bitový operátor NOT  
 V následující tabulce jsou uvedeny typy dat výsledků pro bitový `Not` operátor.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte –|Byte|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
  
 Pokud `Decimal`je `Long`operand, `Single`, `Double`, nebo `String`, Visual Basic se pokusí ho převést na `Long` před operací a výsledný datový typ je.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitové operátory and, or a XOR  
 V následující tabulce jsou uvedeny typy dat výsledků pro bitové `And`operátory, `Or`a. `Xor` Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`SByte`|SByte|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`Byte`|Krátké|Krátké|Byte|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UInteger`|Dlouhé|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|  
|`ULong`|Dlouhé|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|  
  
 Pokud `Decimal`je `Long`operand, `Single`, `Double`, nebo `String`, Visual Basic se pokusí ho převést na `Long` před operací a výsledný datový typ je stejný, jako by tento operand již byl.  
  
## <a name="miscellaneous-operators"></a>Různé operátory  
 Operátor je definován pouze pro zřetězení `String` operandů. `&` Visual Basic každou hodnotu operandu `String` před operací převede tak, jak je potřeba, a výsledný datový typ je vždycky. `String` Pro účely `&` operátoru jsou všechny převody na `String` jsou považovány za rozšiřující, a to i v případě `Option Strict` , `On`že je.  
  
 Operátory `Is` a`IsNot` vyžadují, aby oba operandy byly typu odkazu. `TypeOf`... `Is` výraz vyžaduje, aby první operand byl typu odkazu a druhý operand byl názvem datového typu. Ve všech těchto případech je `Boolean`výsledný datový typ.  
  
 Operátor je definován pouze pro `String` porovnávání vzorů operandů. `Like` Visual Basic se pokusí převést každý operand podle potřeby `String` před operací. Výsledný datový typ je vždycky `Boolean`.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory](../../../visual-basic/language-reference/operators/index.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
