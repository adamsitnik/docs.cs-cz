---
title: Objekty DiscoveryClient a DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 455ccc7f09c13a33b4034099b16b116fd3a8dbdf
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895297"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>Objekty DiscoveryClient a DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy, které se používají na straně klienta pro hledání služeb. <xref:System.ServiceModel.Discovery.DiscoveryClient>poskytuje seznam služeb, které odpovídají určité sadě kritérií, a umožňuje se připojit ke službám. <xref:System.ServiceModel.Discovery.DynamicEndpoint>provede stejnou operaci a navíc se automaticky připojí k jedné ze služeb, které byly nalezeny. Libovolný koncový bod lze navázat do <xref:System.ServiceModel.Discovery.DynamicEndpoint>konfigurace, kritéria hledání je také možné přidat v konfiguraci, což <xref:System.ServiceModel.Discovery.DynamicEndpoint> je užitečné v případě, že budete potřebovat zjišťování ve vašem řešení, ale nechcete měnit klientskou logiku – stačí pouze upravit koncové body. <xref:System.ServiceModel.Discovery.DiscoveryClient>na druhé straně je možné použít k získání přesnější kontroly nad operací vyhledávání. Využití a výhody z nich jsou vypracované níže.  
  
## <a name="discoveryclient"></a>Objektem DiscoveryClient zahozena  
 Definuje synchronní a asynchronní <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> metody Find a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události. <xref:System.ServiceModel.Discovery.DiscoveryClient>  Definuje také synchronní a asynchronní metody Resolve a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> událost. Pomocí metod <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>nebovyhledejteslužby. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Obě tyto metody přijímají <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která umožňuje zadat názvy typů kontraktů, obory, maximální počet požadovaných výsledků a pravidla pro porovnání oboru. Události <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> lze použít při volání metody. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>se aktivuje pokaždé, <xref:System.ServiceModel.Discovery.DiscoveryClient> když přijme odpověď ze služby. Dá se použít k zobrazení indikátoru průběhu znázorňujícího průběh operace Find. Dá se použít i k tomu, aby se při přijetí odpovědi vypracovaly. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Událost se aktivuje po dokončení operace Find. K tomu může dojít, protože byl přijat maximální počet odpovědí nebo pokud <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynula platnost. Po dokončení operace Find se výsledky vrátí do <xref:System.ServiceModel.Discovery.FindResponse> instance. <xref:System.ServiceModel.Discovery.FindResponse> Obsahuje kolekci,kteráobsahujeadresy,názvytypůkontraktů,rozšíření,identifikátorůURInasloucháníaobory<xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> odpovídajícího služby. Tyto informace pak můžete použít k připojení a volání jedné z těchto služeb. Následující příklad ukazuje, jak zavolat metodu System. ServiceModel. Discovery. objektem DiscoveryClient zahozena. Find (System. ServiceModel. Discovery. kritéria hledání) a použít vracená metadata pro volání nalezené služby. Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete seznam koncových bodů, které jste našli, ukládat do mezipaměti a později je použít. Pomocí této mezipaměti můžete vytvořit vlastní logiku, která bude zpracovávat různé stavy selhání.  
  
```csharp
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 Následující příklad ukazuje, jak provést asynchronní operaci Find.  
  
```csharp
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 Použijte metody <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> a k vyhledání služby na základě adresy jejího koncového bodu. <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> To je užitečné, když adresa koncového bodu není síťová adresa. Metody Resolve přebírají instanci <xref:System.ServiceModel.Discovery.ResolveCriteria> , která umožňuje zadat adresu koncového bodu služby, kterou řešíte, maximální dobu trvání operace řešení a sadu rozšíření. Následující příklad ukazuje, jak použít <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodu k vyřešení služby.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>je standardním koncovým bodem (Další informace naleznete v tématu [Standardní koncové body](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)), který provádí zjišťování a automaticky vybere vyhovující službu. Stačí vytvořit <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání v kontraktu pro vyhledání a vazba pro použití a <xref:System.ServiceModel.Discovery.DynamicEndpoint> předání instance klientovi WCF. Následující příklad ukazuje, jak vytvořit a použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> pro volání služby kalkulačky. Zjišťování se provádí při každém otevření klienta. Libovolný koncový bod definovaný v konfiguraci lze také zapnout <xref:System.ServiceModel.Discovery.DynamicEndpoint> `kind ="dynamicEndpoint"` přidáním atributu do konfiguračního elementu koncového bodu.  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a>Viz také:

- [Zjišťování pomocí oborů](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Základy](../../../../docs/framework/wcf/samples/basic-sample.md)
