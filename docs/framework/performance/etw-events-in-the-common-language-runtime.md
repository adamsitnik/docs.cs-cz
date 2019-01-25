---
title: Události Trasování událostí pro Windows v CLR (Common Language Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 284b7f814f8a9355220f0da59e8fce7d79345609
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620237"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="b339a-102">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="b339a-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="b339a-103">Modul CLR (CLR) poskytuje užitečné události trasování pro Windows (ETW) diagnostické informace prostřednictvím širokou škálu ladění a profilování události.</span><span class="sxs-lookup"><span data-stu-id="b339a-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="b339a-104">Událostí CLR ETW pomocí systému Windows trasování událostí pro Windows trasování pro rozšíření existující profilování a ladění poskytované modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b339a-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="b339a-105">Další informace o trasování událostí pro Windows je k dispozici v článku [vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows](https://go.microsoft.com/fwlink/?LinkID=161142) na webové stránce MSDN.</span><span class="sxs-lookup"><span data-stu-id="b339a-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="b339a-106">Informace o nástroji Xperf naleznete v položce [Windows Performance Toolkit – Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) NTDebugging blogu.</span><span class="sxs-lookup"><span data-stu-id="b339a-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="b339a-107">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Nebo později se vyžaduje pro všechny události je popsáno v případě témata.</span><span class="sxs-lookup"><span data-stu-id="b339a-107">The [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="b339a-108">Je minimální podporované klientské operační systém Windows Vista a Windows Server 2008 je minimální podporované serverem.</span><span class="sxs-lookup"><span data-stu-id="b339a-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b339a-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b339a-109">In This Section</span></span>  
 [<span data-ttu-id="b339a-110">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b339a-110">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 <span data-ttu-id="b339a-111">Popisuje nástroje a příkazy pro zachytávání a zobrazování událostí trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="b339a-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="b339a-112">Poskytovatelé Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="b339a-112">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 <span data-ttu-id="b339a-113">Poskytuje informace o modulu runtime a zprostředkovatele doběhu a jak je použít pro shromažďování dat trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="b339a-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="b339a-114">Klíčová slova a úrovně Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="b339a-114">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="b339a-115">Popisuje klíčová slova pro modul Runtime a doběhu zprostředkovatelů, které umožňují filtrovat události podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="b339a-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="b339a-116">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="b339a-116">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)  
 <span data-ttu-id="b339a-117">Poskytuje podrobné informace o CLR ETW – události, klíčová slova, úrovní a data události.</span><span class="sxs-lookup"><span data-stu-id="b339a-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b339a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b339a-118">See also</span></span>
- [<span data-ttu-id="b339a-119">Trasování událostí pro Windows – události v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b339a-119">ETW Events in the .NET Framework</span></span>](../../../docs/framework/performance/etw-events.md)
