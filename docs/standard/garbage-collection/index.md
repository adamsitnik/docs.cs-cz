---
title: Kolekce paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f61b63f78ea3c6131d4d1ab4e421be25149035b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931518"
---
# <a name="garbage-collection"></a><span data-ttu-id="ec1a7-102">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="ec1a7-102">Garbage Collection</span></span>
<span data-ttu-id="ec1a7-103">. NET. systém uvolňování paměti spravuje přidělování a uvolňování paměti pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="ec1a7-104">Při každém vytvoření nového objektu modul CLR přidělí objektu paměť ze spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="ec1a7-105">Dokud je ve spravované haldě k dispozici adresní prostor, modul runtime bude pokračovat v přidělování prostoru pro nové objekty.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="ec1a7-106">Paměť však není neomezená.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-106">However, memory is not infinite.</span></span> <span data-ttu-id="ec1a7-107">Z důvodu získání paměti musí nakonec systém uvolňování paměti provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="ec1a7-108">Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení uvolnění paměti na základě způsobu přidělování paměti.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="ec1a7-109">Při uvolňování paměti systém ověřuje, zda objekty ve spravované haldě již nejsou používány aplikací, a provede nezbytné úkony k opětovnému získání paměti.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="ec1a7-110">Související témata</span><span class="sxs-lookup"><span data-stu-id="ec1a7-110">Related Topics</span></span>  
  
|<span data-ttu-id="ec1a7-111">Název</span><span class="sxs-lookup"><span data-stu-id="ec1a7-111">Title</span></span>|<span data-ttu-id="ec1a7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ec1a7-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ec1a7-113">Základy kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="ec1a7-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="ec1a7-114">Popisuje způsob, jakým funguje systém uvolňování paměti, jakým způsobem jsou objekty přidělovány na spravované haldě, a další základní pojmy.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="ec1a7-115">Kolekce paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="ec1a7-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="ec1a7-116">Popisuje kontroly výkonu, které slouží k diagnostice problémů uvolňování paměti a výkonu.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="ec1a7-117">Vyvolané kolekce</span><span class="sxs-lookup"><span data-stu-id="ec1a7-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="ec1a7-118">Popisuje způsob aktivace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="ec1a7-119">Latentní režimy</span><span class="sxs-lookup"><span data-stu-id="ec1a7-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="ec1a7-120">Popisuje režimy, které určují parametry systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="ec1a7-121">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="ec1a7-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="ec1a7-122">Popisuje způsob optimalizace uvolňování paměti na serverech, které jsou sdíleny několika malými weby.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="ec1a7-123">Oznámení pro kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="ec1a7-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="ec1a7-124">Popisuje, jakým způsobem lze zjistit, kdy se blíží termín úplného uvolňování paměti a kdy bude uvolňování dokončeno.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="ec1a7-125">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ec1a7-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="ec1a7-126">Popisuje sledování využití procesoru a paměti doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="ec1a7-127">Slabé odkazy</span><span class="sxs-lookup"><span data-stu-id="ec1a7-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="ec1a7-128">Popisuje funkce, které systému uvolňování paměti umožňují získat paměť objektu a zároveň podporují přístup aplikace k danému objektu.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="ec1a7-129">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ec1a7-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="ec1a7-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec1a7-130">See also</span></span>

- [<span data-ttu-id="ec1a7-131">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="ec1a7-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
