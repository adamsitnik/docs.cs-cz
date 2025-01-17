---
title: Chování publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 4b3bc0490f791776793e91de0bb8608264663af5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044836"
---
# <a name="metadata-publishing-behavior"></a>Chování publikování metadat
Ukázka chování publikování metadat ukazuje, jak řídit funkce publikování metadat služby. Aby nedocházelo k neúmyslnému zveřejnění potenciálně citlivých metadat služby, služba výchozí konfigurace služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je standardně zabezpečené, ale také znamená, že nemůžete použít nástroj pro import metadat (například Svcutil. exe), aby se vygeneroval kód klienta vyžadovaný pro volání služby, pokud není v konfiguraci explicitně povolený chování publikování metadat služby.  
  
> [!IMPORTANT]
> Pro přehlednost Tato ukázka ukazuje, jak vytvořit nezabezpečený koncový bod publikování metadat. Tyto koncové body jsou možná dostupné anonymním neověřeným příjemcům a před nasazením těchto koncových bodů je nutné zajistit, aby bylo zajištěno, že bude jejich veřejněné zveřejnění metadat služby vhodné. Ukázku zabezpečení koncového bodu metadat najdete v ukázce pro [Vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) .  
  
 Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Aby služba zveřejnila metadata, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být ve službě nakonfigurovaná. Pokud je toto chování k dispozici, můžete publikovat metadata tím, že nakonfigurujete <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod, který zveřejní kontrakt jako implementaci protokolu WS-MetadataExchange (MEX). V rámci této smlouvy byl uveden zkrácený název konfigurace "IMetadataExchange". Tato ukázka používá `mexHttpBinding`, což je pohodlná standardní vazba, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastaveným na `None`. V koncovém bodu se používá relativní adresa "MEX", která při překladu na základě základní adresy služeb má za následek adresu `http://localhost/servicemodelsamples/service.svc/mex`koncového bodu. Následující příklad ukazuje konfiguraci chování:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Následující příklad ukazuje koncový bod MEX.  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 Tato ukázka nastavuje <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost na `true`, která také zpřístupňuje metadata služby pomocí protokolu HTTP GET. Aby bylo možné povolit koncový bod metadat HTTP GET, musí mít služba základní adresu HTTP. Řetězec `?wsdl` dotazu se používá na základní adrese služby pro přístup k metadatům. Například, chcete-li zobrazit WSDL pro službu ve webovém prohlížeči, použijte tuto adresu `http://localhost/servicemodelsamples/service.svc?wsdl`. Alternativně můžete toto chování použít k vystavení metadat přes HTTPS <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> nastavením na. `true` Vyžaduje se základní adresa HTTPS.  
  
 Pokud chcete získat přístup ke koncovému bodu služby MEX, použijte nástroj pro doSvcutilení [metadat (ServiceModel. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Tím se vygeneruje klient na základě metadat služby.  
  
 Pokud chcete získat přístup k metadatům služby pomocí protokolu HTTP GET, najeďte na `http://localhost/servicemodelsamples/service.svc?wsdl`prohlížeč.  
  
 Pokud toto chování odstraníte a pokusíte se otevřít službu, získáte výjimku. K této chybě dochází, protože bez chování nemá koncový bod nakonfigurovaný se `IMetadataExchange` smlouvou žádnou implementaci.  
  
 Pokud nastavíte `HttpGetEnabled` na `false`, zobrazí se stránka s CalculatorService s usnadněním, místo abyste viděli metadata služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
