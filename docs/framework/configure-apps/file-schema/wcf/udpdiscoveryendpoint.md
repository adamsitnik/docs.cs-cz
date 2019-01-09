---
title: '&lt;UdpDiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 6508f73de7920a339e40284c86b0d1d649e7eabe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145429"
---
# <a name="ltudpdiscoveryendpointgt"></a><span data-ttu-id="1b9f2-102">&lt;UdpDiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="1b9f2-102">&lt;udpDiscoveryEndpoint&gt;</span></span>
<span data-ttu-id="1b9f2-103">Tento prvek konfigurace definuje standardní koncový bod, který je předkonfigurován pro operace zjišťování přes UDP vazby vícesměrného vysílání.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-103">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="1b9f2-104">Tento koncový bod má pevnou kontrakt a podporuje dvě verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-104">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="1b9f2-105">Kromě toho má pevnou vazbou UDP a adresu výchozí podle specifikace WS-Discovery (WS-Discovery dubna 2005 nebo V1.1 WS-Discovery).</span><span class="sxs-lookup"><span data-stu-id="1b9f2-105">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="1b9f2-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1b9f2-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="1b9f2-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1b9f2-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9f2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b9f2-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b9f2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1b9f2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1b9f2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b9f2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1b9f2-111">Attributes</span></span>  
  
|<span data-ttu-id="1b9f2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1b9f2-112">Attribute</span></span>|<span data-ttu-id="1b9f2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1b9f2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b9f2-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="1b9f2-114">discoveryMode</span></span>|<span data-ttu-id="1b9f2-115">Řetězec, který určuje režim protokolu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="1b9f2-116">Platné hodnoty jsou "Ad hoc" a "Spravovaný".</span><span class="sxs-lookup"><span data-stu-id="1b9f2-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="1b9f2-117">Ve spravovaném režimu protokol spoléhá na Proxy zjišťování, která slouží jako úložiště zjistitelné služby.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="1b9f2-118">Režimu ad hoc vyžaduje protokol UDP použití vícesměrového vysílání mechanismus pro vyhledání dostupných služeb.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="1b9f2-119">Tato hodnota je typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-119">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="1b9f2-120">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="1b9f2-120">discoveryVersion</span></span>|<span data-ttu-id="1b9f2-121">Řetězec, který určuje jeden ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="1b9f2-122">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="1b9f2-123">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="1b9f2-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="1b9f2-124">maxResponseDelay</span></span>|<span data-ttu-id="1b9f2-125">Časový interval hodnotu, která určuje maximální hodnotu zpoždění protokolu zjišťování bude čekat před odesláním některé zprávy, jako je například sběru dat nebo vyřešit shoda.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="1b9f2-126">Pokud se všechny ProbeMatches odesílají ve stejnou dobu, může docházet k síti storm.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="1b9f2-127">Chcete-li tomu zabránit, ProbeMatches odesílají pomocí náhodného zpoždění mezi každou ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="1b9f2-128">Náhodné zpoždění je v rozsahu od 0 do hodnoty nastavené v tomto atributu.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="1b9f2-129">Pokud tento atribut je nastaven na hodnotu 0, jsou odesílány zprávy ProbeMatches v těsné smyčce bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="1b9f2-130">V opačném případě případě odesílají zprávy ProbeMatches s některé náhodné zpoždění nepřekročí celkový čas potřebný k odeslání všech zpráv ProbeMatches maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="1b9f2-131">Tato hodnota platí pouze pro služby, se používají klienti.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-131">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="1b9f2-132">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="1b9f2-132">multicastAddress</span></span>|<span data-ttu-id="1b9f2-133">Identifikátor Uri určující adresu vícesměrového vysílání pro odesílání a přijímání zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-133">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="1b9f2-134">Výchozí hodnota je jako vyhovující specifikace protokolu adresu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-134">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="1b9f2-135">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-135">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1b9f2-136">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-136">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b9f2-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1b9f2-137">Child Elements</span></span>  
  
|<span data-ttu-id="1b9f2-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b9f2-138">Element</span></span>|<span data-ttu-id="1b9f2-139">Popis</span><span class="sxs-lookup"><span data-stu-id="1b9f2-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b9f2-140">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="1b9f2-140">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="1b9f2-141">Kolekce nastavení, která vám umožní nakonfigurovat přenos UDP pro koncový bod protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-141">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b9f2-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1b9f2-142">Parent Elements</span></span>  
  
|<span data-ttu-id="1b9f2-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b9f2-143">Element</span></span>|<span data-ttu-id="1b9f2-144">Popis</span><span class="sxs-lookup"><span data-stu-id="1b9f2-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b9f2-145">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1b9f2-145">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1b9f2-146">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-146">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1b9f2-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b9f2-147">Example</span></span>  
 <span data-ttu-id="1b9f2-148">Následující příklad ukazuje služby přes UDP naslouchání pro zjišťování zprávy vícesměrového vysílání přenosu.</span><span class="sxs-lookup"><span data-stu-id="1b9f2-148">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="1b9f2-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b9f2-149">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
