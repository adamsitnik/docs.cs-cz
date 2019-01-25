---
title: '&lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: c11fd38e7c40f740d4c1c36ab87c44744ed0daab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627980"
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="7173c-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="7173c-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="7173c-103">Představuje konfigurační oddíl pro definování zálohování seznamu, který uvádí sady koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7173c-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="7173c-104">Pokud je první koncový bod v seznamu dolů, směrovací služba se automaticky převzetí služby při selhání k dalším objektem v seznamu.</span><span class="sxs-lookup"><span data-stu-id="7173c-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="7173c-105">To umožňuje rychlé přidání spolehlivosti do aplikace bez nutnosti představuje klientskou aplikaci, jak zpracovávat složité vzory nebo všechny služby, ve které jsou nasazené.</span><span class="sxs-lookup"><span data-stu-id="7173c-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="7173c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7173c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7173c-107">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="7173c-107">\<routing></span></span>  
<span data-ttu-id="7173c-108">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="7173c-108">\<backupLists></span></span>  
<span data-ttu-id="7173c-109">\<backupList></span><span class="sxs-lookup"><span data-stu-id="7173c-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7173c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7173c-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7173c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7173c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7173c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7173c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7173c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="7173c-113">Attributes</span></span>  
  
|<span data-ttu-id="7173c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="7173c-114">Attribute</span></span>|<span data-ttu-id="7173c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7173c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7173c-116">name</span><span class="sxs-lookup"><span data-stu-id="7173c-116">name</span></span>|<span data-ttu-id="7173c-117">Řetězec určující název používaný k identifikaci tohoto seznamu koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="7173c-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7173c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7173c-118">Child Elements</span></span>  
  
|<span data-ttu-id="7173c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="7173c-119">Element</span></span>|<span data-ttu-id="7173c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7173c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7173c-121">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="7173c-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="7173c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7173c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7173c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="7173c-123">Element</span></span>|<span data-ttu-id="7173c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7173c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7173c-125">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="7173c-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7173c-126">Seznamu zálohy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="7173c-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7173c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7173c-127">Remarks</span></span>  
 <span data-ttu-id="7173c-128">Tato část obsahuje řazená kolekce koncových bodů, které zprávy budou předány v případě výjimky komunikace při odesílání na primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7173c-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="7173c-129">Pokud uvedený na seznamu odeslat na primární koncový bod `endpointName` atribut [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) selže s výjimkou komunikace, směrovací služba se pokusí o odeslání zprávy na první koncový bod v tomto konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="7173c-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="7173c-130">Pokud to je také neúspěšná, s výjimkou komunikace, směrovací služba se pokusí odeslat zprávu na další zprávu obsažené v této části, až do pokusu o odeslání úspěšná, vrátí selhání než výjimky komunikace nebo všechny koncové body v kolekce mají vrátila chybu.</span><span class="sxs-lookup"><span data-stu-id="7173c-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="7173c-131">V následujícím příkladu Pokud odeslat na primární koncový bod s názvem "Cíl" vrátí výjimky komunikace, služba se pokusí odeslání zprávy do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="7173c-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="7173c-132">Pokud tento pokus také vrátí hodnotu výjimky komunikace, směrovací služba se pokusí odeslat zprávu do další koncový bod v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7173c-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="7173c-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7173c-133">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
