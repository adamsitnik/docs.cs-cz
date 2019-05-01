---
title: Základní typy
description: Objevte základní typy, které se používají v F# jazyka.
ms.date: 07/09/2018
ms.openlocfilehash: 74a276792e2566b8f18b87f4bdcfb923b713b9c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959112"
---
# <a name="basic-types"></a>Základní typy

Toto téma obsahuje základní typy, které jsou definovány v F# jazyka. Tyto typy jsou nejdůležitější v F#, které tvoří základ pro téměř každý F# programu. Jsou množinou primitivní typy .NET.

|Type|Typ formátu .NET|Popis|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|Možné hodnoty jsou `true` a `false`.|
|`byte`|<xref:System.Byte>|Hodnoty od 0 do 255.|
|`sbyte`|<xref:System.SByte>|Hodnoty -128 až 127.|
|`int16`|<xref:System.Int16>|Hodnoty od-32 768 do 32767.|
|`uint16`|<xref:System.UInt16>|Hodnoty od 0 do 65535.|
|`int`|<xref:System.Int32>|Hodnoty z-2,147,483,648 do 2 147 483 647.|
|`uint32`|<xref:System.UInt32>|Hodnoty od 0 do 4 294 967 295.|
|`int64`|<xref:System.Int64>|Hodnoty z-9,223,372,036,854,775,808 9,223,372,036,854,775,807.|
|`uint64`|<xref:System.UInt64>|Hodnoty od 0 do 18,446,744,073,709,551,615.|
|`nativeint`|<xref:System.IntPtr>|Nativní ukazatel jako celé číslo se znaménkem.|
|`unativeint`|<xref:System.UIntPtr>|Nativní ukazatel jako celé číslo bez znaménka.|
|`char`|<xref:System.Char>|Hodnoty znaků Unicode.|
|`string`|<xref:System.String>|Text v kódu Unicode.|
|`decimal`|<xref:System.Decimal>|S plovoucí desetinnou čárkou datový typ, který má alespoň 28 platných číslic.|
|`unit`|Není k dispozici|Ukazuje na nepřítomnost skutečnou hodnotu. Typ má pouze jeden formální hodnotu, která je označena `()`. Hodnota jednotka `()`, se často používá jako zástupný symbol, kdy je potřeba hodnotu, ale žádná skutečná hodnota je k dispozici nebo dává smysl.|
|`void`|<xref:System.Void>|Označuje žádný typ nebo hodnota.|
|`float32`, `single`|<xref:System.Single>|Bod typ s plovoucí desetinnou čárkou 32-bit.|
|`float`, `double`|<xref:System.Double>|Bod typ s plovoucí desetinnou čárkou 64bitové.|

> [!NOTE]
> Můžete provést výpočty s celými čísly příliš velký pro 64bitovou celočíselnou hodnotu typu pomocí [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu. `bigint` není považováno za základní typ; je zkratka pro `System.Numerics.BigInteger`.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)