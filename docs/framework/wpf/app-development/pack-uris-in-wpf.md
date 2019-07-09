---
title: Sbalení URI v technologii WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 2a0fa9b67f4fa1f3b701cb64579727bedbf5028c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663788"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="d9bb2-102">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="d9bb2-102">Pack URIs in WPF</span></span>

<span data-ttu-id="d9bb2-103">Ve Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] slouží k identifikaci a načíst soubory mnoha způsoby, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="d9bb2-104">Zadání [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zobrazit při prvním spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="d9bb2-105">Načtení obrázků.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-105">Loading images.</span></span>

- <span data-ttu-id="d9bb2-106">Přejděte na stránky.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-106">Navigating to pages.</span></span>

- <span data-ttu-id="d9bb2-107">Načítají se soubory dat – spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-107">Loading non-executable data files.</span></span>

<span data-ttu-id="d9bb2-108">Kromě toho [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] slouží k identifikaci a nahrajte soubory z různých umístěních, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="d9bb2-109">Aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-109">The current assembly.</span></span>

- <span data-ttu-id="d9bb2-110">Odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-110">A referenced assembly.</span></span>

- <span data-ttu-id="d9bb2-111">Umístění relativně k sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="d9bb2-112">Aplikace webovou stránku původu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-112">The application's site of origin.</span></span>

<span data-ttu-id="d9bb2-113">K zajištění konzistentní mechanismus pro identifikaci a načítání těchto typů souborů z těchto míst [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá rozšiřitelnosti aplikace *schéma URI balíku*.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="d9bb2-114">Toto téma obsahuje základní informace o schématu, popisuje, jak vytvořit balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro širokou škálu scénářů, tento článek popisuje absolutní a relativní [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení před zobrazením jak používat balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obou značek a kódu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="d9bb2-115">Schéma URI balíku</span><span class="sxs-lookup"><span data-stu-id="d9bb2-115">The Pack URI Scheme</span></span>

<span data-ttu-id="d9bb2-116">Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] používá schéma [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) specifikace (OPC), který popisuje model pro organizaci a identifikaci obsahu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="d9bb2-117">Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíčku* je logický kontejner pro jeden nebo více logických *částí*.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="d9bb2-118">Tento koncept znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-118">The following figure illustrates this concept.</span></span>

![Balíček a části diagramu](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="d9bb2-120">K identifikaci částí specifikace OPC využívá rozšiřitelnosti RFC 2396 (identifikátory URI (Uniform Resource): Obecná syntaxe) pro definování sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>

<span data-ttu-id="d9bb2-121">Schéma, která je zadána [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je reprezentován jeho předponu http, ftp a souboru jsou známých příkladů.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="d9bb2-122">Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schématu jako jeho schéma používá "balíček" a obsahuje dvě součásti: autorita a cestu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="d9bb2-123">Tady je formát pro sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<span data-ttu-id="d9bb2-124">balíček: / /*autority*/*cesta*</span><span class="sxs-lookup"><span data-stu-id="d9bb2-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="d9bb2-125">*Autority* Určuje typ balíčku, který je obsažen část, zatímco *cesta* Určuje umístění části v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="d9bb2-126">Tento koncept je znázorněn v následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-126">This concept is illustrated by the following figure:</span></span>

![Vztah mezi balíčku, autority a cesty](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="d9bb2-128">Balíčky a části jsou podobná aplikace a soubory, kde aplikace (balíček) může obsahovat jeden nebo více souborů (částí), včetně:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="d9bb2-129">Soubory prostředků, které jsou kompilovány do místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="d9bb2-130">Soubory prostředků, které jsou kompilovány do odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="d9bb2-131">Soubory prostředků, které jsou kompilovány do odkazující sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="d9bb2-132">Soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-132">Content files.</span></span>

- <span data-ttu-id="d9bb2-133">Lokalita zdroje souborů.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-133">Site of origin files.</span></span>

<span data-ttu-id="d9bb2-134">Pro přístup k tyto typy souborů, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje dva orgány: aplikace: / / / / / a siteoforigin: / / / / /.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="d9bb2-135">Aplikace: / / / / / autority identifikuje datové soubory aplikace, která jsou známá v době kompilace, včetně souborů prostředků a obsahu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="d9bb2-136">Siteoforigin: / / / / / autority identifikuje lokality původní soubory.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="d9bb2-137">Rozsah každé oprávnění je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-137">The scope of each authority is shown in the following figure.</span></span>

![Diagram identifikátoru URI balíčku](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="d9bb2-139">Komponenta autority sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je vložený [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který odkazuje na balíček a musí odpovídat specifikaci RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="d9bb2-140">Kromě toho musí být nahrazen znakem "," znak "/" a vyhrazené znaky, jako je například "%" a "?" musí být uvozeny řídicími znaky.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="d9bb2-141">Zobrazit OPC podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-141">See the OPC for details.</span></span>

<span data-ttu-id="d9bb2-142">Následující části popisují, jak vytvořit balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pomocí těchto dvou orgány ve spojení s příslušné cesty pro identifikaci prostředků, obsah a lokality původní soubory.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="d9bb2-143">Identifikátory URI prostředků soubor balíčku</span><span class="sxs-lookup"><span data-stu-id="d9bb2-143">Resource File Pack URIs</span></span>

<span data-ttu-id="d9bb2-144">Soubory prostředků, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` položek a jsou zkompilovány do sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="d9bb2-145">podporuje vytváření sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , který je možné určit soubory prostředků, které jsou kompilovány do místní sestavení nebo zkompilovány do sestavení, které se odkazuje z místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-145">supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="d9bb2-146">Soubor prostředků místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-146">Local Assembly Resource File</span></span>

<span data-ttu-id="d9bb2-147">Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředek soubor, který se zkompiluje do místní sestavení používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="d9bb2-148">**Autorita**: aplikace: / / / / /.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="d9bb2-149">**Cesta**: Název souboru prostředků, včetně jeho cesty vzhledem ke kořenové složce místní sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="d9bb2-150">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který se nachází v kořenové složce místní sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="d9bb2-151">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěný v podsložce složky místní sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="d9bb2-152">Soubor prostředků odkazovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="d9bb2-153">Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředek soubor, který se zkompiluje do odkazované sestavení používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="d9bb2-154">**Autorita**: aplikace: / / / / /.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="d9bb2-155">**Cesta**: Název zdrojového souboru, který se zkompiluje do odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="d9bb2-156">Cestou musí být v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="d9bb2-157">*AssemblyShortName*{ *; Verze*] { *; PublicKey*]; component /*cesta*</span><span class="sxs-lookup"><span data-stu-id="d9bb2-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="d9bb2-158">**AssemblyShortName**: krátký název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="d9bb2-159">**; Verze** [volitelný]: verze odkazovaného sestavení, která obsahuje soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="d9bb2-160">To se používá, když dva nebo víc odkazovaných sestavení se stejným názvem, short jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="d9bb2-161">**; PublicKey** [volitelný]: veřejný klíč, který se použil k podepsání odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="d9bb2-162">To se používá, když dva nebo víc odkazovaných sestavení se stejným názvem, short jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="d9bb2-163">**; součást**: Určuje, že se z místní sestavení odkazuje sestavení, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="d9bb2-164">**/ Cesta**: název souboru prostředků, včetně jeho cesty vzhledem ke kořenové složce projektu odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="d9bb2-165">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který se nachází v kořenové složce projektu odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="d9bb2-166">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěný v podsložce složky odkazované sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="d9bb2-167">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který se nachází v kořenové složce složky specifické pro verzi, odkazovaná sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="d9bb2-168">Všimněte si, že sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntaxe pro zdrojové soubory odkazované sestavení lze použít pouze s aplikací: / / / / / autoritu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="d9bb2-169">Například následující se nepodporuje v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="d9bb2-170">Identifikátory URI souboru balíčku obsahu</span><span class="sxs-lookup"><span data-stu-id="d9bb2-170">Content File Pack URIs</span></span>

<span data-ttu-id="d9bb2-171">Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor s obsahem používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="d9bb2-172">**Autorita**: aplikace: / / / / /.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="d9bb2-173">**Cesta**: Název souboru obsahu, včetně jeho cesty relativní k umístění systému souboru hlavního spustitelného sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="d9bb2-174">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu soubor umístěný ve stejné složce jako spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="d9bb2-175">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor obsahu, umístěné v podsložce, která je relativní vzhledem k sestavení spustitelného souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] <span data-ttu-id="d9bb2-176">Nelze nalézt soubory obsahu do.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-176">content files cannot be navigated to.</span></span> <span data-ttu-id="d9bb2-177">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schéma podporuje pouze navigaci na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] soubory, které jsou k dispozici na webovou stránku původu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="d9bb2-178">Lokality identifikátorů URI zdroje balíčku</span><span class="sxs-lookup"><span data-stu-id="d9bb2-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="d9bb2-179">Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ke stránce původu soubor používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="d9bb2-180">**Autorita**: siteoforigin: / / / / /.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="d9bb2-181">**Cesta**: Název lokality zdrojový soubor, včetně jeho cesty relativní k umístění, ze kterého byl spuštěn spustitelný soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="d9bb2-182">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality zdrojový soubor, uložené v umístění, ze kterého je spuštěn spustitelný soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="d9bb2-183">Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality původu souborů uložených ve podsložky, která je relativní vzhledem k umístění, ze kterého se spustí spustitelný soubor sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="d9bb2-184">Stránkovací soubory</span><span class="sxs-lookup"><span data-stu-id="d9bb2-184">Page Files</span></span>

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="d9bb2-185">soubory, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky jsou zkompilovány do sestavení stejným způsobem jako soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-185">files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="d9bb2-186">V důsledku toho [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky lze identifikovat pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>

<span data-ttu-id="d9bb2-187">Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které jsou běžně nakonfigurována jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky mají jeden z následujících jako jeho kořenový element:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="d9bb2-188">Absolutní vs. Identifikátory relativních Pack URI</span><span class="sxs-lookup"><span data-stu-id="d9bb2-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="d9bb2-189">Plně kvalifikovaný pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] obsahuje schéma, oprávnění a cesty, a bude považován za absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="d9bb2-190">Jako zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky obvykle umožňují nastavit příslušné atributy s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], který obsahuje pouze cestu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>

<span data-ttu-id="d9bb2-191">Představte si třeba následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] soubor prostředků v místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="d9bb2-192">Relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který odkazuje na tento prostředek soubor by.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="d9bb2-193">Protože lokality původu soubory nejsou přiřazeny k sestavení, se může odkazovat jenom na absolutní Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>

<span data-ttu-id="d9bb2-194">Ve výchozím nastavení, relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se považuje za relativní k umístění značek nebo kódu, který obsahuje odkaz na.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="d9bb2-195">Pokud se používá počáteční zpětné lomítko, ale relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkaz se považovat za kořeni aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="d9bb2-196">Zvažte například následující strukturu projektu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="d9bb2-197">Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , která odkazuje na *kořenové*\SubFolder\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`Page2.xaml`

<span data-ttu-id="d9bb2-198">Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , která odkazuje na *kořenové*\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="d9bb2-199">Identifikátor URI rozlišení Pack</span><span class="sxs-lookup"><span data-stu-id="d9bb2-199">Pack URI Resolution</span></span>

<span data-ttu-id="d9bb2-200">Formát balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] umožňuje pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro různé typy souborů, které vypadají stejně.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="d9bb2-201">Představte si třeba následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="d9bb2-202">Tento balíček absolutní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] může odkazovat na soubor prostředků v místní sestavení nebo souboru obsahu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="d9bb2-203">Totéž platí pro následující relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="d9bb2-204">Aby bylo možné určit typ souboru, který sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] řeší [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků v místní sestavení a soubory obsahu pomocí heuristiky následující:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="d9bb2-205">Metadata sestavení testu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut, který odpovídá této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

2. <span data-ttu-id="d9bb2-206">Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nenajde, cesta balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor s obsahem.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>

3. <span data-ttu-id="d9bb2-207">Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nebyl nalezen, testovat soubory sady prostředků, které jsou kompilovány do místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="d9bb2-208">Pokud soubor prostředků, která odpovídá cestu sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je najít cestu balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>

5. <span data-ttu-id="d9bb2-209">Pokud se prostředek nenajde, interně vytvořené <xref:System.Uri> je neplatný.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <span data-ttu-id="d9bb2-210">řešení se nedá použít pro [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které odkazují na následující:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-210">resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>

- <span data-ttu-id="d9bb2-211">Obsah souborů v odkazovaných sestaveních: Služba nepodporuje tyto typy souborů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="d9bb2-212">Vložené soubory v odkazovaných sestaveních: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] poznají, která jsou jedinečná, vzhledem k tomu, aby obsahovaly název odkazovaného sestavení a `;component` příponu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="d9bb2-213">Lokality původu souborů: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] poznají, které byly jedinečné, protože jsou pouze soubory, které lze identifikovat podle sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které obsahují siteoforigin: / / / / / autority.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="d9bb2-214">Jeden zápis, který pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení umožňuje, je pro kód je poněkud nezávislé na umístění prostředků a obsahu souborů.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="d9bb2-215">Například, pokud máte soubor prostředků v místním sestavení, které je překonfigurovat tak, aby se soubor s obsahem, sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředku zůstala stejná, stejně jako kód, který používá sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="d9bb2-216">Programování s identifikátory Pack URI</span><span class="sxs-lookup"><span data-stu-id="d9bb2-216">Programming with Pack URIs</span></span>

<span data-ttu-id="d9bb2-217">Mnoho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídy implementovat vlastnosti, které lze nastavit s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="d9bb2-218">Tyto vlastnosti můžete nastavit od značek a kódu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="d9bb2-219">Tato část ukazuje základní konstrukce pro oba a potom jsou uvedeny příklady běžným scénářům.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="d9bb2-220">Pomocí identifikátory Pack URI v kódu</span><span class="sxs-lookup"><span data-stu-id="d9bb2-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="d9bb2-221">Aktualizací Service pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je zadán v kódu tak, že nastavíte elementu atributu s balíčkem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="d9bb2-222">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="d9bb2-223">Tabulka 1 znázorňuje různé absolutní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="d9bb2-224">Tabulka 1: Absolutní Pack identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="d9bb2-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="d9bb2-225">Soubor</span><span class="sxs-lookup"><span data-stu-id="d9bb2-225">File</span></span>|<span data-ttu-id="d9bb2-226">Absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9bb2-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="d9bb2-227">Soubor prostředků – místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-228">Soubor prostředků v podsložce – místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-229">Soubor prostředků – odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-230">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-231">Soubor prostředků v verze odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-232">Soubor s obsahem</span><span class="sxs-lookup"><span data-stu-id="d9bb2-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="d9bb2-233">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="d9bb2-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="d9bb2-234">Lokality zdrojový soubor</span><span class="sxs-lookup"><span data-stu-id="d9bb2-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="d9bb2-235">Lokality zdrojový soubor v podsložce</span><span class="sxs-lookup"><span data-stu-id="d9bb2-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="d9bb2-236">Tabulka 2 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="d9bb2-237">Tabulka 2: Balíček relativní identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="d9bb2-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="d9bb2-238">Soubor</span><span class="sxs-lookup"><span data-stu-id="d9bb2-238">File</span></span>|<span data-ttu-id="d9bb2-239">Relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9bb2-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="d9bb2-240">Soubor prostředků v místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-241">Soubor prostředků v podsložce místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-242">Soubor prostředků v odkazovaném sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-243">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="d9bb2-244">Soubor s obsahem</span><span class="sxs-lookup"><span data-stu-id="d9bb2-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="d9bb2-245">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="d9bb2-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="d9bb2-246">Použití identifikátory Pack URI v kódu</span><span class="sxs-lookup"><span data-stu-id="d9bb2-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="d9bb2-247">Zadejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] v kódu po vytvoření instance <xref:System.Uri> třídy a předáním této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="d9bb2-248">To je patrné z následujícího příkladu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="d9bb2-249">Ve výchozím nastavení <xref:System.Uri> třídy bere v úvahu pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] být absolutní.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="d9bb2-250">V důsledku toho je vyvolána výjimka, pokud instance <xref:System.Uri> třída se vytvoří s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9bb2-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="d9bb2-251">Naštěstí <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> přetížení <xref:System.Uri> konstruktoru třídy přijímá parametr typu <xref:System.UriKind> aby bylo možné určit, zda sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="d9bb2-252">Měli byste zadat jenom <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative> když jste si jisti, že zadaný balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="d9bb2-253">Pokud neznáte typ sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který se používá, například když uživatel zadá sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] v době běhu použít <xref:System.UriKind.RelativeOrAbsolute> místo.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="d9bb2-254">Tabulka 3 znázorňuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu s použitím <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d9bb2-255">Tabulka 3: Absolutní Pack identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="d9bb2-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="d9bb2-256">Soubor</span><span class="sxs-lookup"><span data-stu-id="d9bb2-256">File</span></span>|<span data-ttu-id="d9bb2-257">Absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9bb2-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="d9bb2-258">Soubor prostředků – místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-259">Soubor prostředků v podsložce – místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-260">Soubor prostředků – odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-261">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-262">Soubor prostředků v verze odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-263">Soubor s obsahem</span><span class="sxs-lookup"><span data-stu-id="d9bb2-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-264">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="d9bb2-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-265">Lokality zdrojový soubor</span><span class="sxs-lookup"><span data-stu-id="d9bb2-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="d9bb2-266">Lokality zdrojový soubor v podsložce</span><span class="sxs-lookup"><span data-stu-id="d9bb2-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="d9bb2-267">Tabulka 4 znázorňuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d9bb2-268">Tabulka 4: Balíček relativní identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="d9bb2-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="d9bb2-269">Soubor</span><span class="sxs-lookup"><span data-stu-id="d9bb2-269">File</span></span>|<span data-ttu-id="d9bb2-270">Relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9bb2-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="d9bb2-271">Soubor prostředků – místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="d9bb2-272">Soubor prostředků v podsložce – místní sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="d9bb2-273">Soubor prostředků – odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="d9bb2-274">Soubor prostředků v podsložce - odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="d9bb2-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="d9bb2-275">Soubor s obsahem</span><span class="sxs-lookup"><span data-stu-id="d9bb2-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="d9bb2-276">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="d9bb2-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="d9bb2-277">Běžné scénáře identifikátoru URI balíčku</span><span class="sxs-lookup"><span data-stu-id="d9bb2-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="d9bb2-278">V předchozích částech projednat tom, jak vytvořit balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro identifikaci prostředků, obsah a lokality původní soubory.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="d9bb2-279">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], tyto konstrukce se používají v mnoha různými způsoby, a následující části se věnují několika běžných použití.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="d9bb2-280">Určení uživatelské rozhraní k zobrazení při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="d9bb2-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="d9bb2-281"><xref:System.Windows.Application.StartupUri%2A> Určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zobrazíte, když [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="d9bb2-282">Pro samostatné aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být okno, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="d9bb2-283">Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] můžete také určit stránku jako počáteční uživatelského rozhraní, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="d9bb2-284">Pokud aplikace je samostatná aplikace, a stránka není zadán s <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otevře <xref:System.Windows.Navigation.NavigationWindow> hostovat na stránce.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="d9bb2-285">Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], stránka se zobrazí v prohlížeči hostitele.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="d9bb2-286">Přejděte na stránku</span><span class="sxs-lookup"><span data-stu-id="d9bb2-286">Navigating to a Page</span></span>

<span data-ttu-id="d9bb2-287">Následující příklad ukazuje, jak přejít na stránku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="d9bb2-288">Další informace o různých způsobů, jak procházet v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], naleznete v tématu [Přehled navigace](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="d9bb2-289">Určení ikonu okna.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-289">Specifying a Window Icon</span></span>

<span data-ttu-id="d9bb2-290">Následující příklad ukazuje, jak pomocí identifikátoru URI můžete určit ikonu okna.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="d9bb2-291">Další informace naleznete v tématu <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="d9bb2-292">Načítají se obrázek, zvuk a Video soubory</span><span class="sxs-lookup"><span data-stu-id="d9bb2-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="d9bb2-293">umožňuje aplikacím používat celou řadu typů médií, které můžete identifikovat a načítají s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="d9bb2-294">Další informace o práci s mediálního obsahu, najdete v části [grafika a multimédia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="d9bb2-295">Načítání z umístění původních slovník prostředků</span><span class="sxs-lookup"><span data-stu-id="d9bb2-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="d9bb2-296">Slovníky sloučených prostředků (<xref:System.Windows.ResourceDictionary>) lze použít pro podporu motivů aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="d9bb2-297">Jeden způsob, jak vytvářet a spravovat motivy, je vytvořit víc motivů jako slovníky prostředků, které jsou umístěné v lokalitě aplikace původu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="d9bb2-298">To umožňuje motivy, které chcete přidat a aktualizovat bez nutnosti opětovné kompilace a opětovné nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="d9bb2-299">Tyto slovníky prostředků je možné identifikovat a načíst pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], která je uvedena v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="d9bb2-300">Přehled motivy obsažené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], naleznete v tématu [styly a šablony](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9bb2-301">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-301">See also</span></span>

- [<span data-ttu-id="d9bb2-302">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="d9bb2-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
