---
ms.openlocfilehash: b23909c53b451b4b18bf0ccdf59f51e7c8e3114f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802485"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Nesprávné generování kódu při předávání a porovnávání hodnot UInt16

|   |   |
|---|---|
|Podrobnosti|Z důvodu změny zavedené v rozhraní .NET Framework 4.7, v některých případech kód generovaný kompilátorem JIT v aplikacích spuštěných na rozhraní .NET Framework 4.7 nesprávně porovná dva <code>T:System.UInt16</code> hodnoty. Další informace najdete v tématu [11508 # problému: Bezobslužná nesprávná funkce codegen při předávání a porovnávání argumentů ushort](https://github.com/dotnet/coreclr/issues/11508) na webu GitHub.com.|
|Doporučení|Pokud narazíte na problémy při porovnání hodnoty bez znaménka 16 bitů v rozhraní .NET Framework 4.7, upgradujte na rozhraní .NET Framework 4.7.1.|
|Scope|Edge|
|Version|4.7|
|type|Modul runtime|

