---
title: Povolení nebo zakázání přesměrování vazby automaticky generované
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: f646445d5fa4556646700bb5daf8ac859631da2c
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083657"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="a7b53-102">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="a7b53-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="a7b53-103">Při sestavování aplikací v sadě Visual Studio, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novější verze, přesměrování vazby může automaticky přidá do konfiguračního souboru aplikace pro přepsání sjednocení sestavení.</span><span class="sxs-lookup"><span data-stu-id="a7b53-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="a7b53-104">Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a7b53-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="a7b53-105">Funkce automatického přesměrování vazby ovlivňuje aplikace klasické pracovní plochy a webové aplikace, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] nebo novější verze, ačkoli chování se mírně liší pro webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a7b53-105">The automatic binding redirection feature affects desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="a7b53-106">Pokud máte existující aplikace, které předchozí verze cílového rozhraní .NET Framework, nebo tuto funkci můžete zakázat, pokud chcete ručně vytvořit přesměrování vazby, můžete povolit automatické přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="a7b53-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="a7b53-107">Zakázat automatické přesměrování vazby v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="a7b53-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="a7b53-108">Automatické přesměrování vazeb je povoleno standardně pro aplikace klasické pracovní plochy Windows, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="a7b53-108">Automatic binding redirects are enabled by default for Windows desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="a7b53-109">Přesměrování vazby jsou přidána do konfigurace výstup (**app.config**) soubor při kompilaci aplikace a přepsání sjednocení sestavení, které jinak může probíhat.</span><span class="sxs-lookup"><span data-stu-id="a7b53-109">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="a7b53-110">Zdroj **app.config** soubor nezměnil.</span><span class="sxs-lookup"><span data-stu-id="a7b53-110">The source **app.config** file is not modified.</span></span> <span data-ttu-id="a7b53-111">Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci nebo zrušením výběru zaškrtávací políčko ve vlastnostech projektu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a7b53-111">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="a7b53-112">Zakázat prostřednictvím vlastnosti projektu</span><span class="sxs-lookup"><span data-stu-id="a7b53-112">Disable through project properties</span></span>

<span data-ttu-id="a7b53-113">Pokud máte Visual Studio 2017 verze 15.7 nebo novější, můžete snadno zakázat automaticky generované přesměrování vazby na stránkách vlastností projektu.</span><span class="sxs-lookup"><span data-stu-id="a7b53-113">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="a7b53-114">Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a7b53-114">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="a7b53-115">Na **aplikace** stránce, zrušte zaškrtnutí políčka **automaticky generovat přesměrování vazeb** možnost.</span><span class="sxs-lookup"><span data-stu-id="a7b53-115">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="a7b53-116">Stisknutím klávesy **Ctrl**+**S** uložte změnu.</span><span class="sxs-lookup"><span data-stu-id="a7b53-116">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="a7b53-117">Zakázat ručně v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="a7b53-117">Disable manually in the project file</span></span>

1. <span data-ttu-id="a7b53-118">Otevřete soubor projektu s možností úprav pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="a7b53-118">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="a7b53-119">V sadě Visual Studio vyberte projekt v **Průzkumníka řešení**a klikněte na tlačítko **otevřít složku v Průzkumníku souborů** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="a7b53-119">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="a7b53-120">V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="a7b53-120">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="a7b53-121">V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="a7b53-121">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="a7b53-122">Znovu klikněte pravým tlačítkem na projekt uvolněn a klikněte na tlačítko **upravit [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="a7b53-122">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="a7b53-123">V souboru projektu vyhledejte položku následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a7b53-123">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="a7b53-124">Změna `true` k `false`:</span><span class="sxs-lookup"><span data-stu-id="a7b53-124">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="a7b53-125">Ručně povolte automatické přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="a7b53-125">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="a7b53-126">Můžete povolit automatické přesměrování vazby v existujících aplikacích, které starší verze cílového rozhraní .NET Framework, nebo v případech, kde se zobrazí výzva k automaticky přidat přesměrování.</span><span class="sxs-lookup"><span data-stu-id="a7b53-126">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="a7b53-127">Pokud cílíte novější verzi rozhraní framework, ale se mi výzva automaticky přidat přesměrování, zobrazí se pravděpodobně výstup sestavení, který naznačuje, že přemapování sestavení.</span><span class="sxs-lookup"><span data-stu-id="a7b53-127">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="a7b53-128">Otevřete soubor projektu s možností úprav pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="a7b53-128">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="a7b53-129">V sadě Visual Studio vyberte projekt v **Průzkumníka řešení**a klikněte na tlačítko **otevřít složku v Průzkumníku souborů** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="a7b53-129">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="a7b53-130">V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="a7b53-130">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="a7b53-131">V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="a7b53-131">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="a7b53-132">Znovu klikněte pravým tlačítkem na projekt uvolněn a klikněte na tlačítko **upravit [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="a7b53-132">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="a7b53-133">Přidejte následující element do první skupiny vlastností konfigurace (pod \<PropertyGroup > značky):</span><span class="sxs-lookup"><span data-stu-id="a7b53-133">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="a7b53-134">Následuje příklad souboru projektu v prvku vložen:</span><span class="sxs-lookup"><span data-stu-id="a7b53-134">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="a7b53-135">Zkompilujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a7b53-135">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="a7b53-136">Povolit automatické přesměrování vazby ve službě web apps</span><span class="sxs-lookup"><span data-stu-id="a7b53-136">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="a7b53-137">Automatické přesměrování vazby je pro webové aplikace implementováno jinak.</span><span class="sxs-lookup"><span data-stu-id="a7b53-137">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="a7b53-138">Protože konfigurace zdroje (**web.config**) pro webové aplikace musí být změněn soubor, přesměrování vazeb nejsou automaticky přidáni do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a7b53-138">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="a7b53-139">Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit.</span><span class="sxs-lookup"><span data-stu-id="a7b53-139">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="a7b53-140">Protože vždy zobrazí výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a7b53-140">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="a7b53-141">Chcete-li přidat přesměrování vazby na **web.config** souboru:</span><span class="sxs-lookup"><span data-stu-id="a7b53-141">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="a7b53-142">V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.</span><span class="sxs-lookup"><span data-stu-id="a7b53-142">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="a7b53-143">![Vytváření upozornění pro sestavení odkazu konflikty](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="a7b53-143">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="a7b53-144">Pokud existují konflikty vazeb sestavení, zobrazí se upozornění.</span><span class="sxs-lookup"><span data-stu-id="a7b53-144">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="a7b53-145">Dvakrát klikněte na upozornění, nebo vyberte upozornění a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a7b53-145">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="a7b53-146">Dialogové okno, které umožňuje automaticky přidat nezbytná vazbu přesměruje do zdroje **web.config** soubor se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a7b53-146">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="a7b53-147">![Dialogové okno oprávnění přesměrování vazby](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="a7b53-147">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="a7b53-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7b53-148">See also</span></span>

- [<span data-ttu-id="a7b53-149">\<bindingRedirect> Element</span><span class="sxs-lookup"><span data-stu-id="a7b53-149">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="a7b53-150">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="a7b53-150">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
