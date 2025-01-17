---
ms.openlocfilehash: 3b3df8ad736f8f1c6a09e3349379b8c689cf731c
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235497"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Výchozí hodnota ServicePointManager.SecurityProtocol je SecurityProtocolType.System.Default

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací určených pro rozhraní .NET Framework 4.7, výchozí hodnota <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> vlastnost <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Tato změna umožňuje rozhraní .NET Framework síťová rozhraní API podle SslStream (jako je například FTP, HTTPS a SMTP) dědění výchozí protokoly zabezpečení z operačního systému místo pevně definovaných hodnot, které jsou definované pomocí rozhraní .NET Framework. Výchozí hodnota se liší podle operačního systému a všechny vlastní konfiguraci provedené správcem systému. Informace o výchozím protokolem SChannel v jednotlivých verzích operačního systému Windows, naleznete v tématu [protokolů TLS/SSL (zprostředkovateli zabezpečení Schannel)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>Pro aplikace, které jsou cíleny na starší verzi rozhraní .NET Framework, výchozí hodnota <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> vlastnost závisí na verzi rozhraní .NET Framework, který je cílem. Najdete v článku [části sítě mění se cílení změn pro migraci z rozhraní .NET Framework 4.5.2 na 4.6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) Další informace.|
|Doporučení|Tato změna ovlivní aplikace, které jsou cíleny na rozhraní .NET Framework 4.7 nebo novější verze. </br>Pokud byste radši chtěli použít definovaného protokolu, spíše než spoléhání se na výchozí systémové hodnoty, můžete explicitně nastavit hodnotu <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> vlastnost.</br>Pokud tuto změnu nežádoucí, můžete zrušit jeho přidáním nastavení konfigurace, které [ \<runtime >](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad ukazuje, jak <code>&lt;runtime&gt;</code> oddílu a <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> odhlásit přepínače:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.7|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|
