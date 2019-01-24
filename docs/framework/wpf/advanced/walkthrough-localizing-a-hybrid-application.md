---
title: 'Průvodce: Lokalizace hybridní aplikace'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 3d658d0dfb07a636a7338c69cae93b7e8a54383e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613867"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="ce757-102">Průvodce: Lokalizace hybridní aplikace</span><span class="sxs-lookup"><span data-stu-id="ce757-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="ce757-103">Tento návod ukazuje, jak lokalizovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvků v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– hybridní aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce757-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>

<span data-ttu-id="ce757-104">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="ce757-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="ce757-105">Vytváří [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu hostitel.</span><span class="sxs-lookup"><span data-stu-id="ce757-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>

-   <span data-ttu-id="ce757-106">Přidání lokalizovatelné obsahu.</span><span class="sxs-lookup"><span data-stu-id="ce757-106">Adding localizable content.</span></span>

-   <span data-ttu-id="ce757-107">Povoluje se lokalizace.</span><span class="sxs-lookup"><span data-stu-id="ce757-107">Enabling localization.</span></span>

-   <span data-ttu-id="ce757-108">Přiřazení identifikátory prostředků.</span><span class="sxs-lookup"><span data-stu-id="ce757-108">Assigning resource identifiers.</span></span>

-   <span data-ttu-id="ce757-109">Chcete-li vytvořit satelitní sestavení pomocí locbaml – nástroj.</span><span class="sxs-lookup"><span data-stu-id="ce757-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="ce757-110">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [lokalizace ukázkové aplikace hybridní](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="ce757-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="ce757-111">Až skončíte, bude mít lokalizované hybridní aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce757-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce757-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce757-112">Prerequisites</span></span>

<span data-ttu-id="ce757-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="ce757-113">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="ce757-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ce757-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="ce757-115">Vytvoření projektu Windows Forms hostitele</span><span class="sxs-lookup"><span data-stu-id="ce757-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="ce757-116">Prvním krokem je vytvoření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace projekt a přidejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu s obsahem, který bude lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="ce757-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="ce757-117">Chcete-li vytvořit projekt hostitele</span><span class="sxs-lookup"><span data-stu-id="ce757-117">To create the host project</span></span>

