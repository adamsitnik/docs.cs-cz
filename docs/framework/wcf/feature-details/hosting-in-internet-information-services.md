---
title: Hostování v Internetové informační službě
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 3940d8436ba5441d4e884879213a7a782214cb05
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486753"
---
# <a name="hosting-in-internet-information-services"></a>Hostování v Internetové informační službě
Jednou z možností pro hostování služby Windows Communication Foundation (WCF) je v rámci Internetové informační služby (IIS) aplikace. Tento model hostingu je podobný modelu používané technologie ASP.NET a webových služeb ASP.NET Web services (ASMX).  
  
## <a name="versions-of-iis"></a>Verze služby IIS  
 WCF je možné hostovat na následující verze služby IIS na následující operační systémy:  
  
- Služba IIS 5.1 na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Toto prostředí je užitečné pro návrh a vývoj aplikace hostované službou IIS, které později nasazených v serverovém operačním systému, jako [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
- Služba IIS 6.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Služba IIS 6.0 poskytuje model pokročilé proces, který nabízí lepší škálovatelnost, spolehlivost a izolace aplikací. Toto prostředí je vhodná pro produkční nasazení služby WCF, které používají komunikaci pomocí protokolu HTTP výhradně.  
  
- Služba IIS 7.0 na [!INCLUDE[wv](../../../../includes/wv-md.md)] a [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. Služba IIS 7.0 poskytuje stejný model pokročilé zpracování jako služby IIS 6.0, ale pomocí služby Aktivace procesu Windows (WAS) umožňuje aktivaci a síťovou komunikaci přes jiné protokoly než HTTP. Toto prostředí je vhodný pro vývoj služeb WCF, které komunikují přes všechny síťové protokoly podporované službou WCF (včetně protokolu HTTP, net.tcp, net.pipe a net.msmq). Další informace o WAS najdete v tématu [hostování v aktivační službě procesů Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
- [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) funguje s IIS 7.0 a Windows Process Activation Service (WAS), k poskytování bohatých aplikací hostitelské prostředí služby NET4 WCF a WF. Mezi tyto výhody patří správa životního cyklu procesu, proces recykluje, sdílené hostování, rychlou ochranu, osamocení procesu, na vyžádání aktivace a sledování stavu. Podrobné informace najdete v tématu [funkce hostování AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) a [AppFabric hostování koncepty](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Výhody hostování IIS  
 Hostování služby WCF v IIS má několik výhod:  
  
- Služby WCF hostované v IIS se nasazují a spravují podobně jako jakýkoli jiný typ aplikace služby IIS, včetně aplikací ASP.NET a ASMX.  
  
- Služba IIS poskytuje aktivace procesu, správu stavu a recyklaci funkce pro zvýšení spolehlivosti hostovaných aplikací.  
  
- Jako je ASP.NET služby WCF hostované v technologii ASP.NET využít výhod ASP.NET model sdíleného hostingu kde více aplikací jsou umístěny v běžné pracovní proces pro hustota lepší využití serverových a škálovatelnost.  
  
- Služby WCF hostované ve službě IIS pomocí stejného modelu dynamická kompilace jako ASP.NET 2.0, která zjednodušuje vývoj a nasazení hostovaných služeb.  
  
 Když se rozhodujete hostovat služby WCF v IIS, je dobré si uvědomit, že služba IIS 5.1 a 6.0 omezeny pouze komunikaci pomocí protokolu HTTP. Další informace o výběru hostitelské prostředí najdete v tématu [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Nasazení služby WCF hostované IIS  
 Vývoj a nasazení služby WCF hostované IIS se skládá z následujících úloh:  
  
- Zajistěte, aby služba IIS, ASP.NET, WCF a aktivace součást služeb HTTP WCF jsou správně nainstalovaný a zaregistrovaný.  
  
- Vytvoření nové aplikace služby IIS, nebo znovu použít stávající aplikaci ASP.NET.  
  
- Vytvoření souboru .svc pro službu WCF.  
  
- Nasazení implementace služby do aplikace služby IIS.  
  
- Konfigurace služby WCF.  
  
 Informace o těchto úloh, naleznete v tématu [nasazení služby WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET  
 Může být služby WCF hostované buď na straně po boku s technologií ASP.NET nebo v režimu kompatibility ASP.NET, ve kterém můžete služby využívat všech výhod funkcí poskytovaných službou platformu aplikace ASP.NET Web. Informace o těchto funkcích naleznete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [Nasazení služby WCF hostované Internetovou informační službou](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [Služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Osvědčené postupy hostování Internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Konfigurace Internetové informační služby 7.0 pro Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
