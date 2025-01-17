---
ms.openlocfilehash: 0ddd554aa114395085a9f8ff41a99ca9a6096a51
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804549"
---
### <a name="certificate-eku-oid-validation"></a>OID rozšířeného použití klíče ověření certifikátu

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6, <xref:System.Net.Security.SslStream> nebo <xref:System.Net.ServicePointManager> třídy provést ověření identifikátor (OID) objektu rozšířené použití klíče (EKU). Kolekce identifikátorů objektu (OID), které označují aplikace, které používají klíč je rozšíření rozšířené použití klíče (EKU). OID rozšířeného použití klíče ověření používá zpětná volání vzdálený certifikát a ujistěte se, že vzdálený certifikát mají správné identifikátory OID pro zamýšlený účel.|
|Doporučení|Pokud tuto změnu nežádoucí, můžete zakázat certifikát OID rozšířeného použití klíče ověření tak, že přidáte následující přepnout na [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) z vaší konfigurační soubor aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je dostupné pouze z důvodů zpětné kompatibility. Jeho použití v opačném případě se nedoporučuje.</blockquote> |
|Scope|Vedlejší|
|Version|4.6|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

