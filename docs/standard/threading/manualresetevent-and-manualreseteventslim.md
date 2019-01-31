---
title: ManualResetEvent a ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49af405c7954f18e6f59264182a9a67a0be35d3d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279185"
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="17223-102">ManualResetEvent a ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="17223-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="17223-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída představuje, které musí obnovit ručně po to bylo signalizováno událost popisovač místní čekání.</span><span class="sxs-lookup"><span data-stu-id="17223-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="17223-104">Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="17223-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17223-105">Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce ruční obnovení události.</span><span class="sxs-lookup"><span data-stu-id="17223-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="17223-106">A <xref:System.Threading.ManualResetEvent> objekt zůstane až do signalizovaného jeho <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="17223-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="17223-107">Libovolný počet čekajících vláken, nebo vlákna, která čekání na událost po byl signalizován, mohou být vydány, zatímco signalizován stav objektu.</span><span class="sxs-lookup"><span data-stu-id="17223-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span>
  
 <span data-ttu-id="17223-108">V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> třídy pro zajištění lepšího výkonu při jsou velmi krátké doby čekání a události přes hranice procesu.</span><span class="sxs-lookup"><span data-stu-id="17223-108">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="17223-109"><xref:System.Threading.ManualResetEventSlim> používá zaneprázdněný, zprovozňování krátkou dobu, kdy čeká signálování události.</span><span class="sxs-lookup"><span data-stu-id="17223-109"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="17223-110">Po krátkou dobu čekání se může být zaneprázdnění mnohem levnější než čekání pomocí obslužné rutiny čekání.</span><span class="sxs-lookup"><span data-stu-id="17223-110">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="17223-111">Nicméně, pokud není stát signalizovanými události v rámci určité časové období <xref:System.Threading.ManualResetEventSlim> používat normální událost popisovač čekání.</span><span class="sxs-lookup"><span data-stu-id="17223-111">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17223-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17223-112">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>
- [<span data-ttu-id="17223-113">SpinWait</span><span class="sxs-lookup"><span data-stu-id="17223-113">SpinWait</span></span>](spinwait.md)
- [<span data-ttu-id="17223-114">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="17223-114">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)
- [<span data-ttu-id="17223-115">Eventwaithandle – CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="17223-115">EventWaitHandle, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [<span data-ttu-id="17223-116">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="17223-116">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="17223-117">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="17223-117">Threading</span></span>](index.md)
