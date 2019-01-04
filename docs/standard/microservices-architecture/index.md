---
title: Mikroslužby .NET. Architektura pro Kontejnerizované aplikace .NET
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Mikroslužby jsou modulární a umožňují nezávislé nasazení služby. Kontejnery dockeru (pro systémy Linux a Windows) zjednodušit nasazování a testování seskupí služby a jeho závislosti do jedné jednotky, které je potom spouštět v izolovaném prostředí.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 52435c31e77e7139b982829ae4ab33a5e0f9f045
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030435"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="c11f5-105">Mikroslužby .NET: Architektura pro Kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="c11f5-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Titulní knihy](./media/cover-small.png)

<span data-ttu-id="c11f5-107">**EDICE v2.1.03** – aktualizováno, aby ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c11f5-107">**EDITION v2.1.03** - Updated to ASP.NET Core 2.1</span></span>

<span data-ttu-id="c11f5-108">Tato příručka slouží jako úvod k vývoji aplikací založených na mikroslužbách a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c11f5-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="c11f5-109">Tento článek popisuje kontrol architektonického návrhu a implementace přístupy pomocí .NET Core a kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c11f5-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> 

<span data-ttu-id="c11f5-110">Aby bylo snazší, abyste mohli začít, průvodce se zaměřuje na odkaz kontejnerizovaných a aplikací založených na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="c11f5-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="c11f5-111">Referenční aplikace je k dispozici na [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="c11f5-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="c11f5-112">Odkazy na akce</span><span class="sxs-lookup"><span data-stu-id="c11f5-112">Action links</span></span>

* <span data-ttu-id="c11f5-113">Stáhněte si tuto e-kniha ve formát vašeho výběru: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span><span class="sxs-lookup"><span data-stu-id="c11f5-113">Download this eBook in your format of choice: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

