---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 0820ad6a6d5000ef7ea575e856d883ba5325b1b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230977"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Oborů názvů umožňuje shromažďování informací o událostech sítě, změnách, statistiky a vlastnosti. Můžete také určit, jestli je vzdálený hostitel dosažitelný pomocí <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> třídy.  
  
## <a name="network-availability-and-events"></a>Dostupnost sítě a události  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Třída umožňuje určit, zda došlo ke změně síťové adresy nebo dostupnosti. Tuto třídu použít, vytvořit obslužnou rutinu události ke zpracování změny a přidružte jej k <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> nebo <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Další informace najdete v tématu [jak: Zjištění dostupnosti sítě a vyřešení změn](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Statistika sítě a vlastnosti  
 Můžete shromáždit statistiku sítě a vlastnosti na základě rozhraní nebo protokolu. <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, A <xref:System.Net.NetworkInformation.PhysicalAddress> třídy poskytnout informace o konkrétní síťové rozhraní, zatímco <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, a <xref:System.Net.NetworkInformation.UdpStatistics> třídy poskytnout informace o vrstvy 3 a vrstva 4 paketů. Další informace najdete v tématu [jak: Získejte informace o protokolu a Interface](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Určí, zda vzdálený hostitel dostupné  
 Můžete použít <xref:System.Net.NetworkInformation.Ping> třídu k určení, zda vzdálený hostitel správně nahoru, v síti a je dostupný. Další informace najdete v tématu [jak: Příkaz ping na hostitele](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)
- [Ukázka technologie informace o síti](https://go.microsoft.com/fwlink/?LinkID=179564)
- [Ukázka technologie NetStat nástroj](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Ukázka technologie ping klienta](https://go.microsoft.com/fwlink/?LinkID=179565)