1.  <span data-ttu-id="ce757-118">Vytvoření **aplikace WPF** projekt s názvem `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="ce757-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="ce757-119">(**Souboru** > **nové** > **projektu** > **Visual C#** nebo **jazyka Visual Basic**   >  **Klasický desktopový** > **aplikace WPF**).</span><span class="sxs-lookup"><span data-stu-id="ce757-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2.  <span data-ttu-id="ce757-120">Přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> prvek s názvem `SimpleControl` do projektu.</span><span class="sxs-lookup"><span data-stu-id="ce757-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3.  <span data-ttu-id="ce757-121">Použití <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek umístit `SimpleControl` prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ce757-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="ce757-122">Další informace najdete v tématu [názorný postup: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ce757-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="ce757-123">Přidání lokalizovatelné obsahu</span><span class="sxs-lookup"><span data-stu-id="ce757-123">Adding Localizable Content</span></span>

<span data-ttu-id="ce757-124">V dalším kroku přidáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacímu prvku popisek a nastavte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentace obsahu elementu do zdrojů lokalizovatelných řetězců.</span><span class="sxs-lookup"><span data-stu-id="ce757-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="ce757-125">Chcete-li přidat lokalizovatelné obsahu</span><span class="sxs-lookup"><span data-stu-id="ce757-125">To add localizable content</span></span>

1.  <span data-ttu-id="ce757-126">V **Průzkumníka řešení**, dvakrát klikněte na panel **SimpleControl.xaml** a otevřete tak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce757-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2.  <span data-ttu-id="ce757-127">Nastavení obsahu prvku <xref:System.Windows.Controls.Button> řídit pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="ce757-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3.  <span data-ttu-id="ce757-128">V **Průzkumníka řešení**, dvakrát klikněte na panel **Form1** ho otevřete v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ce757-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4.  <span data-ttu-id="ce757-129">Otevřít **nástrojů** a dvakrát klikněte na panel **popisek** přidání ovládacího prvku popisek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ce757-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="ce757-130">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="ce757-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5.  <span data-ttu-id="ce757-131">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ce757-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="ce757-132">Oba `SimpleControl` elementu a ovládací prvek popisku se zobrazí text **"Hello"**.</span><span class="sxs-lookup"><span data-stu-id="ce757-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="ce757-133">Povoluje se lokalizace</span><span class="sxs-lookup"><span data-stu-id="ce757-133">Enabling Localization</span></span>

<span data-ttu-id="ce757-134">Návrhář formulářů Windows poskytuje nastavení pro povolení lokalizace v satelitním sestavení.</span><span class="sxs-lookup"><span data-stu-id="ce757-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="ce757-135">Chcete-li povolit lokalizaci</span><span class="sxs-lookup"><span data-stu-id="ce757-135">To enable localization</span></span>

1.  <span data-ttu-id="ce757-136">V **Průzkumníka řešení**, dvakrát klikněte na panel **Form1.cs** ho otevřete v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ce757-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2.  <span data-ttu-id="ce757-137">V **vlastnosti** okno, nastavte hodnotu vlastnosti formuláře **Localizable** vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="ce757-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3.  <span data-ttu-id="ce757-138">V **vlastnosti** okno, nastavte hodnotu **jazyk** vlastnost **Španělština (Španělsko)**.</span><span class="sxs-lookup"><span data-stu-id="ce757-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4.  <span data-ttu-id="ce757-139">V Návrháři formulářů Windows vyberte ovládací prvek popisku.</span><span class="sxs-lookup"><span data-stu-id="ce757-139">In the Windows Forms Designer, select the label control.</span></span>

5.  <span data-ttu-id="ce757-140">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="ce757-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="ce757-141">Do projektu se přidá nový soubor prostředků s názvem Form1.es ES.resx.</span><span class="sxs-lookup"><span data-stu-id="ce757-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6.  <span data-ttu-id="ce757-142">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.cs** a klikněte na tlačítko **zobrazit kód** ho otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ce757-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7.  <span data-ttu-id="ce757-143">Zkopírujte následující kód do `Form1` konstruktoru, předchozí volání `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="ce757-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8.  <span data-ttu-id="ce757-144">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="ce757-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="ce757-145">Název projektu je označené jako **(není k dispozici)**.</span><span class="sxs-lookup"><span data-stu-id="ce757-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="ce757-146">Klikněte pravým tlačítkem na **LocalizingWpfInWf**a klikněte na tlačítko **upravit LocalizingWpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="ce757-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="ce757-147">Soubor projektu se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ce757-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="ce757-148">Zkopírujte následující řádek do první `PropertyGroup` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ce757-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="ce757-149">Uložte soubor projektu a zavřete ho.</span><span class="sxs-lookup"><span data-stu-id="ce757-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="ce757-150">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **znovu načíst projekt**.</span><span class="sxs-lookup"><span data-stu-id="ce757-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="ce757-151">Přiřazuje se identifikátory prostředků</span><span class="sxs-lookup"><span data-stu-id="ce757-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="ce757-152">Můžete namapovat lokalizovatelné obsah sestavení prostředků s použitím identifikátory prostředků.</span><span class="sxs-lookup"><span data-stu-id="ce757-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="ce757-153">Při zadávání MsBuild.exe aplikace automaticky přiřadí identifikátory prostředků `updateuid` možnost.</span><span class="sxs-lookup"><span data-stu-id="ce757-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="ce757-154">K přiřazení identifikátory prostředků</span><span class="sxs-lookup"><span data-stu-id="ce757-154">To assign resource identifiers</span></span>

