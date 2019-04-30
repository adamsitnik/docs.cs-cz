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
ms.openlocfilehash: cb7520518497b244be8be3751ca8a3063a02717a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788008"
---
# <a name="clr-etw-events"></a><span data-ttu-id="fd4c6-102">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="fd4c6-102">CLR ETW Events</span></span>
<span data-ttu-id="fd4c6-103">Témata v této části popisují trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="fd4c6-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="fd4c6-104">Každá událost má související klíčového slova a úrovně, které jsou popsány v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="fd4c6-105">Modul CLR má dva poskytovatelé pro události:</span><span class="sxs-lookup"><span data-stu-id="fd4c6-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="fd4c6-106">Zprostředkovatel běhového prostředí, které vyvolává události v závislosti na tom, které jsou povolené klíčová slova (kategorie události).</span><span class="sxs-lookup"><span data-stu-id="fd4c6-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="fd4c6-107">Identifikátor GUID zprostředkovatele CLR runtime je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="fd4c6-108">Zprostředkovatel doběhu, který má zvláštní účely.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="fd4c6-109">Identifikátor GUID zprostředkovatele doběhu modulu CLR je a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="fd4c6-110">Další informace o poskytovatelích najdete v tématu [CLR ETW – zprostředkovatelé](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="fd4c6-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd4c6-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fd4c6-111">In This Section</span></span>  
 [<span data-ttu-id="fd4c6-112">Události běhových informací</span><span class="sxs-lookup"><span data-stu-id="fd4c6-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="fd4c6-113">Zaznamenává informace o modulu runtime, včetně SKU, číslo verze, způsobem, ve kterém se aktivovala modul runtime, parametry příkazového řádku, který byl spuštěn s GUID (Pokud je k dispozici) a další relevantní informace.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="fd4c6-114">Událost výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="fd4c6-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="fd4c6-115">Zaznamenává informace o výjimkách, které jsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="fd4c6-116">Kolizní události</span><span class="sxs-lookup"><span data-stu-id="fd4c6-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="fd4c6-117">Zaznamenává informace o počtu kolizí zámků monitorování nebo nativní zámky, které používá modul runtime.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="fd4c6-118">Události fondu vláken</span><span class="sxs-lookup"><span data-stu-id="fd4c6-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="fd4c6-119">Zaznamenává informace o vlákně fondy pracovních procesů a fondy vláken vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="fd4c6-120">Události zavaděče</span><span class="sxs-lookup"><span data-stu-id="fd4c6-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="fd4c6-121">Zaznamenává informace o načítání a uvolňování domény aplikace, sestavení a modulů.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="fd4c6-122">Události metod</span><span class="sxs-lookup"><span data-stu-id="fd4c6-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="fd4c6-123">Zaznamenává informace o metodách CLR pro rozlišení symbolů.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="fd4c6-124">Události kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="fd4c6-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="fd4c6-125">Zaznamenává informace týkající se uvolňování paměti, které vám pomůžou Diagnostika a ladění.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="fd4c6-126">JIT – události trasování (CLR)</span><span class="sxs-lookup"><span data-stu-id="fd4c6-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="fd4c6-127">Zaznamenává informace o just-in-time (JIT) vkládání a volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="fd4c6-128">Události interoperability</span><span class="sxs-lookup"><span data-stu-id="fd4c6-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="fd4c6-129">Zaznamenává informace o Microsoft intermediate language (MSIL) zástupné procedury generování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="fd4c6-130">Události ARM</span><span class="sxs-lookup"><span data-stu-id="fd4c6-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="fd4c6-131">Zachycení podrobných diagnostických informací týkajících se stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="fd4c6-132">Události zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fd4c6-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="fd4c6-133">Zaznamenává informace týkající se silným názvem a ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="fd4c6-134">Událost zásobníku</span><span class="sxs-lookup"><span data-stu-id="fd4c6-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="fd4c6-135">Zaznamenává informace, které slouží ke generování trasování zásobníku, poté, co je vyvolána událost s jinými událostmi.</span><span class="sxs-lookup"><span data-stu-id="fd4c6-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4c6-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd4c6-136">See also</span></span>

- [<span data-ttu-id="fd4c6-137">Vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="fd4c6-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=179696)
- [<span data-ttu-id="fd4c6-138">Blog o Windows Performance</span><span class="sxs-lookup"><span data-stu-id="fd4c6-138">Windows Performance Blog</span></span>](https://go.microsoft.com/fwlink/?LinkId=179509)
- [<span data-ttu-id="fd4c6-139">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fd4c6-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)
- [<span data-ttu-id="fd4c6-140">Poskytovatelé Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="fd4c6-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)
- [<span data-ttu-id="fd4c6-141">Klíčová slova a úrovně Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="fd4c6-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="fd4c6-142">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="fd4c6-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
