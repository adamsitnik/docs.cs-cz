---
title: Charakteristika moderních webových aplikací
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Charakteristiky moderních webových aplikací
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: d3848f3b0cf993930bfc3801ce40c5eac30f094d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374090"
---
# <a name="characteristics-of-modern-web-applications"></a>Charakteristiky moderních webových aplikací

> "… s řádným návrhem se funkce dodávají bezlevné. Tento přístup je namáhavý, ale nadále je úspěšný. "  
> _\-Dennis Ritchie_

Moderní webové aplikace mají větší nároky na uživatele a větší požadavky než kdykoli dřív. Očekává se, že dnešní webové aplikace budou k dispozici 24/7 odkudkoli na světě a dají se použít prakticky z jakéhokoli zařízení nebo velikosti obrazovky. Webové aplikace musí být zabezpečené, flexibilní a škálovatelné, aby splnily špičky na vyžádání. Ve složitějších scénářích by se měly zpracovávat rozsáhlé uživatelské prostředí založené na klientovi pomocí JavaScriptu a efektivně komunikovat prostřednictvím webových rozhraní API.

ASP.NET Core je optimalizovaná pro moderní webové aplikace a cloudové scénáře hostování. Jeho modulární design umožňuje aplikacím záviset jenom na funkcích, které skutečně používají, zlepšování zabezpečení a výkonu aplikací při snižování požadavků na hostování prostředků.

## <a name="reference-application-eshoponweb"></a>Referenční aplikace: eShopOnWeb

Tyto doprovodné materiály obsahují referenční aplikaci _eShopOnWeb_, která předvádí některé principy a doporučení. Aplikace je jednoduchý online obchod, který podporuje procházení katalogem košile, kávy mugs a dalších marketingových položek. Referenční aplikace je záměrně jednoduchá, aby bylo snazší je snadno pochopit.

![eShopOnWeb](./media/image2-1.png)

**Obrázek 2-1.** eShopOnWeb

> ### <a name="reference-application"></a>Referenční aplikace
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hostování a škálovatelnost v cloudu

ASP.NET Core je optimalizovaná pro Cloud (veřejný cloud, privátní cloud, jakýkoliv Cloud), protože se jedná o málo paměti a vysokou propustnost. Menší nároky na ASP.NET Core aplikace znamená, že je můžete hostovat na stejném hardwaru a platíte za méně prostředků při použití služeb hostování cloudu s průběžnými platbami. Vyšší propustnost znamená, že můžete obsluhovat více zákazníků z aplikace, která má stejný hardware, a dále snižovat nutnost investovat na servery a hostingovou infrastrukturu.

## <a name="cross-platform"></a>Různé platformy

ASP.NET Core je pro různé platformy a může běžet v systémech Linux, macOS a Windows. Tím se otevře mnoho nových možností vývoje i nasazení aplikací vytvořených pomocí ASP.NET Core. Kontejnery Docker – systémy Linux i Windows můžou hostovat aplikace ASP.NET Core, což jim umožní využít výhody [kontejnerů a mikroslužeb](../microservices/index.md).

## <a name="modular-and-loosely-coupled"></a>Modulární a volně spojený

Balíčky NuGet jsou občany první třídy v .NET Core a ASP.NET Core aplikace se skládají z mnoha knihoven přes NuGet. Tato členitost funkcí pomáhá zajistit, aby aplikace byla závislá jenom na funkcích, které skutečně vyžadují, aby se snížila oblast jeho přístupnosti a ohrožení zabezpečení.

