---
title: Tabulka explicitních číselných převodů - C# odkaz
ms.custom: seodec18
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 24f7401538eb1eeb675e6c3de265688780d6b91a
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424200"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabulka explicitních číselných převodů (referenční dokumentace jazyka C#)

V následující tabulce jsou uvedeny předdefinované explicitní převody mezi číselnými typy .NET, u kterých se žádné [implicitní převod](implicit-numeric-conversions-table.md).

|From|Chcete-li|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`byte`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[byte](../builtin-types/integral-numeric-types.md)|`sbyte` Nebo `char`|  
|[short](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, nebo `char`|  
|[int](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[uint](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, nebo `char`|  
|[long](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, nebo `char`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, nebo `char`|  
|[char](char.md)|`sbyte`, `byte`, nebo `short`|  
|[float](float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, nebo `decimal`|  
|[double](double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`|  
|[decimal](decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, nebo `double`|  
  
## <a name="remarks"></a>Poznámky  
  
- Explicitní číselný převod může způsobit ztrátu přesnosti nebo výsledek v došlo k výjimce, obvykle <xref:System.OverflowException>.  

- Při převodu hodnoty celočíselného typu na jiný celočíselný typ, výsledek závisí na přetečení [kontrola kontextu](checked-and-unchecked.md). Ve zkontrolovaném kontextu převod je úspěšný, pokud je hodnota zdrojového rozsahu cílového typu. V opačném případě <xref:System.OverflowException> je vyvolána výjimka. V nekontrolovaném kontextu převod vždy úspěšná a probíhá následujícím způsobem:

  - Pokud typ zdroje je větší než cílový typ, pak je rozdělená do zdrojové hodnoty se zahodí jeho "navíc" nejvýznamnější bity. Výsledek je pak považován za hodnotu cílového typu.

  - Pokud typ zdroje je menší než cílový typ, pak zdrojová hodnota je rozšířena o znaménko nebo nulou tak, aby se stejnou velikostí jako typ cíle. Rozšířením znaménka se používá, pokud typ zdroje je podepsaný; nulové rozšíření se používá, pokud se zdrojový typ není podepsaný. Výsledek je pak považován za hodnotu cílového typu.

  - Pokud se stejnou velikostí jako cílový typ je typ zdrojového, zdrojová hodnota je považován za hodnotu cílového typu.
  
- Při převodu `decimal` hodnota na integrální typ., tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud je výsledný celočíselné hodnoty mimo rozsah cílového typu <xref:System.OverflowException> je vyvolána výjimka.  
  
- Při převodu `double` nebo `float` hodnota na integrální typ., tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud výsledná celočíselné hodnoty je mimo rozsah cílového typu, výsledek závisí na přetečení [kontrola kontextu](checked-and-unchecked.md). Ve zkontrolovaném kontextu <xref:System.OverflowException> je vyvolána, když v nekontrolovaném kontextu, výsledek je neurčená hodnota cílového typu.  
  
- Při převodu `double` k `float`, `double` hodnota je zaokrouhlená na nejbližší `float` hodnotu. Pokud `double` hodnota je příliš malá nebo příliš velký a nevejde do cílového typu, výsledkem bude nula nebo nekonečno.  
  
- Při převodu `float` nebo `double` k `decimal`, zdrojová hodnota je převedena na `decimal` vyjádření a zaokrouhlí na nejbližší číslo po 28 desetinné místo podle potřeby. V závislosti na hodnotě zdrojovou hodnotu může dojít jednu z následujících výsledků:  

  - Pokud zdrojová hodnota je příliš malá, aby se dala vyjádřit jako `decimal`, výsledkem bude nule.  

  - Pokud zdrojová hodnota NaN (není číslo), nekonečno, nebo příliš velký, aby se dala vyjádřit jako `decimal`, <xref:System.OverflowException> je vyvolána výjimka.  
  
- Při převodu `decimal` k `float` nebo `double`, `decimal` hodnota je zaokrouhlená na nejbližší `double` nebo `float` hodnotu.  
  
 Další informace o explicitních převodů, najdete v článku [explicitních převodů](~/_csharplang/spec/conversions.md#explicit-conversions) část [specifikace jazyka C#](../language-specification/index.md).
  
## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Přetypování a převody typu](../../programming-guide/types/casting-and-type-conversions.md)
- [() – operátor](../operators/type-testing-and-conversion-operators.md#cast-operator-)
- [Celočíselné typy](../builtin-types/integral-numeric-types.md)
- [Tabulka typů s plovoucí desetinnou čárkou](floating-point-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)
