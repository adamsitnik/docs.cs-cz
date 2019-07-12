---
ms.openlocfilehash: a7f61ad42305377331a7f65fb91d49d709d1b728
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803175"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open selhání ve Windows 7 s IFS Winsock BSP nebo LSP k dispozici

|   |   |
|---|---|
|Podrobnosti|<xref:System.Data.SqlClient.SqlConnection.Open> a <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> selhat v rozhraní .NET Framework 4.5, pokud běží na počítači s Windows 7 s IFS Winsock BSP nebo LSP jsou k dispozici v počítači. Chcete-li zjistit, jestli je nainstalovaná IFS BSP nebo LSP, použijte <code>netsh WinSock Show Catalog</code> příkaz a zkontrolujte každý <code>Winsock Catalog Provider Entry</code> položku, která je vrácena. Pokud má hodnota příznaků služby <code>0x20000</code> bitem, poskytovatele používá IFS popisovače a bude fungovat správně. Pokud <code>0x20000</code> bit vymazat (Nenastaveno), je IFS BSP nebo LSP.|
|Doporučení|Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže lze se vyhnout upgradem rozhraní .NET Framework. Alternativně můžete se vyhnout tak, že odeberete všechny nainstalované bez - IFS Winsock LSP.|
|Scope|Vedlejší|
|Version|4.5|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