ASP.NET Core také plně podporuje [vkládání závislostí](https://deviq.com/dependency-injection/)interně i na úrovni aplikace. Rozhraní mohou mít více implementací, které lze podle potřeby odkládací. Vložení závislostí umožňuje aplikacím volně se oddělit k těmto rozhraním, spíše než ke konkrétním implementům, a usnadnit tak rozšiřování, údržbu a testování.

## <a name="easily-tested-with-automated-tests"></a>Snadné testování pomocí automatizovaných testů

ASP.NET Core aplikace podporují testování částí a jejich volné propojení a podpora pro vkládání závislostí usnadňuje prohození otázek infrastruktury s falešnými implementacemi pro účely testování. ASP.NET Core také dodává TestServer, který se dá použít k hostování aplikací v paměti. Funkční testy mohou následně provádět požadavky na tento server v paměti a využívat úplný zásobník aplikace (včetně middlewaru, směrování, vazeb modelů, filtrů atd.) a příjem odpovědi, a to vše za zlomek času, který by vyžadoval hostování aplikace na skutečném serveru. a provádějte požadavky prostřednictvím síťové vrstvy. Tyto testy jsou obzvláště snadné pro psaní a cenné pro rozhraní API, které jsou v moderních webových aplikacích stále důležitější.

## <a name="traditional-and-spa-behaviors-supported"></a>Podporovaná tradiční a zabezpečené chování

Tradiční webové aplikace zahrnovaly malé chování na straně klienta, ale místo toho se spoléhaly na server pro veškerou navigaci, dotazy a aktualizace, které může být potřeba udělat. Každá nová operace, kterou uživatel udělal, by se přeložila na novou webovou žádost. Výsledkem je úplné načtení stránky v prohlížeči koncového uživatele. Rozhraní Classic model-View-Controller (MVC) obvykle používají tento přístup, přičemž každý nový požadavek odpovídající jiné akci kontroleru, který by měl zase pracovat s modelem a vrací zobrazení. Některé jednotlivé operace na dané stránce můžou být vylepšené funkcemi AJAX (asynchronní JavaScript a XML), ale celková architektura aplikace používala mnoho různých zobrazení MVC a koncových bodů URL. Kromě toho ASP.NET Core MVC podporuje také Razor Pages, což je jednodušší způsob, jak organizovat stránky ve stylu MVC.

Jednostránkové aplikace (jednostránkové) naproti tomu obsahují velmi málo dynamicky vygenerované stránky na straně serveru (pokud existují). Mnoho jednostránkové se inicializuje v rámci statického souboru HTML, který načte potřebné knihovny JavaScriptu ke spuštění a spuštění aplikace. Tyto aplikace výrazně využívají webová rozhraní API pro potřeby svých dat a můžou poskytovat mnohem rozsáhlejší uživatelské prostředí.

Mnoho webových aplikací zahrnuje kombinaci tradičního chování webových aplikací (obvykle pro obsah) a jednostránkové (pro interaktivitu). ASP.NET Core podporuje MVC (zobrazení nebo stránkování) i webová rozhraní API ve stejné aplikaci pomocí stejné sady nástrojů a základních knihoven architektury.

## <a name="simple-development-and-deployment"></a>Jednoduchý vývoj a nasazení

ASP.NET Core aplikace je možné psát pomocí jednoduchých textových editorů a rozhraní příkazového řádku nebo s plnohodnotným vývojovým prostředím, jako je Visual Studio. Aplikace monolitické jsou obvykle nasazeny do jednoho koncového bodu. Nasazení lze snadno automatizovat v rámci kanálu průběžné integrace (CI) a průběžného doručování (CD). Kromě tradičních nástrojů pro CI/CD má Windows Azure integrovanou podporu pro úložiště Git a může automaticky nasadit aktualizace, když se provedou v zadané větvi nebo značce Git.

## <a name="traditional-aspnet-and-web-forms"></a>Tradiční ASP.NET a webové formuláře

Kromě ASP.NET Core bude tradiční ASP.NET 4. x nadále spolehlivou a spolehlivou platformou pro vytváření webových aplikací. ASP.NET podporuje vývojové modely MVC a webové rozhraní API a také webové formuláře, které jsou vhodné pro bohatou podporu aplikací založených na stránkách a nabízí bohatou ekosystém komponent třetích stran. Microsoft Azure má skvělou podporu dlouhodobě zavazuje chránit pro aplikace ASP.NET 4. x a mnoho vývojářů je s touto platformou obeznámené.

> ### <a name="references--modern-web-applications"></a>Odkazy – moderní webové aplikace
>
> - **Úvod do ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Šest klíčových výhod ASP.NET Core, které se liší a lépe**  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Testování v ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
>[Předchozí](index.md)Další
>[](choose-between-traditional-web-and-single-page-apps.md)
