---
title: Ladění, trasování a profilace
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 855a1329c9804e4b40d796c639bbe8768156dcc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754463"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="8d81b-102">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="8d81b-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="8d81b-103">Pro ladění aplikace rozhraní .NET Framework, musí být nakonfigurováno kompilátoru a modulu runtime prostředí umožňující ladicího programu pro připojení k aplikaci a k vytvoření symboly a řádku mapy, pokud je to možné, aplikace a její odpovídající Microsoft intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="8d81b-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="8d81b-104">Poté, co byl ladit spravované aplikace, můžete profilaci pro zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="8d81b-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="8d81b-105">Profilace vyhodnocuje a popisuje, řádky zdrojového kódu, které generují kód nejčastěji prováděnou a kolik času je trvá je spouštět.</span><span class="sxs-lookup"><span data-stu-id="8d81b-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="8d81b-106">Aplikace rozhraní .NET framework jsou jednoduše ladit pomocí sady Visual Studio, která zpracovává řadu podrobnosti o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8d81b-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="8d81b-107">Pokud není nainstalována aplikace Visual Studio, můžete prozkoumat a zlepšit výkon aplikací využívajících rozhraní .NET Framework pomocí tříd ladění v rozhraní .NET Framework <xref:System.Diagnostics> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8d81b-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="8d81b-108">Tento obor názvů obsahuje <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, a <xref:System.Diagnostics.TraceSource> třídy pro sledování spuštění toku a <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, a <xref:System.Diagnostics.PerformanceCounter> třídy pro profilování kódu.</span><span class="sxs-lookup"><span data-stu-id="8d81b-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d81b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8d81b-109">In This Section</span></span>  
 [<span data-ttu-id="8d81b-110">Povolení JIT – ladění Attach</span><span class="sxs-lookup"><span data-stu-id="8d81b-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="8d81b-111">Ukazuje, jak nakonfigurovat registr JIT připojit ladicí modul k aplikaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d81b-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="8d81b-112">Usnadnění ladění obrázku</span><span class="sxs-lookup"><span data-stu-id="8d81b-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="8d81b-113">Ukazuje, jak vypnout sledování JIT na a optimalizace pro usnadnění sestavení pro ladění.</span><span class="sxs-lookup"><span data-stu-id="8d81b-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="8d81b-114">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="8d81b-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="8d81b-115">Popisuje, jak monitorovat aplikace během jejího běhu a jak k instrumentaci a jak dobře zobrazit provádí, nebo jestli se něco nepovedlo.</span><span class="sxs-lookup"><span data-stu-id="8d81b-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="8d81b-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="8d81b-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="8d81b-117">Popisuje asistentů spravovaného ladění (mda), které ladíte pomůcek, které fungují ve spojení s modul CLR (CLR), která poskytují informace o stavu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8d81b-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="8d81b-118">Rozšíření ladění pomocí atributů zobrazení ladicího programu</span><span class="sxs-lookup"><span data-stu-id="8d81b-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="8d81b-119">Popisuje, jak může vývojář typu určit co, že typ bude vypadat podobně jako když se objeví v ladicí program.</span><span class="sxs-lookup"><span data-stu-id="8d81b-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="8d81b-120">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="8d81b-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="8d81b-121">Popisuje čítače, které můžete použít ke sledování výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d81b-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8d81b-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8d81b-122">Related Sections</span></span>  
 [<span data-ttu-id="8d81b-123">Ladění aplikací ASP.NET nebo ASP.NET Core v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d81b-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 <span data-ttu-id="8d81b-124">Obsahuje požadavky a pokyny, jak ladit aplikaci technologie ASP.NET při vývoji nebo po nasazení.</span><span class="sxs-lookup"><span data-stu-id="8d81b-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="8d81b-125">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="8d81b-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="8d81b-126">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="8d81b-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
