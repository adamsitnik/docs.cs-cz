---
title: Technologií rozhraní .NET framework není k dispozici v rozhraní .NET Core
description: Seznamte se s technologií rozhraní .NET Framework, které jsou k dispozici v rozhraní .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/7/2018
ms.openlocfilehash: 8b43c15a942e0effab486e5399325bec746484a2
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904901"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a><span data-ttu-id="4b66a-103">Technologií rozhraní .NET framework není k dispozici v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b66a-103">.NET Framework technologies unavailable on .NET Core</span></span>

<span data-ttu-id="4b66a-104">Několik technologií, které jsou k dispozici pro knihovny rozhraní .NET Framework nejsou k dispozici pro použití s .NET Core, jako je například objektů třídy AppDomains, vzdálené komunikace, zabezpečení přístupu kódu (CAS) a transparentnost zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4b66a-104">Several technologies available to .NET Framework libraries aren't available for use with .NET Core, such as AppDomains, Remoting, Code Access Security (CAS), and Security Transparency.</span></span> <span data-ttu-id="4b66a-105">Pokud vaše knihovny spoléhat na jeden nebo více z těchto technologií, vezměte v úvahu alternativních přístupů popsaných níže.</span><span class="sxs-lookup"><span data-stu-id="4b66a-105">If your libraries rely on one or more of these technologies, consider the alternative approaches outlined below.</span></span> <span data-ttu-id="4b66a-106">Další informace o kompatibilitě rozhraní API CoreFX tým udržuje [seznam konce změny/compat chování a zastaralé nebo starší verze rozhraní API](https://github.com/dotnet/corefx/wiki/ApiCompat) v Githubu.</span><span class="sxs-lookup"><span data-stu-id="4b66a-106">For more information on API compatibility, the CoreFX team maintains a [List of behavioral changes/compat breaks and deprecated/legacy APIs](https://github.com/dotnet/corefx/wiki/ApiCompat) at GitHub.</span></span>

<span data-ttu-id="4b66a-107">To, že rozhraní API nebo technologie v současnosti není implementovaná nebude neznamená, že má nepodporovanou záměrně.</span><span class="sxs-lookup"><span data-stu-id="4b66a-107">Just because an API or technology isn't currently implemented doesn't imply it's intentionally unsupported.</span></span> <span data-ttu-id="4b66a-108">By měli nejdřív vyhledat úložiště GitHub pro .NET Core, pokud chcete zobrazit, pokud konkrétní problém narazíte je záměrné, ale pokud nemůžete najít takový ukazatel, požádejte prosím problém ve službě [úložišti dotnet/corefx problémy](https://github.com/dotnet/corefx/issues) v Githubu požádat pro konkrétní rozhraní API a technologií.</span><span class="sxs-lookup"><span data-stu-id="4b66a-108">You should first search the GitHub repositories for .NET Core to see if a particular issue you encounter is by design, but if you cannot find such an indicator, please file an issue in the [dotnet/corefx repository issues](https://github.com/dotnet/corefx/issues) at GitHub to ask for specific APIs and technologies.</span></span> <span data-ttu-id="4b66a-109">[Portování požadavky otázky](https://github.com/dotnet/corefx/labels/port-to-core) jsou označené `port-to-core` popisek.</span><span class="sxs-lookup"><span data-stu-id="4b66a-109">[Porting requests in the issues](https://github.com/dotnet/corefx/labels/port-to-core) are marked with the `port-to-core` label.</span></span>

## <a name="appdomains"></a><span data-ttu-id="4b66a-110">AppDomains</span><span class="sxs-lookup"><span data-stu-id="4b66a-110">AppDomains</span></span>

