---
title: Nástroj pro analýzu sestavení (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6851ac334d439f2e5c0f6056f5226e3faa1503d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872336"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="6f4a3-102">Nástroj pro analýzu sestavení (Mefx)</span><span class="sxs-lookup"><span data-stu-id="6f4a3-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="6f4a3-103">Nástroj pro analýzu sestavení (Mefx) je aplikace příkazového řádku, která analyzuje knihovny (.dll) a soubory aplikace (.exe) obsahující části Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="6f4a3-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="6f4a3-104">Primárním účelem Mefx je vývojářům poskytuje způsob, jak Diagnostika selhání sestavení ve svých aplikacích MEF bez nutnosti přidat kód náročné trasování do vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="6f4a3-105">Může být také užitečné porozumět částí z knihovny poskytované třetích stran.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="6f4a3-106">Toto téma popisuje způsob použití Mefx a poskytuje odkaz pro její syntaxe.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="6f4a3-107">Získávání Mefx</span><span class="sxs-lookup"><span data-stu-id="6f4a3-107">Getting Mefx</span></span>  
 <span data-ttu-id="6f4a3-108">Je k dispozici na Githubu v Mefx [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="6f4a3-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="6f4a3-109">Jednoduše stáhněte a rozbalte nástroj.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="6f4a3-110">Základní syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f4a3-110">Basic Syntax</span></span>  
 <span data-ttu-id="6f4a3-111">Mefx vyvolat pomocí příkazového řádku v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="6f4a3-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="6f4a3-112">První sadu argumentů určit soubory a adresáře, ze kterého se má načíst součásti pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="6f4a3-113">Zadejte soubor s `/file:` přepínače a adresář se `/directory:` přepnout.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="6f4a3-114">Můžete zadat více souborů či adresářů, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6f4a3-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  <span data-ttu-id="6f4a3-115">Každý .dll nebo .exe by měla načíst pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="6f4a3-116">Pokud je soubor načten více než jednou, nástroj může vrátit nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="6f4a3-117">Po seznam souborů a adresářů je nutné zadat příkazu a možnosti pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="6f4a3-118">Výpis dostupných částí</span><span class="sxs-lookup"><span data-stu-id="6f4a3-118">Listing Available Parts</span></span>  
 <span data-ttu-id="6f4a3-119">Použití `/parts` akci vypsat všechny součásti deklarované v souborech načíst.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="6f4a3-120">Výsledkem je jednoduchý seznam názvů část.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-120">The result is a simple list of part names.</span></span>  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="6f4a3-121">Další informace o součástech, použijte `/verbose` možnost.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="6f4a3-122">To bude výstupní Další informace o všech dostupných částí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-122">This will output more information for all available parts.</span></span> <span data-ttu-id="6f4a3-123">Chcete-li získat další informace o jedné součásti, použijte `/type` akce místo `/parts`.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="6f4a3-124">Výpis importy a exporty</span><span class="sxs-lookup"><span data-stu-id="6f4a3-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="6f4a3-125">`/imports` a `/exports` akce zobrazí seznam všechny importované části a všechny exportované části, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="6f4a3-126">Můžete také zařadit části, které importovat nebo exportovat pomocí určitého typu `/importers` nebo `/exporters` akce.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="6f4a3-127">Můžete také použít `/verbose` možnost tyto akce.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="6f4a3-128">Zjištění odmítl částí</span><span class="sxs-lookup"><span data-stu-id="6f4a3-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="6f4a3-129">Po jeho načtení dostupných částí, používá Mefx Kompoziční modul rozhraní MEF k vytvořte z nich.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="6f4a3-130">Části, které nemohou být složené úspěšně jsou označovány jako *odmítl*.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="6f4a3-131">K zobrazení seznamu všechny odmítnuté části, použijte `/rejected` akce.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="6f4a3-132">Můžete použít `/verbose` spolu s možností `/rejected` akce k vytištění podrobné informace o odmítl částí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="6f4a3-133">V následujícím příkladu `ClassLibrary1` obsahuje knihovny DLL `AddIn` část, která importuje `MemberPart` a `ChainOne` částí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="6f4a3-134">`ChainOne` Importuje `ChainTwo`, ale `ChainTwo` neexistuje.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="6f4a3-135">To znamená, že `ChainOne` byl odmítnut, které způsobí, že `AddIn` zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="6f4a3-136">Následuje úplný výstup z předchozího příkazu:</span><span class="sxs-lookup"><span data-stu-id="6f4a3-136">The following shows the complete output of the previous command:</span></span>  
  
```  
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="6f4a3-137">Zajímavé informace jsou součástí `[Exception]` a `[Unsuitable]` výsledky.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="6f4a3-138">`[Exception]` Výsledek obsahuje informace o proč byla odmítnuta část.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="6f4a3-139">`[Unsuitable]` Výsledek vyplývá, proč nelze použít jako součást jinak odpovídající tak, aby vyplnil importu, v tomto případě protože tuto část byl sám odmítnutých pro chybějící importuje.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="6f4a3-140">Analýza primární způsobí, že</span><span class="sxs-lookup"><span data-stu-id="6f4a3-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="6f4a3-141">Pokud několik částí jsou propojeny v řetězec dlouhý závislostí, může způsobit problém zahrnující část dole celý řetěz zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="6f4a3-142">Diagnostika těchto problémů může být obtížné, protože hlavní příčinu selhání není vždy zřejmé.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="6f4a3-143">Chcete-li pomoci s problémem, který můžete použít `/causes` akce, která se pokusí najít původní příčinu možných žádné kaskádové zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="6f4a3-144">Použití `/causes` akce v předchozím příkladu by zobrazila seznam pouze informace o `ChainOne`, jehož nevyplněným import je hlavní příčinou zamítnutí `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="6f4a3-145">`/causes` Akce lze použít v obou normální a `/verbose` možnosti.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f4a3-146">Ve většině případů budou moci diagnostikovat původní příčinu selhání kaskádové Mefx.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="6f4a3-147">Ale v případech, kde částí se prostřednictvím kódu programu do kontejneru přidá, případech hierarchické kontejnery nebo případech vlastní `ExportProvider` implementacích Mefx nebude možné určování příčin problémů.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="6f4a3-148">Obecně platí, výše popsaných případech mělo by se vyhnout tam, kde je to možné, jsou obecně obtížné diagnostikovat selhání.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="6f4a3-149">Bílý list</span><span class="sxs-lookup"><span data-stu-id="6f4a3-149">White Lists</span></span>  
 <span data-ttu-id="6f4a3-150">`/whitelist` Možnost umožňuje zadat textový soubor, který obsahuje části, které se očekává zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="6f4a3-151">Neočekávané zamítnutí pak mají označit příznakem.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="6f4a3-152">To může být užitečné při analýze neúplné knihovny nebo dílčí knihovnu, která chybí některé závislosti.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="6f4a3-153">`/whitelist` Možnost lze použít pouze k `/rejected` nebo `/causes` akce.</span><span class="sxs-lookup"><span data-stu-id="6f4a3-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="6f4a3-154">Vezměte v úvahu soubor s názvem test.txt, který obsahuje text "ClassLibrary1.ChainOne".</span><span class="sxs-lookup"><span data-stu-id="6f4a3-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="6f4a3-155">Pokud spustíte `/rejected` akce s `/whitelist` možnost v předchozím příkladu, vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6f4a3-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
