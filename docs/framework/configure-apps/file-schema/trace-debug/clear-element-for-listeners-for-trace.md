---
title: <clear> – element pro element <listeners> pro element <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: b199f24a2c1e1c8154c0ec22bef6367e5ba0ec26
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262602"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="014e1-102">\<Vymazat > – Element pro \<naslouchacích procesů > pro \<trasování ></span><span class="sxs-lookup"><span data-stu-id="014e1-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="014e1-103">Vymaže `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="014e1-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="014e1-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="014e1-104">\<configuration></span></span>  
<span data-ttu-id="014e1-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="014e1-105">\<system.diagnostics></span></span>  
<span data-ttu-id="014e1-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="014e1-106">\<trace></span></span>  
<span data-ttu-id="014e1-107">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="014e1-107">\<listeners></span></span>  
<span data-ttu-id="014e1-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="014e1-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="014e1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="014e1-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="014e1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="014e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="014e1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="014e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="014e1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="014e1-112">Attributes</span></span>  
 <span data-ttu-id="014e1-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="014e1-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="014e1-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="014e1-114">Child Elements</span></span>  
 <span data-ttu-id="014e1-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="014e1-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="014e1-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="014e1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="014e1-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="014e1-117">Element</span></span>|<span data-ttu-id="014e1-118">Popis</span><span class="sxs-lookup"><span data-stu-id="014e1-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="014e1-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="014e1-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="014e1-120">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="014e1-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="014e1-121">Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="014e1-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="014e1-122">Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="014e1-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="014e1-123">Posluchači přímý výstup trasování příslušný cíli.</span><span class="sxs-lookup"><span data-stu-id="014e1-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="014e1-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="014e1-124">Remarks</span></span>  
 <span data-ttu-id="014e1-125">`<clear>` Element odebere všechny moduly pro naslouchání z `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="014e1-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="014e1-126">Můžete použít `<clear>` prvek před použitím `<add>` element je potřeba mít jistotu, nejsou žádné aktivní naslouchací procesy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="014e1-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="014e1-127">Můžete vymazat `Listeners` kolekce programově zavoláním <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metodu <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnosti (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="014e1-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="014e1-128">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="014e1-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="014e1-129">`<clear>` Odebere element <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce, změna chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="014e1-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="014e1-130">Volání `Assert` nebo `Fail` metoda je normálně ve výsledku zobrazení okna se zprávou.</span><span class="sxs-lookup"><span data-stu-id="014e1-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="014e1-131">Však se nezobrazí okno se zprávou, pokud <xref:System.Diagnostics.DefaultTraceListener> se nepoužívá `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="014e1-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="014e1-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="014e1-132">Example</span></span>  
 <span data-ttu-id="014e1-133">Následující příklad ukazuje způsob použití `<clear>` prvek před použitím `<add>` prvek a přidat naslouchací proces `console` k `Listeners` kolekce pro trasovacího.</span><span class="sxs-lookup"><span data-stu-id="014e1-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="014e1-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="014e1-134">See also</span></span>
- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="014e1-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="014e1-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="014e1-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="014e1-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="014e1-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="014e1-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