<span data-ttu-id="4b66a-111">Domény aplikace (AppDomains) izolace aplikace od sebe.</span><span class="sxs-lookup"><span data-stu-id="4b66a-111">Application domains (AppDomains) isolate apps from one another.</span></span> <span data-ttu-id="4b66a-112">Objektů třídy AppDomains vyžadují podpora modulu CLR a obvykle jsou dost drahé.</span><span class="sxs-lookup"><span data-stu-id="4b66a-112">AppDomains require runtime support and are generally quite expensive.</span></span> <span data-ttu-id="4b66a-113">Nepodporuje vytváření domén další aplikace...</span><span class="sxs-lookup"><span data-stu-id="4b66a-113">Creating additional app domains is not supported..</span></span> <span data-ttu-id="4b66a-114">Plánujeme není na přidání této funkce v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="4b66a-114">We don't plan on adding this capability in future.</span></span> <span data-ttu-id="4b66a-115">Izolace kódu, doporučujeme samostatné procesy nebo pomocí kontejnerů jako alternativu.</span><span class="sxs-lookup"><span data-stu-id="4b66a-115">For code isolation, we recommend separate processes or using containers as an alternative.</span></span> <span data-ttu-id="4b66a-116">Pro dynamické načítání sestavení, doporučujeme vám nový <xref:System.Runtime.Loader.AssemblyLoadContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b66a-116">For the dynamic loading of assemblies, we recommend the new <xref:System.Runtime.Loader.AssemblyLoadContext> class.</span></span>

<span data-ttu-id="4b66a-117">Pro usnadnění migrace kódu z rozhraní .NET Framework, .NET Core uvádí některé <xref:System.AppDomain> rovinu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4b66a-117">To make code migration from .NET Framework easier, .NET Core exposes some of the <xref:System.AppDomain> API surface.</span></span> <span data-ttu-id="4b66a-118">Některá rozhraní API normálně fungovat (například <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), některé členy Neprovádět žádnou akci (třeba <xref:System.AppDomain.SetCachePath%2A>), a některé z nich výjimku <xref:System.PlatformNotSupportedException> (například <xref:System.AppDomain.CreateDomain%2A>).</span><span class="sxs-lookup"><span data-stu-id="4b66a-118">Some of the APIs function normally (for example, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), some members do nothing (for example, <xref:System.AppDomain.SetCachePath%2A>), and some of them throw <xref:System.PlatformNotSupportedException> (for example, <xref:System.AppDomain.CreateDomain%2A>).</span></span> <span data-ttu-id="4b66a-119">Zkontrolujte typy použít proti [ `System.AppDomain` zdroj odkazu](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) v [úložiště GitHub dotnet/corefx](https://github.com/dotnet/corefx)a vyberte větev, která odpovídá verzi implementovaná.</span><span class="sxs-lookup"><span data-stu-id="4b66a-119">Check the types you use against the [`System.AppDomain` reference source](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) in the [dotnet/corefx GitHub repository](https://github.com/dotnet/corefx), making sure to select the branch that matches your implemented version.</span></span>

## <a name="remoting"></a><span data-ttu-id="4b66a-120">Vzdálená komunikace</span><span class="sxs-lookup"><span data-stu-id="4b66a-120">Remoting</span></span>

<span data-ttu-id="4b66a-121">Vzdálené komunikace .NET byla identifikována jako problematické architektury.</span><span class="sxs-lookup"><span data-stu-id="4b66a-121">.NET Remoting was identified as a problematic architecture.</span></span> <span data-ttu-id="4b66a-122">Používá se pro komunikaci mezi domény aplikace, které se už nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="4b66a-122">It's used for cross-AppDomain communication, which is no longer supported.</span></span> <span data-ttu-id="4b66a-123">Vzdálená komunikace také vyžaduje podpora modulu CLR, které je náročné na údržbu.</span><span class="sxs-lookup"><span data-stu-id="4b66a-123">Also, Remoting requires runtime support, which is expensive to maintain.</span></span> <span data-ttu-id="4b66a-124">Z těchto důvodů se nepodporuje vzdálené komunikace .NET na .NET Core a není plánujeme v budoucnu doplnění podpory pro něj.</span><span class="sxs-lookup"><span data-stu-id="4b66a-124">For these reasons, .NET Remoting isn't supported on .NET Core, and we don't plan on adding support for it in the future.</span></span>

<span data-ttu-id="4b66a-125">Komunikace mezi procesy, vezměte v úvahu mechanismus meziprocesové komunikace (IPC) jako alternativu k vzdálené komunikace, jako <xref:System.IO.Pipes> nebo <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b66a-125">For communication across processes, consider inter-process communication (IPC) mechanisms as an alternative to Remoting, such as the <xref:System.IO.Pipes> or the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> class.</span></span>

