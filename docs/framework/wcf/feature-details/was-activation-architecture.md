---
title: Architektura aktivace WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 9c1af21782b377a9fb01cbd05e4fe61f6a69f3ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134053"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="b3ad9-102">Architektura aktivace WAS</span><span class="sxs-lookup"><span data-stu-id="b3ad9-102">WAS Activation Architecture</span></span>
<span data-ttu-id="b3ad9-103">V tomto tématu najdete výčet a tento článek popisuje komponenty služby Aktivace procesu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="b3ad9-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="b3ad9-104">Aktivace součásti</span><span class="sxs-lookup"><span data-stu-id="b3ad9-104">Activation Components</span></span>  
 <span data-ttu-id="b3ad9-105">SE skládá z několika komponent architektury:</span><span class="sxs-lookup"><span data-stu-id="b3ad9-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="b3ad9-106">Naslouchací proces adaptéry.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-106">Listener adapters.</span></span> <span data-ttu-id="b3ad9-107">Služby Windows, které přijímají zprávy na konkrétních síťových protokolech a komunikovat s WAS můžete směrovat příchozí zprávy správné pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="b3ad9-108">BYLA.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-108">WAS.</span></span> <span data-ttu-id="b3ad9-109">Služba Windows, která spravuje vytváření a dobu života pracovních procesů.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="b3ad9-110">Obecný pracovní proces spustitelný soubor (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="b3ad9-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="b3ad9-111">Správce aplikací.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-111">Application manager.</span></span> <span data-ttu-id="b3ad9-112">Spravuje vytváření a dobu života aplikační domény, které zpracovávají hostování aplikací v rámci pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="b3ad9-113">Obslužné rutiny protokolu.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-113">Protocol handlers.</span></span> <span data-ttu-id="b3ad9-114">Konkrétní součásti, které běží v procesu pracovního procesu a správu komunikace mezi pracovního procesu a adaptéry jednotlivý naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="b3ad9-115">Existují dva typy obslužné rutiny protokolu: zpracování obslužné rutiny protokolu a obslužné rutiny protokolu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="b3ad9-116">Když služba WAS aktivuje instance procesu pracovního procesu, načítá obslužné rutiny protokolu procesu vyžaduje do pracovního procesu a používá správce aplikace pro vytvoření domény aplikace pro hostování aplikace.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="b3ad9-117">Doména aplikace načte kódu vaší aplikace, stejně jako obslužné rutiny protokolu domény aplikace, které používá síťové protokoly aplikace vyžadovat.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![Snímek obrazovky zobrazující architektura WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="b3ad9-119">Adaptéry naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="b3ad9-119">Listener Adapters</span></span>  
 <span data-ttu-id="b3ad9-120">Naslouchací proces adaptéry jsou jednotlivé služby Windows, které implementují logiku komunikace sítě používá pro příjem zpráv pomocí síťového protokolu se naslouchat.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="b3ad9-121">V následující tabulce jsou uvedeny adaptéry naslouchací proces pro protokoly Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b3ad9-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="b3ad9-122">Název služby adaptér naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="b3ad9-122">Listener adapter service name</span></span>|<span data-ttu-id="b3ad9-123">Protocol (Protokol)</span><span class="sxs-lookup"><span data-stu-id="b3ad9-123">Protocol</span></span>|<span data-ttu-id="b3ad9-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3ad9-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="b3ad9-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="b3ad9-125">W3SVC</span></span>|<span data-ttu-id="b3ad9-126">http</span><span class="sxs-lookup"><span data-stu-id="b3ad9-126">http</span></span>|<span data-ttu-id="b3ad9-127">Běžné komponenty, která poskytuje Aktivace protokolem HTTP pro internetové informační služby 7.0 nebo WCF.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="b3ad9-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="b3ad9-128">NetTcpActivator</span></span>|<span data-ttu-id="b3ad9-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="b3ad9-129">net.tcp</span></span>|<span data-ttu-id="b3ad9-130">Závisí na konfiguraci služby NetTcpPortSharing službě.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="b3ad9-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="b3ad9-131">NetPipeActivator</span></span>|<span data-ttu-id="b3ad9-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="b3ad9-132">net.pipe</span></span>||  
|<span data-ttu-id="b3ad9-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="b3ad9-133">NetMsmqActivator</span></span>|<span data-ttu-id="b3ad9-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="b3ad9-134">net.msmq</span></span>|<span data-ttu-id="b3ad9-135">Pro použití s aplikací na základě WCF služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="b3ad9-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="b3ad9-136">NetMsmqActivator</span></span>|<span data-ttu-id="b3ad9-137">msmq.formatname</span><span class="sxs-lookup"><span data-stu-id="b3ad9-137">msmq.formatname</span></span>|<span data-ttu-id="b3ad9-138">Poskytuje zpětné kompatibilitě se stávajícími aplikacemi služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="b3ad9-139">Adaptéry naslouchací proces pro konkrétní protokoly jsou registrovány během instalace v souboru applicationHost.config, jak je znázorněno v následujícím příkladu XML.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"   
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"   
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"   
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"   
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="b3ad9-140">Obslužné rutiny protokolu</span><span class="sxs-lookup"><span data-stu-id="b3ad9-140">Protocol Handlers</span></span>  
 <span data-ttu-id="b3ad9-141">Proces a obslužné rutiny protokolu domény aplikace pro konkrétní protokoly jsou registrované v souboru Web.config úrovni počítače.</span><span class="sxs-lookup"><span data-stu-id="b3ad9-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3ad9-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3ad9-142">See also</span></span>

- [<span data-ttu-id="b3ad9-143">Konfigurace WAS pro použití s WCF</span><span class="sxs-lookup"><span data-stu-id="b3ad9-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="b3ad9-144">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="b3ad9-144">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
