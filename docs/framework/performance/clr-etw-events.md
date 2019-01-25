---
title: Události ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d64ee6942d9397ceb45b812ef3c26179fac9b2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540296"
---
# <a name="clr-etw-events"></a><span data-ttu-id="48a96-102">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="48a96-102">CLR ETW Events</span></span>
<span data-ttu-id="48a96-103">Témata v této části popisují trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="48a96-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="48a96-104">Každá událost má související klíčového slova a úrovně, které jsou popsány v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="48a96-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="48a96-105">Modul CLR má dva poskytovatelé pro události:</span><span class="sxs-lookup"><span data-stu-id="48a96-105">The CLR has two providers for the events:</span></span>  
  
-   <span data-ttu-id="48a96-106">Zprostředkovatel běhového prostředí, které vyvolává události v závislosti na tom, které jsou povolené klíčová slova (kategorie události).</span><span class="sxs-lookup"><span data-stu-id="48a96-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="48a96-107">Identifikátor GUID zprostředkovatele CLR runtime je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="48a96-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
-   <span data-ttu-id="48a96-108">Zprostředkovatel doběhu, který má zvláštní účely.</span><span class="sxs-lookup"><span data-stu-id="48a96-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="48a96-109">Identifikátor GUID zprostředkovatele doběhu modulu CLR je a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="48a96-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="48a96-110">Další informace o poskytovatelích najdete v tématu [CLR ETW – zprostředkovatelé](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="48a96-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48a96-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="48a96-111">In This Section</span></span>  
 [<span data-ttu-id="48a96-112">Události běhových informací</span><span class="sxs-lookup"><span data-stu-id="48a96-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="48a96-113">Zaznamenává informace o modulu runtime, včetně SKU, číslo verze, způsobem, ve kterém se aktivovala modul runtime, parametry příkazového řádku, který byl spuštěn s GUID (Pokud je k dispozici) a další relevantní informace.</span><span class="sxs-lookup"><span data-stu-id="48a96-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="48a96-114">Událost výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="48a96-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="48a96-115">Zaznamenává informace o výjimkách, které jsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="48a96-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="48a96-116">Kolizní události</span><span class="sxs-lookup"><span data-stu-id="48a96-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="48a96-117">Zaznamenává informace o počtu kolizí zámků monitorování nebo nativní zámky, které používá modul runtime.</span><span class="sxs-lookup"><span data-stu-id="48a96-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="48a96-118">Události fondu vláken</span><span class="sxs-lookup"><span data-stu-id="48a96-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="48a96-119">Zaznamenává informace o vlákně fondy pracovních procesů a fondy vláken vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="48a96-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="48a96-120">Události zavaděče</span><span class="sxs-lookup"><span data-stu-id="48a96-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="48a96-121">Zaznamenává informace o načítání a uvolňování domény aplikace, sestavení a modulů.</span><span class="sxs-lookup"><span data-stu-id="48a96-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="48a96-122">Události metod</span><span class="sxs-lookup"><span data-stu-id="48a96-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="48a96-123">Zaznamenává informace o metodách CLR pro rozlišení symbolů.</span><span class="sxs-lookup"><span data-stu-id="48a96-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="48a96-124">Události kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="48a96-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="48a96-125">Zaznamenává informace týkající se uvolňování paměti, které vám pomůžou Diagnostika a ladění.</span><span class="sxs-lookup"><span data-stu-id="48a96-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="48a96-126">JIT – události trasování (CLR)</span><span class="sxs-lookup"><span data-stu-id="48a96-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="48a96-127">Zaznamenává informace o just-in-time (JIT) vkládání a volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="48a96-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="48a96-128">Události interoperability</span><span class="sxs-lookup"><span data-stu-id="48a96-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="48a96-129">Zaznamenává informace o Microsoft intermediate language (MSIL) zástupné procedury generování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="48a96-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="48a96-130">Události ARM</span><span class="sxs-lookup"><span data-stu-id="48a96-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="48a96-131">Zachycení podrobných diagnostických informací týkajících se stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="48a96-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="48a96-132">Události zabezpečení</span><span class="sxs-lookup"><span data-stu-id="48a96-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="48a96-133">Zaznamenává informace týkající se silným názvem a ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="48a96-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="48a96-134">Událost zásobníku</span><span class="sxs-lookup"><span data-stu-id="48a96-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="48a96-135">Zaznamenává informace, které slouží ke generování trasování zásobníku, poté, co je vyvolána událost s jinými událostmi.</span><span class="sxs-lookup"><span data-stu-id="48a96-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a96-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48a96-136">See also</span></span>
- [<span data-ttu-id="48a96-137">Vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="48a96-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=179696)
- [<span data-ttu-id="48a96-138">Blog o Windows Performance</span><span class="sxs-lookup"><span data-stu-id="48a96-138">Windows Performance Blog</span></span>](https://go.microsoft.com/fwlink/?LinkId=179509)
- [<span data-ttu-id="48a96-139">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48a96-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)
- [<span data-ttu-id="48a96-140">Poskytovatelé Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="48a96-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)
- [<span data-ttu-id="48a96-141">Klíčová slova a úrovně Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="48a96-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="48a96-142">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="48a96-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
