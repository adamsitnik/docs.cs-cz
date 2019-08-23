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
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="a82bf-102">Postupy: Konfigurace používání sdílení portů ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="a82bf-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="a82bf-103">Nejjednodušší způsob, jak použít sdílení NET. TCP://port v aplikaci Windows Communication Foundation (WCF), je vystavit službu pomocí <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a82bf-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="a82bf-104">Tato vazba poskytuje <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost, která určuje, zda je povoleno sdílení NET. TCP://port pro službu konfigurovanou s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="a82bf-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="a82bf-105">Následující postup ukazuje, jak použít <xref:System.ServiceModel.NetTcpBinding> třídu k otevření koncového bodu v identifikátoru URI (Uniform Resource Identifier) NET. TCP://localhost/MyService, nejprve v kódu a poté pomocí konfiguračních elementů.</span><span class="sxs-lookup"><span data-stu-id="a82bf-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="a82bf-106">Povolení sdílení NET. TCP://port na NetTcpBinding v kódu</span><span class="sxs-lookup"><span data-stu-id="a82bf-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="a82bf-107">Vytvořte službu pro implementaci kontraktu s názvem `IMyService` a zavolejte na `MyService`něj.</span><span class="sxs-lookup"><span data-stu-id="a82bf-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="a82bf-108">Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> nastavte vlastnost na `true`.</span><span class="sxs-lookup"><span data-stu-id="a82bf-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="a82bf-109">Vytvořte a přidejte do `MyService` něj koncový bod služby, který používá sdílení <xref:System.ServiceModel.NetTcpBinding> portů a který naslouchá na identifikátoru URI adresy koncového bodu NET. TCP://localhost/MyService. <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="a82bf-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="a82bf-110">V tomto příkladu se používá výchozí port TCP 808, protože identifikátor URI adresy koncového bodu neurčuje jiné číslo portu.</span><span class="sxs-lookup"><span data-stu-id="a82bf-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="a82bf-111">Vzhledem k tomu, že sdílení portů je explicitně povoleno u přenosové vazby, může tato služba sdílet port 808 s dalšími službami v jiných procesech.</span><span class="sxs-lookup"><span data-stu-id="a82bf-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="a82bf-112">Pokud sdílení portů nebylo povoleno a jiná aplikace již používala port 808, tato služba vyvolá <xref:System.ServiceModel.AddressAlreadyInUseException> při otevření.</span><span class="sxs-lookup"><span data-stu-id="a82bf-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="a82bf-113">Povolení sdílení NET. TCP://port v NetTcpBinding v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="a82bf-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="a82bf-114">Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby pomocí elementů konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a82bf-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a82bf-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a82bf-115">See also</span></span>

- [<span data-ttu-id="a82bf-116">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="a82bf-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="a82bf-117">Postupy: Povolení služby sdílení portů Net. TCP</span><span class="sxs-lookup"><span data-stu-id="a82bf-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
