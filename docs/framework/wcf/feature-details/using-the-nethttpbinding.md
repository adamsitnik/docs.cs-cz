---
title: Používání vazeb NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 47a4da6dd709c300b62a7380e6e0754e31782dd8
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411067"
---
# <a name="using-the-nethttpbinding"></a>Používání vazeb NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding> Vazba určená pro použití protokolu HTTP nebo objektu websocket na straně služby a používá binární kódování ve výchozím nastavení. <xref:System.ServiceModel.NetHttpBinding> zjistí, jestli se používá s kontraktů požadavek odpověď nebo duplexní kontrakt a změnit její chování tak, aby odpovídaly – použije HTTP pro kontraktů požadavek odpověď a protokoly Websocket pro duplexní kontrakty. Toto chování lze přepsat pomocí <xref:System.ServiceModel.Channels.WebSocketTransportUsage> nastavení:  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> – To přinutí WebSockets se použije i pro kontraktů požadavek odpověď.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> – To brání použití objekty Websocket. Pokus o použití duplexního kontraktu s tímto nastavením bude mít za následek výjimku.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> – Toto je výchozí hodnota a chová, jak je popsáno výše.  
  
 <xref:System.ServiceModel.NetHttpBinding> podporuje spolehlivé relace v režimu HTTP a WebSocket režimu. V objektu websocket na straně relace režimu jsou poskytovány přenos.  
  
> [!WARNING]
>  Při použití <xref:System.ServiceModel.NetHttpBinding> a režim přenosu vazby je nastavena na TransferMode.Streamed, velké datové proudy může způsobit zablokování a vypršení časového limitu bude volání. Chcete vyřešit tento problém odesílat menší zprávy nebo použít třídy TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurace služby k použití NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> Může být nakonfigurované stejně jako jakákoli jiná vazba. Následující konfigurace fragment kódu ukazuje, jak se konfigurace služby WCF s <xref:System.ServiceModel.NetHttpBinding>.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 Následující fragment kódu ukazuje, jak přidat <xref:System.ServiceModel.NetHttpBinding> v kódu.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>Viz také:
- [Konfigurace vazeb pro služby](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
