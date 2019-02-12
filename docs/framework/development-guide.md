---
title: Průvodce vývojem s použitím rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 894895331c2444a8e52a09e3de9d5a47daa87e5d
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092953"
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="3ad6b-102">Průvodce vývojem s použitím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ad6b-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="3ad6b-103">Tato část vysvětluje, jak vytvořit, konfigurovat, ladění, zabezpečení a nasazení aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="3ad6b-104">V části také obsahuje informace o oblastech technologií, jako jsou dynamické programování, interoperabilita, rozšiřitelnost, správa paměti a dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ad6b-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3ad6b-105">In This Section</span></span>  
 [<span data-ttu-id="3ad6b-106">Základy vytváření aplikací</span><span class="sxs-lookup"><span data-stu-id="3ad6b-106">Application Essentials</span></span>](../../docs/standard/application-essentials.md)  
 <span data-ttu-id="3ad6b-107">Poskytuje informace o základní aplikaci vývojářských úlohách, například programování s doménami aplikací a sestaveními, pomocí atributů, formátování a analýzu základních typů, pomocí kolekcí, zpracování událostí a výjimek, použití souborů a datových proudů a použití Obecné typy.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="3ad6b-108">Data a modelování</span><span class="sxs-lookup"><span data-stu-id="3ad6b-108">Data and Modeling</span></span>](../../docs/framework/data/index.md)  
 <span data-ttu-id="3ad6b-109">Poskytuje informace o tom, jak získat přístup k datům pomocí technologie ADO.NET, Language Integrated Query (LINQ), služeb WCF Data Services a XML.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="3ad6b-110">Klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="3ad6b-110">Client Applications</span></span>](../../docs/framework/develop-client-apps.md)  
 <span data-ttu-id="3ad6b-111">Vysvětluje, jak vytvářet aplikace založené na Windows s použitím Windows Presentation Foundation (WPF) nebo formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="3ad6b-112">Webové aplikace s ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3ad6b-112">Web Applications with ASP.NET</span></span>](../../docs/framework/develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="3ad6b-113">Obsahuje odkazy na informace o používání technologie ASP.NET vytvářet podnikové webové aplikace s minimálním kódováním.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="3ad6b-114">Aplikace orientované na služby s použitím technologie WCF</span><span class="sxs-lookup"><span data-stu-id="3ad6b-114">Service-Oriented Applications with WCF</span></span>](../../docs/framework/wcf/index.md)  
 <span data-ttu-id="3ad6b-115">Popisuje způsob použití služby Windows Communication Foundation (WCF) k vytváření aplikací orientovaných na služby, které jsou bezpečné a spolehlivé.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="3ad6b-116">[Vytváření pracovních postupů s Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="3ad6b-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="3ad6b-117">Poskytuje informace o programovací model, ukázek a nástrojů pro používání Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="3ad6b-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="3ad6b-118">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="3ad6b-118">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
 <span data-ttu-id="3ad6b-119">Vysvětluje, jak pomocí sady Visual Studio a rozhraní .NET Framework k vytvoření aplikace, který je nainstalován jako služby a spuštění, zastavení a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="3ad6b-120">Paralelní zpracování, souběžnost a asynchronní programování v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3ad6b-120">Parallel Processing, Concurrency, and Async Programming in .NET</span></span>](../../docs/standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="3ad6b-121">Poskytuje informace o správě vláken, paralelním programování a návrhových vzorech asynchronního programování.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="3ad6b-122">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ad6b-122">Network Programming in the .NET Framework</span></span>](../../docs/framework/network-programming/index.md)  
 <span data-ttu-id="3ad6b-123">Popisuje vícevrstvou, rozšiřitelnou a spravovatelnou implementaci internetových služeb, které můžete rychle a snadno integrovat do vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="3ad6b-124">[Konfigurace aplikací .NET Framework](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="3ad6b-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="3ad6b-125">Vysvětluje, jak můžete použít konfigurační soubory pro změnu nastavení bez nutnosti znovu kompilovat aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="3ad6b-126">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="3ad6b-126">Compiling Apps with .NET Native</span></span>](../../docs/framework/net-native/index.md)  
 <span data-ttu-id="3ad6b-127">Vysvětluje, jak můžete použít [!INCLUDE[net_native](../../includes/net-native-md.md)] technologie předkompilace pro sestavování a nasazování aplikací pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-127">Explains how you can use the [!INCLUDE[net_native](../../includes/net-native-md.md)] precompilation technology to build and deploy Windows Store apps.</span></span> [!INCLUDE[net_native](../../includes/net-native-md.md)] <span data-ttu-id="3ad6b-128">zkompiluje aplikace napsané ve spravovaném kódu (C#), který cílit na rozhraní .NET Framework do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-128">compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="3ad6b-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ad6b-129">Security</span></span>](../../docs/standard/security/index.md)  
 <span data-ttu-id="3ad6b-130">Poskytuje informace o třídách a službách v rozhraní .NET Framework, které usnadňují vývoj zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="3ad6b-131">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="3ad6b-131">Debugging, Tracing, and Profiling</span></span>](../../docs/framework/debug-trace-profile/index.md)  
 <span data-ttu-id="3ad6b-132">Vysvětluje, jak testovat, optimalizovat a Profilovat aplikace rozhraní .NET Framework a prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="3ad6b-133">Tato část obsahuje informace pro správce i pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="3ad6b-134">Vývoj pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="3ad6b-134">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="3ad6b-135">Poskytuje informace o použití rozhraní .NET Framework pro tvorbu sestavení, které mohou být sdíleny napříč více platforem a více zařízení, jako jsou telefony, počítače a web.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="3ad6b-136">Nasazení</span><span class="sxs-lookup"><span data-stu-id="3ad6b-136">Deployment</span></span>](../../docs/framework/deployment/index.md)  
 <span data-ttu-id="3ad6b-137">Vysvětluje, jak zabalit a distribuovat aplikaci rozhraní .NET Framework a obsahuje pokyny pro nasazení pro vývojáře a správce.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="3ad6b-138">Výkon</span><span class="sxs-lookup"><span data-stu-id="3ad6b-138">Performance</span></span>](../../docs/framework/performance/index.md)  
 <span data-ttu-id="3ad6b-139">Poskytuje informace o ukládání do mezipaměti, opožděné inicializaci, spolehlivosti a trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
 
