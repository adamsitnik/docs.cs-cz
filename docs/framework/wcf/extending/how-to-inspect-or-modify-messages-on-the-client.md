---
title: 'Postupy: Kontrola a změny zpráv na klientovi'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 3bf349a5b41c56d5dc3a79107b3fc86968033d54
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606302"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="8dd57-102">Postupy: Kontrola a změny zpráv na klientovi</span><span class="sxs-lookup"><span data-stu-id="8dd57-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="8dd57-103">Může kontrola nebo úprava příchozí a odchozí zprávy přes klienta WCF pomocí implementace <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> a jejich vložení do modul runtime klienta.</span><span class="sxs-lookup"><span data-stu-id="8dd57-103">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="8dd57-104">Další informace najdete v tématu [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8dd57-104">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md).</span></span> <span data-ttu-id="8dd57-105">Je ekvivalentní funkce ve službě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8dd57-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8dd57-106">Příklad úplného kódu najdete v článku [Messageinspectors](../../../../docs/framework/wcf/samples/message-inspectors.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="8dd57-106">For a complete code example see the [Message Inspectors](../../../../docs/framework/wcf/samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="8dd57-107">Chcete-li zkontrolovat nebo upravit zprávy</span><span class="sxs-lookup"><span data-stu-id="8dd57-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="8dd57-108">Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8dd57-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="8dd57-109">Implementace <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> v závislosti na rozsahu, ve kterém chcete vložit zprávu inspektoru klienta.</span><span class="sxs-lookup"><span data-stu-id="8dd57-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="8dd57-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> Umožňuje změnit chování na úrovni koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8dd57-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="8dd57-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> Umožňuje změnit chování na úrovni kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8dd57-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="8dd57-112">Vložit chování před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8dd57-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8dd57-113">Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="8dd57-113">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd57-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="8dd57-114">Example</span></span>  
 <span data-ttu-id="8dd57-115">Následující příklady kódu zobrazit v pořadí:</span><span class="sxs-lookup"><span data-stu-id="8dd57-115">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="8dd57-116">Implementace inspektoru klienta.</span><span class="sxs-lookup"><span data-stu-id="8dd57-116">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="8dd57-117">Chování koncového bodu, který se vkládá inspektor.</span><span class="sxs-lookup"><span data-stu-id="8dd57-117">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="8dd57-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-odvozené třídy, která vám umožní přidávat chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8dd57-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="8dd57-119">Konfigurační soubor, který přidá chování koncového bodu, který vloží zprávu inspektoru klienta do modulu runtime klienta.</span><span class="sxs-lookup"><span data-stu-id="8dd57-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client   
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they   
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element   
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"   
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8dd57-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8dd57-120">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="8dd57-121">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="8dd57-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
