---
title: Asynchronní programování pomocí delegátů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41c9793900c3e7accd5463a19de10d1cb81afd59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870120"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="c8485-102">Asynchronní programování pomocí delegátů</span><span class="sxs-lookup"><span data-stu-id="c8485-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="c8485-103">Delegáty umožňují volání v asynchronním režimu synchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c8485-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="c8485-104">Při volání delegáta synchronně, `Invoke` metoda volá metodu cíl přímo u aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="c8485-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="c8485-105">Pokud `BeginInvoke` metoda je volána, common language runtime (CLR) zařadí do fronty požadavek a okamžitě vrací volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c8485-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="c8485-106">Cílové metody je volána asynchronně na vlákně z fondu podprocesů.</span><span class="sxs-lookup"><span data-stu-id="c8485-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="c8485-107">Původní podproces, který danou žádost odeslal, je zdarma má pokračovat provedením souběžně s cílovou metodu.</span><span class="sxs-lookup"><span data-stu-id="c8485-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="c8485-108">Pokud byl zadán metody zpětného volání při volání `BeginInvoke` metody, metody zpětného volání je volána, když skončí cílové metody.</span><span class="sxs-lookup"><span data-stu-id="c8485-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="c8485-109">V metodě zpětného volání `EndInvoke` metoda získá návratovou hodnotu a vstup/výstup nebo jen pro výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="c8485-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="c8485-110">Pokud žádná metoda zpětného volání je zadán při volání metody `BeginInvoke`, `EndInvoke` lze volat z vlákna, která se nazývá `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="c8485-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8485-111">Kompilátory by měly vydávat třídy delegáta s `Invoke`, `BeginInvoke`, a `EndInvoke` metod pomocí delegáta specifikovaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c8485-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="c8485-112">`BeginInvoke` a `EndInvoke` metody by měly být doplněny jako nativní.</span><span class="sxs-lookup"><span data-stu-id="c8485-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="c8485-113">Protože tyto metody jsou označeny jako nativní, modul CLR automaticky poskytuje implementaci v okamžiku načtení třídy.</span><span class="sxs-lookup"><span data-stu-id="c8485-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="c8485-114">Zavaděč zajistí, že nejsou přepsána.</span><span class="sxs-lookup"><span data-stu-id="c8485-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8485-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c8485-115">In This Section</span></span>  
 [<span data-ttu-id="c8485-116">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="c8485-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="c8485-117">Tento článek popisuje použití delegátů pro asynchronní volání běžné metody a poskytuje příklady jednoduchého kódu, které ukazují čtyři způsoby čekání na asynchronní volání k vrácení.</span><span class="sxs-lookup"><span data-stu-id="c8485-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8485-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c8485-118">Related Sections</span></span>  
 [<span data-ttu-id="c8485-119">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="c8485-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="c8485-120">Popisuje asynchronní programování s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8485-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8485-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8485-121">See also</span></span>

- <xref:System.Delegate>
