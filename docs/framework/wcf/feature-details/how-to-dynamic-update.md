---
title: 'Postupy: Dynamická aktualizace'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 0a103e980d0d1be08f3ae6850c6af64405582c7b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972079"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="5531e-102">Postupy: Dynamická aktualizace</span><span class="sxs-lookup"><span data-stu-id="5531e-102">How To: Dynamic Update</span></span>
<span data-ttu-id="5531e-103">Toto téma popisuje základní kroky potřebné k vytvoření a dynamické aktualizaci konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="5531e-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="5531e-104">V tomto příkladu se konfigurace počátečního směrování získá z konfiguračního souboru a směruje všechny zprávy do služby regularCalc kalkulačky. je ale následně Aktualizováno programově, aby se změnil cílový koncový bod služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="5531e-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5531e-105">V mnoha implementacích bude konfigurace plně dynamická a nebude se spoléhat na výchozí konfiguraci. Existují však některé scénáře, jako je například v tomto tématu, kde je žádoucí mít výchozí stav konfigurace při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="5531e-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5531e-106">Dynamické aktualizace se vyskytují pouze v paměti a nevedou k úpravě konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="5531e-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="5531e-107">RegularCalc i roundingCalc podporují stejné operace sčítání, odčítání, násobení a dělení; roundingCalc však Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="5531e-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="5531e-108">Konfigurační soubor se používá ke konfiguraci služby ke směrování všech zpráv do služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="5531e-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="5531e-109">Po spuštění směrovací služby se služba znovu nakonfiguruje tak, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> aby směrovala zprávy do služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="5531e-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="5531e-110">Implementace počáteční konfigurace</span><span class="sxs-lookup"><span data-stu-id="5531e-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="5531e-111">Vytvořte základní konfiguraci směrovací služby zadáním koncových bodů služby vystavených službou.</span><span class="sxs-lookup"><span data-stu-id="5531e-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="5531e-112">Následující příklad definuje jeden koncový bod služby, který se použije pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="5531e-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="5531e-113">Definuje také koncový bod klienta, který bude použit k posílání zpráv do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="5531e-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. <span data-ttu-id="5531e-114">Definujte filtr, který se použije ke směrování zpráv do cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="5531e-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="5531e-115">V tomto příkladu se používá filtr MatchAll ke směrování všech zpráv do regularCalcEndpoint, které jste definovali dříve.</span><span class="sxs-lookup"><span data-stu-id="5531e-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="5531e-116">Následující příklad definuje tabulku filtru a filtru.</span><span class="sxs-lookup"><span data-stu-id="5531e-116">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. <span data-ttu-id="5531e-117">Chcete-li vyhodnotit příchozí zprávy proti filtrům obsaženým v tabulce filtru, je nutné přidružit tabulku filtru k koncovým bodům služby pomocí chování směrování.</span><span class="sxs-lookup"><span data-stu-id="5531e-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="5531e-118">Následující příklad znázorňuje přidružení "filterTable1" ke koncovému bodu služby.</span><span class="sxs-lookup"><span data-stu-id="5531e-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="5531e-119">Implementovat dynamickou konfiguraci</span><span class="sxs-lookup"><span data-stu-id="5531e-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="5531e-120">Dynamickou konfiguraci směrovací služby lze provést pouze v kódu vytvořením nového <xref:System.ServiceModel.Routing.RoutingConfiguration> a použitím <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> k nahrazení aktuální konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5531e-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="5531e-121">V tomto příkladu je směrovací služba samoobslužně hostována v rámci konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="5531e-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="5531e-122">Po spuštění aplikace můžete změnit konfiguraci směrování zadáním "normálního" nebo "zaokrouhlení" v okně konzoly ke konfiguraci cílového koncového bodu, na který jsou zprávy směrovány. regularCalc při zadání ' Regular ', jinak roundingCalc při zadání ' zaokrouhlení '.</span><span class="sxs-lookup"><span data-stu-id="5531e-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="5531e-123">Aby bylo možné podporovat směrovací službu, je nutné přidat následující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="5531e-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="5531e-124">Následující kód slouží k samoobslužnému hostování směrovací služby jako konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="5531e-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="5531e-125">Tím inicializujete směrovací službu pomocí konfigurace popsané v předchozím kroku, který je obsažen v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5531e-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="5531e-126">Smyčka while obsahuje kód používaný ke změně konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="5531e-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners           
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. <span data-ttu-id="5531e-127">Chcete-li dynamicky aktualizovat konfiguraci směrování, je nutné vytvořit novou konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="5531e-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="5531e-128">Tato akce musí obsahovat všechny koncové body, filtry a tabulky filtru, které jsou požadovány pro novou konfiguraci směrování, protože zcela nahradí stávající konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="5531e-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="5531e-129">Aby bylo možné použít novou konfiguraci směrování, je nutné vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> novou konfiguraci a předat ji.</span><span class="sxs-lookup"><span data-stu-id="5531e-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="5531e-130">Do dříve definované smyčky while přidejte následující kód, který umožní překonfigurovat službu na základě vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="5531e-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="5531e-131">Vzhledem k tomu, že metoda pro poskytování nového konfigurace RoutingConfiguration je obsažena v rozšíření služby RoutingExtension, mohou být nové objekty konfigurace RoutingConfiguration poskytnuty kdekoli v modelu rozšiřitelnosti WCF, který má nebo může získat odkaz na třídu ServiceHost nebo ServiceExtensions (například v jiném ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="5531e-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="5531e-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="5531e-132">Example</span></span>  
 <span data-ttu-id="5531e-133">Následuje úplný seznam konzolové aplikace použité v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="5531e-133">Following is a complete listing of the console application used in this example.</span></span>  
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {             
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners           
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="5531e-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="5531e-134">Example</span></span>  
 <span data-ttu-id="5531e-135">Následuje úplný seznam konfiguračního souboru použitého v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="5531e-135">Following is a complete listing of the configuration file used in this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5531e-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5531e-136">See also</span></span>

- [<span data-ttu-id="5531e-137">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="5531e-137">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