* <span data-ttu-id="c11f5-114">Klon/Forku referenční aplikace [aplikaci eShopOnContainers na Githubu](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="c11f5-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>
 
* <span data-ttu-id="c11f5-115">Podívejte [úvodní video na Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="c11f5-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

* <span data-ttu-id="c11f5-116">Seznamte se [architektury Mikroslužeb](https://aka.ms/MicroservicesArchitecture) hned</span><span class="sxs-lookup"><span data-stu-id="c11f5-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="c11f5-117">Úvod</span><span class="sxs-lookup"><span data-stu-id="c11f5-117">Introduction</span></span>

<span data-ttu-id="c11f5-118">Podniky jsou stále porozumění úspory nákladů, řešení problémů s nasazením a zlepšení operace DevOps a produkčním prostředí pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c11f5-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="c11f5-119">Microsoft má byla uvolnění inovace kontejner pro Windows a Linux tak, že vytvoříte produkty, jako je Azure Container Service a Azure Service Fabric a díky partnerství s vedoucím postavením, jako je Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c11f5-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="c11f5-120">Tyto produkty poskytovat kontejneru řešení, která pomáhají společnostem sestavovat a nasazovat aplikace v cloudu rychlost a škálování, kterou si sami vyberou platformy nebo nástroje.</span><span class="sxs-lookup"><span data-stu-id="c11f5-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="c11f5-121">Docker je stále de facto standardem v odvětví kontejneru, podporovány jsou nejdůležitější dodavatelé v ekosystémů Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="c11f5-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="c11f5-122">(Microsoft je hlavní cloudových vendorů, podporu Dockeru.) V budoucích verzích Dockeru bude pravděpodobně všudypřítomná v libovolné datacentrum do cloudu nebo lokálně.</span><span class="sxs-lookup"><span data-stu-id="c11f5-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="c11f5-123">Kromě toho [mikroslužeb](https://martinfowler.com/articles/microservices.html) architektura je nově vznikající jako důležité přístup pro distribuované klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="c11f5-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="c11f5-124">V architektuře s využitím mikroslužeb je aplikace sestavená u kolekce služeb, které mohou být vytvořeny, otestovat, nasazené a systémovou správou verzí nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="c11f5-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="c11f5-125">Informace o této příručce</span><span class="sxs-lookup"><span data-stu-id="c11f5-125">About this guide</span></span>

<span data-ttu-id="c11f5-126">Tato příručka slouží jako úvod k vývoji aplikací založených na mikroslužbách a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c11f5-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="c11f5-127">Tento článek popisuje kontrol architektonického návrhu a implementace přístupy pomocí .NET Core a kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c11f5-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="c11f5-128">Aby bylo snazší začít pracovat s kontejnery a mikroslužby, průvodce se zaměřuje na odkaz kontejnerizovaných a aplikací založených na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="c11f5-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="c11f5-129">Ukázková aplikace je k dispozici na [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="c11f5-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="c11f5-130">Tato příručka obsahuje základní vývoj a doprovodné materiály k architektuře primárně na úrovni prostředí vývoj se zaměřením na technologie: .NET Core a docker.</span><span class="sxs-lookup"><span data-stu-id="c11f5-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="c11f5-131">Naším úmyslem je, že si přečtete tuto příručku při posuzování návrhu aplikace, nemusíte se soustředit na infrastrukturu (v cloudu nebo místních) vašeho produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="c11f5-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="c11f5-132">Bude rozhodnutí o infrastruktuře později, při vytváření aplikace připravené pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="c11f5-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="c11f5-133">Proto tato příručka je určena být nezávislá a více vývojové prostředí – zaměřené na infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="c11f5-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="c11f5-134">Po zkoumali této příručce, bude dalším krokem je další informace o mikroslužbách připravené pro produkční prostředí v Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c11f5-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="c11f5-135">Version</span><span class="sxs-lookup"><span data-stu-id="c11f5-135">Version</span></span>

<span data-ttu-id="c11f5-136">Tento průvodce byl změněn na pokrytí **.NET Core 2.1** verze a mnoho dalších aktualizace související s stejné "wave" technologií (tj.</span><span class="sxs-lookup"><span data-stu-id="c11f5-136">This guide has been revised to cover **.NET Core 2.1** version plus many additional updates related to the same “wave” of technologies (that is.</span></span> <span data-ttu-id="c11f5-137">Azure a další 3. stran technologie) okamžiku v čase s .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="c11f5-137">Azure and additional 3rd party technologies) coinciding in time with .NET Core 2.1.</span></span> <span data-ttu-id="c11f5-138">To je důvod, proč verze knihy se také aktualizovala na verzi **2.1**.</span><span class="sxs-lookup"><span data-stu-id="c11f5-138">That’s why the book version has also been updated to version **2.1**.</span></span> 

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="c11f5-139">Co tato příručka nepopisuje</span><span class="sxs-lookup"><span data-stu-id="c11f5-139">What this guide does not cover</span></span>

<span data-ttu-id="c11f5-140">Tato příručka se nezaměřuje na životního cyklu aplikací, vývoj a provoz kanálů CI/CD nebo tým pracovat.</span><span class="sxs-lookup"><span data-stu-id="c11f5-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="c11f5-141">Doplňkové průvodce [Kontejnerizovaných životní cyklus aplikace Dockeru s platformou a nástroji Microsoft](https://aka.ms/dockerlifecycleebook) se zaměřuje na tohoto subjektu.</span><span class="sxs-lookup"><span data-stu-id="c11f5-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="c11f5-142">Aktuální Průvodce také neposkytuje podrobné informace o implementaci na infrastrukturu Azure, jako je například informace o konkrétní orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="c11f5-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c11f5-143">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c11f5-143">Additional resources</span></span>

-   <span data-ttu-id="c11f5-144">**Životní cyklus aplikace Dockeru s platformou a nástroji Microsoft kontejnerizovaných** (ke stažení e kniha)</span><span class="sxs-lookup"><span data-stu-id="c11f5-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a><span data-ttu-id="c11f5-145">Kdo by měl používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="c11f5-145">Who should use this guide</span></span>

<span data-ttu-id="c11f5-146">Jsme napsali Tato příručka pro vývojáře a architekty řešení, kteří jsou nové pro vývoj aplikací založených na Dockeru a architektura založená na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="c11f5-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="c11f5-147">Tento průvodce je pro, pokud chcete získat informace tom, jak navrhovat, navrhování a implementace aplikací testování konceptu s vývojovým technologiím Microsoftu (se zvláštním zaměřením na .NET Core) a s kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c11f5-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="c11f5-148">Také zjistíte Tato příručka užitečné, pokud jste technický pracovník s rozhodovací pravomocí, jako je například podnikový architekt, kdo chce, aby se architektura a přehledu technologie před rozhodnout, na jaké přístup k výběru pro nové a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="c11f5-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="c11f5-149">Jak používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="c11f5-149">How to use this guide</span></span>

<span data-ttu-id="c11f5-150">První části této příručky zavádí kontejnery Dockeru, popisuje, jak si vybrat mezi .NET Core a .NET Framework jako rozhraní pro vývoj a najdete zde přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="c11f5-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="c11f5-151">Tento obsah je pro architekty a technické pracovníky s rozhodovací pravomocí, kteří mají přehled, ale není potřeba zaměřit se na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="c11f5-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="c11f5-152">Začíná druhé části v průvodci [aplikací založených na proces vývoje pro Docker](./docker-application-development-process/index.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="c11f5-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="c11f5-153">Zaměřuje se na vývoj a mikroslužeb vzory pro provádění aplikací pomocí .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="c11f5-153">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="c11f5-154">Tato část bude mít největší zájem vývojářům a architektům, kteří chtějí soustředit se na kód a vzorců a podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="c11f5-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="c11f5-155">Související mikroslužby a aplikace založené na kontejnerech odkaz: aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c11f5-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="c11f5-156">Aplikaci eShopOnContainers aplikace je odkaz na open source aplikace pro .NET Core a mikroslužeb, která slouží k nasazení kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c11f5-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="c11f5-157">Aplikace se skládá z více subsystémů, včetně několik e-store uživatelského rozhraní front-endů (aplikace Web MVC, SPA webové a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="c11f5-157">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="c11f5-158">Zahrnuje také back-end mikroslužeb a kontejnerů pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="c11f5-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span> 

<span data-ttu-id="c11f5-159">Účelem aplikace je k prezentaci vzorech architektury.</span><span class="sxs-lookup"><span data-stu-id="c11f5-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="c11f5-160">**IT není připravené pro produkční prostředí ŠABLONU** ke spouštění skutečných aplikací.</span><span class="sxs-lookup"><span data-stu-id="c11f5-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="c11f5-161">Aplikace ve skutečnosti je ve stavu trvalé beta, jak se také používá k testování nových potenciálně zajímavý technologií, jako zobrazí.</span><span class="sxs-lookup"><span data-stu-id="c11f5-161">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="c11f5-162">Pošlete nám svůj názor!</span><span class="sxs-lookup"><span data-stu-id="c11f5-162">Send us your feedback!</span></span>

<span data-ttu-id="c11f5-163">Jsme napsali této příručce, které vám pomůžou porozumět architektuře mikroslužeb v rozhraní .NET a kontejnerizovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="c11f5-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="c11f5-164">Průvodce a související referenční aplikace bude se vyvíjí, takže vaše připomínky budou vítány!</span><span class="sxs-lookup"><span data-stu-id="c11f5-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="c11f5-165">Pokud máte připomínky jak se tento průvodce může zlepšit, odešlete jim:</span><span class="sxs-lookup"><span data-stu-id="c11f5-165">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="c11f5-166">Závěrečné titulky</span><span class="sxs-lookup"><span data-stu-id="c11f5-166">Credits</span></span>

<span data-ttu-id="c11f5-167">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="c11f5-167">Co-Authors:</span></span>

> <span data-ttu-id="c11f5-168">**De la Torre Cesarovi**, Senior PM, .NET produktový tým Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="c11f5-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="c11f5-169">**Bill Wagnera**, Senior obsahu pro vývojáře, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="c11f5-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="c11f5-170">**Mike Rousos**, hlavní softwarový inženýr, týmu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="c11f5-171">Editory:</span><span class="sxs-lookup"><span data-stu-id="c11f5-171">Editors:</span></span>

> <span data-ttu-id="c11f5-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="c11f5-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="c11f5-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="c11f5-173">**Steve Hoag**</span></span>

<span data-ttu-id="c11f5-174">Účastníci a recenzenti:</span><span class="sxs-lookup"><span data-stu-id="c11f5-174">Participants and reviewers:</span></span>

> <span data-ttu-id="c11f5-175">**Jeffrey Richter**, Partner softwaru Eng týmu Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-176">**Jimmy Bogard**, hlavní architekt na Headspring</span><span class="sxs-lookup"><span data-stu-id="c11f5-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="c11f5-177">**UDI Dahan**, Zakladatel a generální ředitel, určitého softwaru</span><span class="sxs-lookup"><span data-stu-id="c11f5-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="c11f5-178">**Jimmy Nilsson**, Spoluzakladatel a generální Factor10</span><span class="sxs-lookup"><span data-stu-id="c11f5-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="c11f5-179">**Glenn Condron**, Senior Program Manager tým ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c11f5-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="c11f5-180">**Označit Fussell**, hlavní Projektový manažer zájemce, tým Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-181">**Diego Vega**, PM zájemce, Entity Framework týmu, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-182">**Jiří Dorrans**, hlavní manažer programu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c11f5-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="c11f5-183">**Rowan Miller**, Senior Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-184">**Ankit Asthana**, hlavní manažer PM, týmu .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-185">**Scott Hunter**, Partner Director oddělení PM, týmu .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-186">**Dylan Reisenberger**, architekt a vedoucí vývoje v Polly</span><span class="sxs-lookup"><span data-stu-id="c11f5-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="c11f5-187">**Steve Smith**, Tvůrce softwaru & Trainer na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="c11f5-187">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="c11f5-188">**Ian Cooper**, kódování navrhovat jasnější na</span><span class="sxs-lookup"><span data-stu-id="c11f5-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="c11f5-189">**Unai Zorrilla**, architekt a vedoucí vývoje v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="c11f5-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="c11f5-190">**Eduard Tomáši**, vedoucí vývoje v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="c11f5-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="c11f5-191">**Ramon Tomáši**, vývojář v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="c11f5-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="c11f5-192">**David Sanz**, vývojář v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="c11f5-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="c11f5-193">**Javier Valero**, hlavní, provozní ředitel ve Grupo řešení</span><span class="sxs-lookup"><span data-stu-id="c11f5-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="c11f5-194">**Pierre proso**, Senior konzultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-195">**Michael Friis**, správce produktu, Inc Dockeru</span><span class="sxs-lookup"><span data-stu-id="c11f5-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="c11f5-196">**Charles Lowell**, softwarový inženýr, týmu VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c11f5-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="c11f5-197">**Miguel Veloso**, Senior konzultant na Turing výzvy</span><span class="sxs-lookup"><span data-stu-id="c11f5-197">**Miguel Veloso**, Sr. Consultant at Turing Challenge</span></span>


## <a name="copyright"></a><span data-ttu-id="c11f5-198">Copyright</span><span class="sxs-lookup"><span data-stu-id="c11f5-198">Copyright</span></span>

<span data-ttu-id="c11f5-199">Ke stažení je k dispozici na: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="c11f5-199">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="c11f5-200">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="c11f5-200">PUBLISHED BY</span></span>

<span data-ttu-id="c11f5-201">Microsoft Developer Division, .NET a Visual Studio produktových týmů</span><span class="sxs-lookup"><span data-stu-id="c11f5-201">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="c11f5-202">Divize Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="c11f5-202">A division of Microsoft Corporation</span></span>

<span data-ttu-id="c11f5-203">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="c11f5-203">One Microsoft Way</span></span>

<span data-ttu-id="c11f5-204">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="c11f5-204">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="c11f5-205">Copyright © 2018 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c11f5-205">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="c11f5-206">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="c11f5-206">All rights reserved.</span></span> <span data-ttu-id="c11f5-207">Žádná část obsahu této knihy může reprodukovat nebo v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="c11f5-207">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="c11f5-208">Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory.</span><span class="sxs-lookup"><span data-stu-id="c11f5-208">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="c11f5-209">Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="c11f5-209">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="c11f5-210">Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="c11f5-210">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="c11f5-211">Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.</span><span class="sxs-lookup"><span data-stu-id="c11f5-211">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="c11f5-212">Microsoft a ochranné známky uvedený na <https://www.microsoft.com> na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c11f5-212">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="c11f5-213">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="c11f5-213">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="c11f5-214">Velryba logo Dockeru je registrovaná ochranná známka společnosti Docker, Inc. Použít oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c11f5-214">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="c11f5-215">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="c11f5-215">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="c11f5-216">Next</span><span class="sxs-lookup"><span data-stu-id="c11f5-216">Next</span></span>](container-docker-introduction/index.md)
