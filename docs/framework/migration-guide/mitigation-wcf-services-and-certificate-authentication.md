---
title: 'Omezení rizik: služby WCF a ověřování certifikátů'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: 8c8493efa2c3223809ad87e01e3faddaea859ca8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457792"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Omezení rizik: služby WCF a ověřování certifikátů

.NET Framework 4,6 přidá do seznamu výchozí seznam protokolu WCF SSL protokol TLS 1,1 a TLS 1,2. Pokud jsou v klientské i serverové počítače nainstalované .NET Framework 4,6 nebo novější, pro vyjednávání se používá TLS 1,2.

## <a name="impact"></a>Dopad

TLS 1,2 nepodporuje ověřování certifikátu MD5. Výsledkem je, že pokud zákazník používá certifikát SSL, který používá MD5 pro algoritmus hash, klient služby WCF se nemůže připojit ke službě WCF. Další informace najdete v tématu [zmírnění rizik: služby WCF a ověřování certifikátů](mitigation-wcf-services-and-certificate-authentication.md).

## <a name="mitigation"></a>Zmírnění

Tento problém můžete obejít tak, aby se klient WCF mohl připojit k serveru WCF pomocí kterékoli z následujících možností:

- Aktualizujte certifikát, aby nepoužíval algoritmus MD5. Toto je doporučené řešení.

- Pokud není vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1,1 nebo dřívější verzi protokolu. To vám umožní pokračovat v používání certifikátu s algoritmem hash MD5.

  > [!CAUTION]
  > Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

  Následující konfigurační soubor provede toto:

  ```xml
  <configuration>
      <system.serviceModel>
          <bindings>
              <netTcpBinding>
                  <binding>
                      <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                          <transport clientCredentialType="None|Windows|Certificate"
                                              protectionLevel="None|Sign|EncryptAndSign"
                                              sslProtocols="Ssl3|Tls1|Tls11">
                          </transport>
                      </security>
                  </binding>
              </netTcpBinding>
          </bindings>
      </system.serviceModel>
  </configuration>
  ```

- Pokud je vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte vlastnost <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> na použití TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verze protokolu ve zdrojovém kódu.

  > [!CAUTION]
  > Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
