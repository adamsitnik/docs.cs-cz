---
ms.openlocfilehash: 130c26b7d135db232eb40a2c466aa3bdb2481ace
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858442"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Perský kalendář nyní používá algoritmus hidžra sluneční soustavy.

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6 <xref:System.Globalization.PersianCalendar?displayProperty=name> třída používá algoritmus sluneční hidžra. Převod dat mezi <xref:System.Globalization.PersianCalendar?displayProperty=name> a ostatních kalendářích, které může vytvořit výsledek mírně lišit od verze rozhraní .NET Framework 4.6 pro data starší než 1 800 nebo pozdější než 2023 (gregoriánského). Navíc <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> je nyní <code>March 22, 0622</code> místo <code>March 21, 0622</code>.|
|Doporučení|Mějte na paměti, že některá data časnému nebo pozdní může mírně lišit při používání perského kalendáře v rozhraní .NET Framework 4.6. Navíc při serializaci dat mezi procesy, které můžou běžet na různé verze rozhraní .NET Framework, nebudou ukládat je jako perského kalendáře řetězců kalendářních dat (protože mohou být tyto hodnoty odlišné).|
|Scope|Vedlejší|
|Version|4.6|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|

