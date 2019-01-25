---
title: Revize lokalizovatelnosti
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4c205d61e6de3e835954e405cece143520b4d2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623977"
---
# <a name="localizability-review"></a><span data-ttu-id="09193-102">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="09193-102">Localizability Review</span></span>
<span data-ttu-id="09193-103">Přezkoumání lokalizovatelnosti je mezikroku vývoj světově připravených aplikací.</span><span class="sxs-lookup"><span data-stu-id="09193-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="09193-104">Ověřuje, že globalizovaná aplikace je připravena k lokalizaci a identifikuje jakýkoli kód, nebo všechny aspekty uživatelského rozhraní, které vyžadují speciální zacházení.</span><span class="sxs-lookup"><span data-stu-id="09193-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="09193-105">Tento krok také pomáhá zajistit, že proces lokalizace nezpůsobí žádné funkčních chyb do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="09193-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="09193-106">Při všech problémech, přezkoumání lokalizovatelnosti vyvolané vyřeší, vaše aplikace je připravena k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="09193-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="09193-107">Pokud je důkladné přezkoumání lokalizovatelnosti, by nemělo být upravit veškerý kód zdroje během proces lokalizace.</span><span class="sxs-lookup"><span data-stu-id="09193-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="09193-108">Přezkoumání lokalizovatelnosti se skládá z následujících tří kontroly:</span><span class="sxs-lookup"><span data-stu-id="09193-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="09193-109">Implementace doporučení pro globalizaci?</span><span class="sxs-lookup"><span data-stu-id="09193-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="09193-110">Jazykové funkce správného zpracování?</span><span class="sxs-lookup"><span data-stu-id="09193-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="09193-111">Otestovali jste aplikaci s mezinárodními daty?</span><span class="sxs-lookup"><span data-stu-id="09193-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="09193-112">Implementace doporučení pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="09193-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="09193-113">Pokud máte navržená a vyvinutá vaší aplikace pomocí na lokalizaci a pokud jste postupovali podle doporučení popsaných v [globalizace](../../../docs/standard/globalization-localization/globalization.md) článku, přezkoumání lokalizovatelnosti do značné míry budou pouze kontrolou kvality .</span><span class="sxs-lookup"><span data-stu-id="09193-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="09193-114">V opačném případě během této fáze je vhodné zkontrolovat a implementaci doporučení pro [globalizace](../../../docs/standard/globalization-localization/globalization.md)a opravte chyby ve zdrojovém kódu, které brání lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="09193-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="09193-115">Zpracování funkcí závislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="09193-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="09193-116">Rozhraní .NET Framework neposkytuje programové podpory v různých oblastech, které výrazně lišit podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="09193-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="09193-117">Ve většině případů musíte napsat vlastní kód pro zpracování oblasti funkcí, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="09193-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="09193-118">Adresy.</span><span class="sxs-lookup"><span data-stu-id="09193-118">Addresses.</span></span>  
  
-   <span data-ttu-id="09193-119">Telefonní čísla.</span><span class="sxs-lookup"><span data-stu-id="09193-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="09193-120">Formáty papíru.</span><span class="sxs-lookup"><span data-stu-id="09193-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="09193-121">Jednotky délky, váhy, oblasti, svazek a teploty.</span><span class="sxs-lookup"><span data-stu-id="09193-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="09193-122">Přestože rozhraní .NET Framework neposkytuje nabízí integrovanou podporu pro převod mezi měrné jednotky, můžete použít <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> a určí, zda konkrétní zemi nebo oblast používá metrika systému, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="09193-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="09193-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="09193-123">Testing your application</span></span>  
 <span data-ttu-id="09193-124">Předtím, než je lokalizovat aplikaci, měli byste otestovat pomocí mezinárodní data na mezinárodních verzích operačního systému.</span><span class="sxs-lookup"><span data-stu-id="09193-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="09193-125">I když většina uživatelského rozhraní nebude v tomto okamžiku lokalizována, bude možné zjišťovat problémy, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="09193-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="09193-126">Serializovaná data, která není správně deserializovat mezi verzemi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="09193-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="09193-127">Číselná data, která nebere v úvahu konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="09193-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="09193-128">Například může být zobrazena čísla s nepřesné skupiny oddělovače, oddělovače desetinných míst nebo symboly měny.</span><span class="sxs-lookup"><span data-stu-id="09193-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="09193-129">Datum a čas dat, který nepředstavuje konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="09193-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="09193-130">Například číslo představující měsíc a den mohou objevit v nesprávném pořadí, oddělovače data může být nesprávný nebo může být nesprávné informace o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="09193-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="09193-131">Prostředky, které nelze nalézt, protože nebylo nalezeno výchozí jazykovou verzi pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="09193-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="09193-132">Řetězce, které jsou zobrazeny v neobvyklé objednávky pro konkrétní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="09193-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="09193-133">Řetězec porovnání nebo porovnání rovnosti, které vrací neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="09193-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="09193-134">Pokud jste postupovali podle doporučení pro globalizaci při vývoji vaší aplikace, zpracovává zohledňující jazykovou verzi funkce správně a identifikovat a řešit problémy lokalizace, které vznikly během testování, můžete přejít k dalšímu kroku, [Lokalizace](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="09193-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09193-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09193-135">See also</span></span>

- [<span data-ttu-id="09193-136">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="09193-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="09193-137">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="09193-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)
- [<span data-ttu-id="09193-138">Globalizace</span><span class="sxs-lookup"><span data-stu-id="09193-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="09193-139">Prostředky v desktopových aplikacích</span><span class="sxs-lookup"><span data-stu-id="09193-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
