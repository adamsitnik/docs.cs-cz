---
ms.openlocfilehash: ab7731d34aad5b6b6481f13ba11b778393e2cac2
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858478"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase náhodně UseRandomizedStringHashAlgorithm už posunut

|   |   |
|---|---|
|Podrobnosti|Před rozhraní .NET Framework 4.6, hodnota <xref:System.AppDomainSetup.DynamicBase> by se náhodně mění mezi doménami aplikace nebo mezi procesy, pokud userandomizedstringhashalgorithm – byla povolena v konfiguračním souboru aplikace. Počínaje .NET Framework 4.6 <xref:System.AppDomainSetup.DynamicBase> vrátí stabilní výsledek mezi různými instancemi produktu běžící aplikaci a mezi doménami aplikací lišit. Dynamické základny budou stále lišit pro různé aplikace; Tato změna odebere jenom náhodných názvů element pro různé instance stejné aplikace.|
|Doporučení|Mějte na paměti tuto povolení <code>UseRandomizedStringHashAlgorithm</code> opozdí ve vykonání <xref:System.AppDomainSetup.DynamicBase> se náhodně mění. V případě potřeby náhodná základní musí být vytvořený v kódu vaší aplikace, nikoli přes toto rozhraní API.|
|Scope|Edge|
|Version|4.6|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|

