---
title: Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Mikroslužby jsou modulární a nezávisle nasazujíelné služby. Kontejnery Docker (pro Linux a Windows) zjednodušují nasazení a testování tím, že propojí službu a její závislosti do jedné jednotky, která se pak spustí v izolovaném prostředí.
ms.date: 01/07/2019
ms.openlocfilehash: 7fa4935fe56ca873a5311812637964083e34170e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089911"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikroslužby .NET: architektura pro kontejnerové aplikace .NET

![Titulní kniha](./media/cover-small.png)

**Edice 2.2** – aktualizace na ASP.NET Core 2,2

Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů. Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker.

Aby bylo snazší začít, příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat. Referenční aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .

## <a name="action-links"></a>Odkazy na akce

- Stáhnout tuto elektronickou knihu ve zvoleném formátu (pouze anglické verze): | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |

- Klonování/rozvětvení referenční aplikace [eShopOnContainers na GitHubu](https://github.com/dotnet-architecture/eShopOnContainers)

- Podívejte se na [úvodní video na Channel 9](https://aka.ms/microservices-video)

- Získejte hned informace o [architektuře mikroslužeb](https://aka.ms/MicroservicesArchitecture) .

## <a name="introduction"></a>Úvod

Podniky mají stále větší náklady na úspory nákladů, řešení problémů s nasazením a vylepšení DevOps a produkčních operací pomocí kontejnerů. Společnost Microsoft vydala inovace kontejnerů pro Windows a Linux tím, že vytváří produkty, jako je Azure Kubernetes Service a Azure Service Fabric, a spolupracuje s oborovými vedoucími, jako jsou Docker, Mesosphere a Kubernetes. Tyto produkty poskytují řešení kontejnerů, která společnosti pomůžou sestavovat a nasazovat aplikace při rychlosti a škálování cloudu bez ohledu na to, jakou platformu nebo nástroje.

Docker se stává jako de facto standard v odvětví kontejneru, který je podporovaný nejvýznamnějšími dodavateli v ekosystémech Windows a Linux. (Microsoft je jedním z hlavních dodavatelů cloudů, kteří podporují Docker.) V budoucnu se Docker bude pravděpodobně všudypřítomný do libovolného datacentra v cloudu nebo v místním prostředí.

Kromě toho architektura [mikroslužeb](https://martinfowler.com/articles/microservices.html) se vychází jako důležitý přístup pro distribuované klíčové aplikace. V architektuře založené na mikroslužbách je aplikace postavená na kolekci služeb, které se dají vyvíjet, testovat, nasazovat a samostatně nakládat s verzemi.

## <a name="about-this-guide"></a>O této příručce

Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů. Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker. Aby bylo snazší začít s kontejnery a mikroslužbami, tato příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat. Ukázková aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .

Tato příručka poskytuje pokyny pro základní vývoj a architekturu primárně na úrovni vývojového prostředí se zaměřením na dvě technologie: Docker a .NET Core. Naším záměrem je přečíst si tuto příručku při zvažování návrhu vaší aplikace bez zaměření na infrastrukturu (Cloud nebo místní) vašeho provozního prostředí. Rozhodnutí o vaší infrastruktuře budete provádět později při vytváření aplikací připravených pro produkční prostředí. Proto je tato příručka zamýšlená jako infrastruktura nezávislá a další vývojové prostředí.

Po prostudování tohoto průvodce by vám v dalším kroku pomohlo zjistit mikroslužby připravené k výrobě na Microsoft Azure.

## <a name="version"></a>Version

Tato příručka byla revidována tak, aby kryla verzi **.NET Core 2,2** a řadu dalších aktualizací, které se vztahují ke stejným "Wave" technologií (tj. Azure a další technologie jiných výrobců se shodují v čase s .NET Core 2,2. To je důvod, proč se verze knihy aktualizovala také na verzi **2,2**.

## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nepokrývá

Tato příručka se nezaměřuje na životní cyklus aplikací, DevOps, kanály CI/CD ani týmovou práci. [Doplněný životní cyklus aplikace Docker v kontejneru s využitím platformy a nástrojů Microsoftu se](https://aka.ms/dockerlifecycleebook) zaměřuje na tento předmět. Aktuální příručka také neposkytuje podrobnosti o implementaci infrastruktury Azure, jako jsou informace o konkrétních orchestrcích.

### <a name="additional-resources"></a>Další zdroje

- **Kontejnerové životní cykly aplikace Docker s platformou a nástroji Microsoftu** (elektronická kniha ke stažení)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Tuto příručku jsme napsali pro vývojáře a architekty řešení, kteří jsou noví pro vývoj aplikací založených na Docker a na architekturu založenou na mikroslužbách. Tato příručka je určena pro vás, pokud se chcete dozvědět, jak architekt, navrhovat a implementovat aplikace pro zkušební použití pomocí vývojových technologií Microsoftu (se speciálním zaměřením na .NET Core) a s kontejnery Docker.

Tento průvodce najdete také v případě, že jste Tvůrce technického rozhodnutí, jako je například podnikový architekt, který vyžaduje architekturu a technologický přehled, než se rozhodnete, jaký přístup vybrat pro nové a moderní distribuované aplikace.

### <a name="how-to-use-this-guide"></a>Jak používat tohoto průvodce

První část této příručky zavádí kontejnery Docker, popisuje, jak zvolit mezi .NET Core a .NET Framework jako vývojovou architekturou a poskytuje přehled mikroslužeb. Tento obsah je určen pro architekty a pracovníky technického rozhodování, kteří chtějí přehled, ale nemusí se soustředit na podrobnosti implementace kódu.

Druhá část příručky začíná [procesem vývoje pro aplikace založené na Docker](./docker-application-development-process/index.md) . Zaměřuje se na vývoj a vzory mikroslužeb pro implementaci aplikací pomocí .NET Core a Docker. Tato část bude mít největší zájem na vývojáře a architekty, kteří se chtějí zaměřit na kód a podrobnosti o vzorech a implementaci.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Související referenční aplikace založené na mikroslužbách a kontejneru: eShopOnContainers

Aplikace eShopOnContainers je open source referenční aplikace pro .NET Core a mikroslužby, které jsou navržené tak, aby se nasadily pomocí kontejnerů Docker. Aplikace se skládá z několika subsystémů, včetně několika front-Store přední konců uživatelského rozhraní (aplikace webové MVC, webové zabezpečené ověřování a nativní mobilní aplikace). Zahrnuje také back-endové mikroslužby a kontejnery pro všechny požadované operace na straně serveru.

Účelem aplikace je předvedení struktur architektury. Nejedná se **o šablonu připravenou pro produkční prostředí** pro spouštění reálných aplikací. Ve skutečnosti je aplikace v trvalé verzi beta verze, protože se také používá k otestování nových potenciálně zajímavých technologií, které se zobrazují.

## <a name="send-us-your-feedback"></a>Pošlete nám svůj názor.

Tento průvodce jsme napsali a pomohli vám pochopit architekturu kontejnerových aplikací a mikroslužeb v .NET. Bude vyvíjena příručka a související referenční aplikace, takže jsme Vítejte na vašem názoru. Pokud máte komentáře týkající se toho, jak se dá tato příručka zlepšit, pošlete prosím jim tyto informace:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a>dobropis

Spoluautoři:

> **Cesar de la Torre**, SR. PM, produktový tým .NET, Microsoft Corp.
>
> **Bill Wagner**, SR. Content Developer, C + E, Microsoft Corp.
>
> **Jan Rousos**, hlavní softwarový inženýr, DevDiv Cat tým, Microsoft

Editory

> **Mike Pope**
>
> **Steve Hoag**

Účastníci a kontroloři:

> **Jeffrey Richter**, partnerský software eng, tým Azure, Microsoft
>
> **Jimmy Bogard**, hlavní architekt na headspring
>
> **UDI Dahan**, zakladatel & výkonný ředitel, konkrétní software
>
> **Jimmy Nilsson**, zakladatel a generální ředitel pro Factor10
>
> **Glenn Condron**, SR. Program Manager, ASP.NET tým
>
> **Mark Fussell**, hlavní vedoucí pro odpoledne, Azure Service Fabric Team, Microsoft
>
> **Diegu Vega**, vedoucí pracovník, Entity Framework tým, Microsoft
>
> **Barryho Dorrans**, správce programu SR. Security
>
> **Rowan Miller**, SR. Program Manager, Microsoft
>
> **Ankit Asthana**, hlavní správce odpoledne, tým .NET, Microsoft
>
> **Scott Hunterem**, ředitel pro partnery, tým .NET, Microsoft
>
> **Nish Anil**, SR. Program Manager, .NET Team, Microsoft
>
> **Dylan Reisenberger**, architekt a vývojářského vedoucího v Polly
>
> **Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper**, architekt kódu na jasnější úrovni
>
> **Unai Zorrilla**, architekt a vývojářské olovo v jednoduchých konceptech
>
> **Eduard Tomas**, vedoucí pro vývoj na jednoduchých konceptech
>
> **Ramon Tomas**, Developer na jednoduchých konceptech
>
> **David Sanz**, Developer na jednoduchých konceptech
>
> **Javier Valero**, vedoucí pracovník v Grupo solutio
>
> **Pierre-Millet**, SR. konzultant, Microsoft
>
> **Michael Friis**, produktový manažer, Docker Inc
>
> **Charles Lowell**, software inženýr, vs Cat tým, Microsoft
>
> **Miguel Veloso**, SR. konzultant při Turing výzvě

## <a name="copyright"></a>Úprava

STAŽENÍ k dispozici na adrese: <https://aka.ms/microservicesebook>

PUBLIKOVAL (A)

Microsoft Developer divize, .NET a Visual Studio Product teams

Divize společnosti Microsoft Corporation

Jeden způsob Microsoftu

Redmond, Washington 98052-6399

Copyright © 2019 od společnosti Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené. Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.

Microsoft a ochranné známky uvedené na adrese <https://www.microsoft.com> na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

>[!div class="step-by-step"]
>[Next](container-docker-introduction/index.md)
