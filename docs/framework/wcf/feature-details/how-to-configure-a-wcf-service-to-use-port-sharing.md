---
title: 'Postupy: Konfigurace používání sdílení portů ve službě WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: e92ce3468bd43456ac3f838cfc44ea7c6624502b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912218"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Postupy: Konfigurace používání sdílení portů ve službě WCF
Nejjednodušší způsob, jak použít sdílení NET. TCP://port v aplikaci Windows Communication Foundation (WCF), je vystavit službu pomocí <xref:System.ServiceModel.NetTcpBinding>.  
  
 Tato vazba poskytuje <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost, která určuje, zda je povoleno sdílení NET. TCP://port pro službu konfigurovanou s touto vazbou.  
  
 Následující postup ukazuje, jak použít <xref:System.ServiceModel.NetTcpBinding> třídu k otevření koncového bodu v identifikátoru URI (Uniform Resource Identifier) NET. TCP://localhost/MyService, nejprve v kódu a poté pomocí konfiguračních elementů.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Povolení sdílení NET. TCP://port na NetTcpBinding v kódu  
  
1. Vytvořte službu pro implementaci kontraktu s názvem `IMyService` a zavolejte na `MyService`něj.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> nastavte vlastnost na `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Vytvořte a přidejte do `MyService` něj koncový bod služby, který používá sdílení <xref:System.ServiceModel.NetTcpBinding> portů a který naslouchá na identifikátoru URI adresy koncového bodu NET. TCP://localhost/MyService. <xref:System.ServiceModel.ServiceHost>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > V tomto příkladu se používá výchozí port TCP 808, protože identifikátor URI adresy koncového bodu neurčuje jiné číslo portu. Vzhledem k tomu, že sdílení portů je explicitně povoleno u přenosové vazby, může tato služba sdílet port 808 s dalšími službami v jiných procesech. Pokud sdílení portů nebylo povoleno a jiná aplikace již používala port 808, tato služba vyvolá <xref:System.ServiceModel.AddressAlreadyInUseException> při otevření.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Povolení sdílení NET. TCP://port v NetTcpBinding v konfiguraci  
  
1. Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby pomocí elementů konfigurace.  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Viz také:

- [Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Postupy: Povolení služby sdílení portů Net. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