## <a name="reference"></a><span data-ttu-id="3ad6b-140">Odkaz</span><span class="sxs-lookup"><span data-stu-id="3ad6b-140">Reference</span></span>  
 [<span data-ttu-id="3ad6b-141">Knihovna tříd rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="3ad6b-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="3ad6b-142">Poskytuje syntaxi, příklady kódu a informace o využití pro každou třídu, která je součástí [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-142">Supplies syntax, code examples, and usage information for each class that is contained in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3ad6b-143">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3ad6b-143">Related Sections</span></span>  
 [<span data-ttu-id="3ad6b-144">Začínáme</span><span class="sxs-lookup"><span data-stu-id="3ad6b-144">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
 <span data-ttu-id="3ad6b-145">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="3ad6b-146">Co je nového</span><span class="sxs-lookup"><span data-stu-id="3ad6b-146">What's New</span></span>](../../docs/framework/whats-new/index.md)  
 <span data-ttu-id="3ad6b-147">Popisuje hlavní nové funkce a změny v nejnovější verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="3ad6b-148">Obsahuje seznam nových a zastaralých typů a členů a poskytuje návod pro migraci aplikací z předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="3ad6b-149">Nástroje</span><span class="sxs-lookup"><span data-stu-id="3ad6b-149">Tools</span></span>](../../docs/framework/tools/index.md)  
 <span data-ttu-id="3ad6b-150">Popisuje nástroje, které vám pomohou vyvíjet, konfigurovat a nasazovat aplikace s použitím technologií rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="3ad6b-151">.NET ukázky a kurzy</span><span class="sxs-lookup"><span data-stu-id="3ad6b-151">.NET samples and tutorials</span></span>](../samples-and-tutorials/index.md)  
 <span data-ttu-id="3ad6b-152">Poskytuje odkazy na ukázky a kurzy, které vám pomůžou informace o rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3ad6b-152">Provides links to samples and tutorials that help you learn about .NET.</span></span>
