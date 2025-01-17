---
ms.openlocfilehash: ae3766e2045b5834fbf6ea20415942413b1590c0
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858630"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>Služby WCF, které používají NETTCP zabezpečení SSL a ověřování pomocí certifikátu MD5

|   |   |
|---|---|
|Podrobnosti|Rozhraní .NET Framework 4.6 přidá do seznamu WCF SSL výchozí protokol TLS 1.1 a TLS 1.2. Když klientských i serverových počítačích mít rozhraní .NET Framework 4.6 nebo novější, použije se pro vyjednávání protokolu TLS 1.2. Protokol TLS 1.2 nepodporuje ověřování pomocí certifikátu MD5. V důsledku toho pokud zákazník používá certifikát MD5, klienta WCF se nepodaří připojit ke službě WCF.|
|Doporučení|Tento problém můžete obejít tak, aby klient WCF můžete připojit k serveru WCF pomocí některého z následujících akcí:<ul><li>Aktualizujte certifikát nechcete použít algoritmus MD5. Toto je doporučené řešení.</li><li>Pokud se vazba není dynamicky nakonfigurována ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace pro použití protokolu TLS 1.1 nebo starší verzi protokolu. To umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.</li></ul> <blockquote> [!WARNING] Toto řešení se nedoporučuje, protože certifikátu s algoritmem hash MD5 se považuje za nezabezpečené.</blockquote> Následující konfigurační soubor provede následující:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>Pokud je vazba konfigurována dynamicky ve zdrojovém kódu, aktualizujte <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> vlastnost na používání protokolu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> nebo starší verzi protokolu ve zdrojovém kódu.</li></ul> <blockquote> [!WARNING] Toto řešení se nedoporučuje, protože certifikátu s algoritmem hash MD5 se považuje za nezabezpečené.</blockquote> |
|Scope|Vedlejší|
|Version|4.6|
|type|Modul runtime|

