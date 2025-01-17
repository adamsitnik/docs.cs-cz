---
ms.openlocfilehash: 12ba683655319e42368f9f2a6cf7bf70e1dbd77d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859049"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Výchozí SignedXML a SignedXMS algoritmy SHA256 změnit

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7 a dřívějších verzí SignedXML a SignedCMS ve výchozím nastavení SHA1 pro některé operace. Od verze rozhraní .NET Framework 4.7.1, SHA256 je povoleno standardně pro tyto operace. Tato změna je nezbytné, protože SHA1 nelze nadále považovat za zabezpečení.|
|Doporučení|Existují dvě nové hodnoty kontextu přepínačů do ovládacího prvku, jestli je ve výchozím nastavení použije SHA1 (není bezpečné) nebo SHA256:<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>Pro aplikace, že cílové rozhraní .NET Framework 4.7.1 a novější verze, pokud použití SHA256 nežádoucí, můžete obnovit výchozí SHA1 tak, že přidáte následující konfigurační přepínač na [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurace vaší aplikace soubor:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>Pro aplikace, které jsou cíleny na rozhraní .NET Framework 4.7 a starší verze, můžete se rozhodnout do této změny tak, že přidáte následující konfigurační přepínač tak, aby [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.7.1|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|

