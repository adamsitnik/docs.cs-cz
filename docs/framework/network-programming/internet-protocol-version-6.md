---
title: Protokol IP (Internet Protocol) verze 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 135d87f126dcdb9689c23adbaaa4786bc69a3e09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182322"
---
# <a name="internet-protocol-version-6"></a>Protokol IP (Internet Protocol) verze 6
Internet Protocol verze 6 (IPv6) je nová sada standardních protokolů pro síťové vrstvy z Internetu. Protokol IPv6 je navržená k řešení mnoha problémů je aktuální verze sady Internet Protocol (označují se termínem IPv4) s ohledem na plnění vyčerpávání, zabezpečení, automatickou konfiguraci, rozšíření a tak dále. Protokol IPv6 se rozšiřují možnosti Internetu povolit nové typy aplikací, jako jsou třeba aplikace peer-to-peer a mobilní. Toto jsou hlavní problémy aktuální protokolu IPv4:  
  
-   Rychlé vyčerpání adresního prostoru.  
  
     To vedlo k využívání síťových adres (NAT), které mapují více privátních adres na jednu veřejnou IP adresu. Hlavní problémy, které vytvořil tento mechanismus zpracování režijní náklady a nedostupnosti začátku do konce.  
  
-   Chybějící podpora hierarchie.  
  
     Z důvodu jeho vlastní třídy předdefinovaného organizace nemá IPv4 true hierarchické podpory. Není možné strukturovat IP adres tak, aby skutečně mapy topologie sítě. Tato chyba zásadní návrh vytvoří potřebné pro velké tabulky směrování k poskytování IPv4 paketů do jakéhokoli umístění na Internetu.  
  
-   Konfigurace složité sítě.  
  
     S podporou protokolu IPv4, musí být adresy staticky přiřadit nebo pomocí protokolu konfigurace, jako je DHCP. V ideálním případě by hostitelé nemusíte spoléhat na správu infrastruktury DHCP. Místo toho by moct konfigurovat sami podle segmentu sítě, ve které se nacházejí.  
  
-   Chybějící integrované ověřování a zachováním důvěrnosti.  
  
     IPv4 nevyžaduje podporu pro každý použitý mechanizmus, který poskytuje ověřování nebo výměnu dat šifrování. Tím se změní s protokolem IPv6. Internet Protocol security (IPSec) je požadavek na podporu IPv6.  
  
 Nová sada protokolů musí splňovat základní požadavky na následující:  
  
-   Ve velkém měřítku směrování a adresování s nízkou režií.  
  
-   Automatická konfigurace pro připojení různých situacích.  
  
-   Integrované ověřování a zachováním důvěrnosti.  
  
 Další informace najdete v tématu [adresování IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [směrování IPv6](../../../docs/framework/network-programming/ipv6-routing.md), [automatickou konfiguraci protokolu IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [povolení a zákaz IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), a [Jak: Upravte konfigurační soubor počítače na povolení podpory IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Odkazy  
 Toto jsou vybrané dokumenty RFC, na které narazíte na [Engineering Task Force IETF (Internet)](https://www.ietf.org/) webu:  
  
-   RFC. 1287, směrem k architektuře budoucí Internet.  
  
-   RFC 1454 porovnání návrhy na další verzi protokolu IP.  
  
-   RFC 2373, Architektura adresování IP verze 6.  
  
-   RFC 2374 formátu agregovatelné globální adresy jednosměrového vysílání IPv6.  
  
 Můžete také najít informace související s IPv6 na [IP verze 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka sokety IPv6](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)
- [Sokety](../../../docs/framework/network-programming/sockets.md)