1.  <span data-ttu-id="ce757-155">Z nabídky Start otevřete Developer Command Prompt pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ce757-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2.  <span data-ttu-id="ce757-156">Použijte následující příkaz k přiřazení identifikátory prostředků lokalizovatelných obsah.</span><span class="sxs-lookup"><span data-stu-id="ce757-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3.  <span data-ttu-id="ce757-157">V **Průzkumníka řešení**, dvakrát klikněte na panel **SimpleControl.xaml** ho otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ce757-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="ce757-158">Uvidíte, že `msbuild` příkaz má přidat `Uid` atribut na všechny prvky.</span><span class="sxs-lookup"><span data-stu-id="ce757-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="ce757-159">To usnadňuje lokalizaci prostřednictvím přiřazení identifikátory prostředků.</span><span class="sxs-lookup"><span data-stu-id="ce757-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4.  <span data-ttu-id="ce757-160">Stisknutím klávesy **F6** k sestavení řešení.</span><span class="sxs-lookup"><span data-stu-id="ce757-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="ce757-161">Pomocí locbaml – Chcete-li vytvořit satelitní sestavení</span><span class="sxs-lookup"><span data-stu-id="ce757-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="ce757-162">Lokalizovaný obsah uložený v pouze prostředky *satelitní sestavení*.</span><span class="sxs-lookup"><span data-stu-id="ce757-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="ce757-163">Pomocí nástroje příkazového řádku LocBaml.exe k vytvoření lokalizovaných sestavení pro vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="ce757-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="ce757-164">Chcete-li vytvořit satelitní sestavení</span><span class="sxs-lookup"><span data-stu-id="ce757-164">To produce a satellite assembly</span></span>

1.  <span data-ttu-id="ce757-165">Zkopírujte do složky vašeho projektu obj\Debug LocBaml.exe.</span><span class="sxs-lookup"><span data-stu-id="ce757-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="ce757-166">Další informace najdete v tématu [lokalizace aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="ce757-166">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>

2.  <span data-ttu-id="ce757-167">V okně příkazového řádku použijte následující příkaz k extrakci zdrojové řetězce do dočasného souboru.</span><span class="sxs-lookup"><span data-stu-id="ce757-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3.  <span data-ttu-id="ce757-168">Otevřete soubor temp.csv pomocí sady Visual Studio nebo jiného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="ce757-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="ce757-169">Nahraďte řetězec `"Hello"` spolu s překladem Španělština `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="ce757-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4.  <span data-ttu-id="ce757-170">Uložte soubor temp.csv.</span><span class="sxs-lookup"><span data-stu-id="ce757-170">Save the temp.csv file.</span></span>

5.  <span data-ttu-id="ce757-171">Použijte následující příkaz k vygenerování lokalizované soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="ce757-171">Use the following command to generate the localized resource file.</span></span>

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="ce757-172">Soubor LocalizingWpfInWf.g.es ES.resources se vytvoří ve složce obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="ce757-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6.  <span data-ttu-id="ce757-173">Použijte následující příkaz k vytvoření lokalizované satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="ce757-173">Use the following command to build the localized satellite assembly.</span></span>

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="ce757-174">Soubor LocalizingWpfInWf.resources.dll se vytvoří ve složce obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="ce757-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7.  <span data-ttu-id="ce757-175">Zkopírujte soubor LocalizingWpfInWf.resources.dll do složky projektu bin\Debug\es-ES.</span><span class="sxs-lookup"><span data-stu-id="ce757-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="ce757-176">Nahraďte existující soubor.</span><span class="sxs-lookup"><span data-stu-id="ce757-176">Replace the existing file.</span></span>

8.  <span data-ttu-id="ce757-177">Spusťte LocalizingWpfInWf.exe, který je umístěn ve složce bin\Debug vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="ce757-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="ce757-178">Znovu sestavit aplikaci nebo do satelitního sestavení se přepíšou.</span><span class="sxs-lookup"><span data-stu-id="ce757-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="ce757-179">Aplikace se zobrazí lokalizované řetězce místo anglické řetězce.</span><span class="sxs-lookup"><span data-stu-id="ce757-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce757-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce757-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="ce757-181">Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="ce757-181">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
- [<span data-ttu-id="ce757-182">Návod: Lokalizace formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="ce757-182">Walkthrough: Localizing Windows Forms</span></span>](https://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)
- [<span data-ttu-id="ce757-183">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ce757-183">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
