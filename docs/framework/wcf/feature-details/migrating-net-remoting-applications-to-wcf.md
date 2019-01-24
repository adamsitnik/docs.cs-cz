---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 96018b775b858e8ac0d0221135cb5109b0cd81d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509997"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrace aplikací vzdálené komunikace .NET do WCF
**Toto téma se věnuje starší technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj nových projektů. Distribuované aplikace by měla nyní být vyvinuto s použitím WCF.**  
  
 Existují dva způsoby, jak využít výhod WCF se stávajícími aplikacemi .NET Remoting: integrace a migrace. Integrace umožňuje mít .net Remoting 2.0 a WCF s kódem na straně sebe, umožňuje vystavit stejné objekty obchodní přes obě technologie současně bez nutnosti upravovat vaše existující rozhraní .net 2.0 vzdálené komunikace. Integrace vyžaduje, zda jsou spuštěny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 nebo novější. Pokud chcete využít výhod funkcí WCF a není nutné kompatibility při přenosu pomocí vzdálené komunikace 2.0 systémů, můžete migrovat celou službu do WCF. Migrace z verze 2.0 vzdálené komunikace .NET na WCF vyžaduje změny v rozhraní vzdáleného objektu a jeho nastavení konfigurace. Obě tato témata se věnují [ze vzdálené komunikace Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Viz také:
- [Koncepční přehled](../../../../docs/framework/wcf/conceptual-overview.md)
