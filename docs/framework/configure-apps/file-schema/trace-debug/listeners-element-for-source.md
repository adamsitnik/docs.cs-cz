---
title: '&lt;naslouchací procesy&gt; – Element pro &lt;zdroje&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 949b6c7272b39900698b618760f5e5bad11ccc3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670638"
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="544c7-102">&lt;naslouchací procesy&gt; – Element pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="544c7-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="544c7-103">Přidá nebo odebere naslouchacích procesů v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekce <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="544c7-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="544c7-104">Naslouchací proces bude směrovat výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="544c7-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="544c7-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="544c7-105">\<configuration></span></span>  
<span data-ttu-id="544c7-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="544c7-106">\<system.diagnostics></span></span>  
<span data-ttu-id="544c7-107">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="544c7-107">\<sources></span></span>  
<span data-ttu-id="544c7-108">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="544c7-108">\<source></span></span>  
<span data-ttu-id="544c7-109">\<naslouchací procesy > – Element</span><span class="sxs-lookup"><span data-stu-id="544c7-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544c7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="544c7-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="544c7-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="544c7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="544c7-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="544c7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="544c7-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="544c7-113">Attributes</span></span>  
 <span data-ttu-id="544c7-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="544c7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="544c7-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="544c7-115">Child Elements</span></span>  
  
|<span data-ttu-id="544c7-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="544c7-116">Element</span></span>|<span data-ttu-id="544c7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="544c7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="544c7-118">\<add></span><span class="sxs-lookup"><span data-stu-id="544c7-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="544c7-119">Přidá naslouchací proces pro `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="544c7-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="544c7-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="544c7-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="544c7-121">Odebere z naslouchacího procesu `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="544c7-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="544c7-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="544c7-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="544c7-123">Vymaže `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="544c7-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="544c7-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="544c7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="544c7-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="544c7-125">Element</span></span>|<span data-ttu-id="544c7-126">Popis</span><span class="sxs-lookup"><span data-stu-id="544c7-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="544c7-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="544c7-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="544c7-128">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="544c7-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="544c7-129">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="544c7-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="544c7-130">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="544c7-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="544c7-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="544c7-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="544c7-132">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="544c7-132">Configuration File</span></span>  
 <span data-ttu-id="544c7-133">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="544c7-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="544c7-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="544c7-134">Example</span></span>  
 <span data-ttu-id="544c7-135">Následující příklad ukazuje způsob použití `<listeners>` prvku pro přidání naslouchacího procesu trasování konzoly pro `mySource` zdroje dat a Vymazat výchozí naslouchací služby stopy.</span><span class="sxs-lookup"><span data-stu-id="544c7-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="544c7-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="544c7-136">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="544c7-137">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="544c7-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="544c7-138">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="544c7-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
