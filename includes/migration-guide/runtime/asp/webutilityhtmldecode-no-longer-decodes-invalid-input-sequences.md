---
ms.openlocfilehash: dfc1a0d05142861ff1c1b7391126d86e09fa71c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803727"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode už dekóduje neplatné vstupní sekvence

|   |   |
|---|---|
|Podrobnosti|Ve výchozím nastavení metody dekódování již neprovádějí dekódování neplatné vstupní sekvence do neplatného řetězce UTF-16. Namísto toho vracejí původní vstup.|
|Doporučení|Změna dekodéru výstupu by měla mít vliv, pouze pokud do řetězců ukládáte binární data namísto dat UTF-16. Pokud chcete explicitně kontrolovat toto chování, nastavte <code>aspnet:AllowRelaxedUnicodeDecoding</code> atribut [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) elementu <code>true</code> abyste povolili starší chování nebo <code>false</code> k povolili aktuální chování.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
