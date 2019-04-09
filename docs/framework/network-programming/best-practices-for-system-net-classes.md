---
title: Osvědčené postupy pro třídy System.Net
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: 5bb3ac545613da68d5f370fefbf94b674b70fe64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200945"
---
# <a name="best-practices-for-systemnet-classes"></a>Osvědčené postupy pro třídy System.Net
Následující doporučení vám pomůže s použitím třídy obsažené v <xref:System.Net> k jejich přinášelo maximální výhody:  
  
-   Osvědčené postupy zabezpečení TLS (Transport Layer), najdete v části [zabezpečení TLS (Transport Layer) osvědčené postupy s rozhraním .NET Framework](tls.md).

-   Použití <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> kdykoli je to možné, ne přetypování typu na odvozené třídy. Aplikace, které používají **WebRequest** a **WebResponse** můžete využívat nové internetové protokoly bez nutnosti rozsáhlého kódu změny.  
  
-   Při psaní aplikací ASP.NET, které běží na serveru pomocí **System.Net** třídy, je často vhodnější, z hlediska výkonu použít asynchronní metody pro <xref:System.Net.WebRequest.GetResponse%2A> a <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Počet otevřených připojení k internetového zdroji může mít významný dopad na výkon sítě a propustnost. **System.Net** ve výchozím nastavení používá dvě spojení na aplikaci na hostitele. Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnost <xref:System.Net.ServicePoint> pro vaše aplikace toto číslo můžete navýšit pro konkrétního hostitele. Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnost zvýšit toto výchozí nastavení pro všechny hostitele.  
  
-   Při zápisu protokoly na úrovni soketu, zkuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je to možné místo psaní přímo <xref:System.Net.Sockets.Socket>. Tyto dva klientské zapouzdřují vytváření TCP a UDP sockets aniž by bylo potřeba zpracovat podrobné údaje o připojení.  
  
-   Pokud přístup k serverům, které vyžadují přihlašovací údaje, použijte <xref:System.Net.CredentialCache> třídy za účelem vytvoření mezipaměti přihlašovacích údajů namísto zadávání při každé žádosti. **CredentialCache** třídy vyhledá mezipaměti k vyhledání příslušné přihlašovací údaje prezentovat s žádostí, můžete homogenního odpovědnosti, vytváření a prezentování přihlašovací údaje podle zadané adresy URL.  
  
## <a name="see-also"></a>Viz také:

- [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)