<span data-ttu-id="4b66a-126">V počítačích použijte jako alternativu řešení založené na síti.</span><span class="sxs-lookup"><span data-stu-id="4b66a-126">Across machines, use a network-based solution as an alternative.</span></span> <span data-ttu-id="4b66a-127">Pokud možno použijte protokol s nízkou režií prostého textu, jako je například HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b66a-127">Preferably, use a low-overhead plain text protocol, such as HTTP.</span></span> <span data-ttu-id="4b66a-128">[Kestrel webový server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), webový server používá ASP.NET Core, je možnost tady.</span><span class="sxs-lookup"><span data-stu-id="4b66a-128">The [Kestrel web server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), the web server used by ASP.NET Core, is an option here.</span></span> <span data-ttu-id="4b66a-129">Také zvážit použití <xref:System.Net.Sockets> pro scénáře založené na síti, mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="4b66a-129">Also consider using <xref:System.Net.Sockets> for network-based, cross-machine scenarios.</span></span> <span data-ttu-id="4b66a-130">Další možnosti najdete v tématu [.NET Open Source projektů pro vývojáře: Zasílání zpráv](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).</span><span class="sxs-lookup"><span data-stu-id="4b66a-130">For more options, see [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).</span></span>

## <a name="code-access-security-cas"></a><span data-ttu-id="4b66a-131">Zabezpečení přístupu kódu (CAS)</span><span class="sxs-lookup"><span data-stu-id="4b66a-131">Code Access Security (CAS)</span></span>

<span data-ttu-id="4b66a-132">Izolace (sandbox), které spoléhá na modul runtime nebo rozhraní, chcete-li omezit které prostředky spravované aplikace nebo knihovna používá nebo běží, [není podporován v rozhraní .NET Framework](~/docs/framework/misc/code-access-security.md) a proto se taky nepodporuje v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b66a-132">Sandboxing, which relies on the runtime or the framework to constrain which resources a managed application or library uses or runs, [isn't supported on .NET Framework](~/docs/framework/misc/code-access-security.md) and therefore is also not supported on .NET Core.</span></span> <span data-ttu-id="4b66a-133">Nejsou moc velký počet případů v rozhraní .NET Framework a modulu runtime kde dojde k zvýšení oprávnění pokračovat zpracování certifikační Autority jako hranice zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4b66a-133">There are too many cases in the .NET Framework and the runtime where an elevation of privileges occurs to continue treating CAS as a security boundary.</span></span> <span data-ttu-id="4b66a-134">Certifikační Autority navíc díky implementaci složitější a často má vliv na správnost výkon pro aplikace, které nechcete použít.</span><span class="sxs-lookup"><span data-stu-id="4b66a-134">In addition, CAS makes the implementation more complicated and often has correctness-performance implications for applications that don't intend to use it.</span></span>

<span data-ttu-id="4b66a-135">Volit raději hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnerů nebo uživatelské účty pro spouštění procesů s minimální sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="4b66a-135">Use security boundaries provided by the operating system, such as virtualization, containers, or user accounts for running processes with the minimum set of privileges.</span></span>

## <a name="security-transparency"></a><span data-ttu-id="4b66a-136">Transparentnost zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4b66a-136">Security Transparency</span></span>

<span data-ttu-id="4b66a-137">Podobně jako u certifikační Autority, transparentnost zabezpečení ze zabezpečení kritického kódu deklarativní způsobem odděluje kódu v izolovaném prostoru, ale je [již nejsou podporovány jako hranice zabezpečení](~/docs/framework/misc/security-transparent-code.md).</span><span class="sxs-lookup"><span data-stu-id="4b66a-137">Similar to CAS, Security Transparency separates sandboxed code from security critical code in a declarative fashion but is [no longer supported as a security boundary](~/docs/framework/misc/security-transparent-code.md).</span></span> <span data-ttu-id="4b66a-138">Tato funkce je nejčastěji používá program Silverlight.</span><span class="sxs-lookup"><span data-stu-id="4b66a-138">This feature is heavily used by Silverlight.</span></span> 

<span data-ttu-id="4b66a-139">Volit raději hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnerů nebo uživatelské účty pro spouštění procesů s nejmenší sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="4b66a-139">Use security boundaries provided by the operating system, such as virtualization, containers, or user accounts for running processes with the least set of privileges.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="4b66a-140">Next</span><span class="sxs-lookup"><span data-stu-id="4b66a-140">Next</span></span>](third-party-deps.md)