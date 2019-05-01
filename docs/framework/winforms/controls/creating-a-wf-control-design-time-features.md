---
title: 'Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
ms.openlocfilehash: 70cd08a9d7d03cec4e946d2acb806dbecfe774f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011555"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a><span data-ttu-id="4621d-102">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="4621d-102">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>

<span data-ttu-id="4621d-103">Možnosti času návrhu pro vlastní ovládací prvek může taková instalace vylepšit pro vytváření přidružený vlastní designer.</span><span class="sxs-lookup"><span data-stu-id="4621d-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="4621d-104">Tento návod ukazuje, jak vytvořit vlastního návrháře pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4621d-104">This walkthrough illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="4621d-105">Budete implementovat `MarqueeControl` typu a přidružené návrháře třídy, nazvané `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="4621d-105">You will implement a `MarqueeControl` type and an associated designer class, called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="4621d-106">`MarqueeControl` Typ implementuje podobný výběr celé obrazovky, s animovaný světla a blikající text zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4621d-106">The `MarqueeControl` type implements a display similar to a theater marquee, with animated lights and flashing text.</span></span>

<span data-ttu-id="4621d-107">Návrhář pro tento ovládací prvek komunikuje s prostředím návrhu poskytnout vlastní možnosti času návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="4621d-108">Vlastní návrháři, můžete sestavit vlastní `MarqueeControl` implementaci animovaný světla a blikající text v mnoha kombinace.</span><span class="sxs-lookup"><span data-stu-id="4621d-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="4621d-109">Můžete použít deskách ovládací prvek ve formuláři jako jakýkoli jiný ovládací prvek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4621d-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="4621d-110">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="4621d-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="4621d-111">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="4621d-111">Creating the Project</span></span>

- <span data-ttu-id="4621d-112">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="4621d-112">Creating a Control Library Project</span></span>

- <span data-ttu-id="4621d-113">Odkazování na projekt vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-113">Referencing the Custom Control Project</span></span>

- <span data-ttu-id="4621d-114">Definování vlastního ovládacího prvku a jeho vlastní návrháři</span><span class="sxs-lookup"><span data-stu-id="4621d-114">Defining a Custom Control and Its Custom Designer</span></span>

- <span data-ttu-id="4621d-115">Vytvoření Instance vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-115">Creating an Instance of Your Custom Control</span></span>

- <span data-ttu-id="4621d-116">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="4621d-116">Setting Up the Project for Design-Time Debugging</span></span>

- <span data-ttu-id="4621d-117">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-117">Implementing Your Custom Control</span></span>

- <span data-ttu-id="4621d-118">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4621d-118">Creating a Child Control for Your Custom Control</span></span>

- <span data-ttu-id="4621d-119">Vytvoření MarqueeBorder podřízený ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4621d-119">Create the MarqueeBorder Child Control</span></span>

- <span data-ttu-id="4621d-120">Vytvoření vlastního návrháře a stínové vlastnosti filtru</span><span class="sxs-lookup"><span data-stu-id="4621d-120">Creating a Custom Designer to Shadow and Filter Properties</span></span>

- <span data-ttu-id="4621d-121">Zpracování změny součásti</span><span class="sxs-lookup"><span data-stu-id="4621d-121">Handling Component Changes</span></span>

- <span data-ttu-id="4621d-122">Příkazy návrháře přidání do vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="4621d-122">Adding Designer Verbs to your Custom Designer</span></span>

- <span data-ttu-id="4621d-123">Vytvoření vlastního editoru UITypeEditor.</span><span class="sxs-lookup"><span data-stu-id="4621d-123">Creating a Custom UITypeEditor</span></span>

- <span data-ttu-id="4621d-124">Testování vlastní ovládací prvek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="4621d-124">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="4621d-125">Až budete hotovi, vaše vlastní ovládací prvek bude vypadat podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="4621d-125">When you are finished, your custom control will look something like the following:</span></span>

<span data-ttu-id="4621d-126">![Možné uspořádání typu MarqueeControl](./media/demomarqueecontrol.gif "DemoMarqueeControl")</span><span class="sxs-lookup"><span data-stu-id="4621d-126">![A possible MarqueeControl arrangement](./media/demomarqueecontrol.gif "DemoMarqueeControl")</span></span>

<span data-ttu-id="4621d-127">Výpis úplného kódu naleznete v tématu [jak: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4621d-127">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

> [!NOTE]
> <span data-ttu-id="4621d-128">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="4621d-128">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4621d-129">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="4621d-129">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4621d-130">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="4621d-130">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4621d-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4621d-131">Prerequisites</span></span>

<span data-ttu-id="4621d-132">K dokončení tohoto návodu budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="4621d-132">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="4621d-133">Dostatečná oprávnění k vytvoření a spuštění projektů aplikace Windows Forms v počítači nainstalovanou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4621d-133">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="4621d-134">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="4621d-134">Creating the Project</span></span>

<span data-ttu-id="4621d-135">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4621d-135">The first step is to create the application project.</span></span> <span data-ttu-id="4621d-136">Tento projekt bude používat k sestavení aplikace, který je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-136">You will use this project to build the application that hosts the custom control.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="4621d-137">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="4621d-137">To create the project</span></span>

- <span data-ttu-id="4621d-138">Vytvořte projekt Formulářové aplikace Windows s názvem "MarqueeControlTest" (**souboru** > **nový** > **projektu**  >   **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="4621d-138">Create a Windows Forms Application project called "MarqueeControlTest" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="creating-a-control-library-project"></a><span data-ttu-id="4621d-139">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="4621d-139">Creating a Control Library Project</span></span>

<span data-ttu-id="4621d-140">Dalším krokem je vytvoření projektu knihovny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="4621d-140">The next step is to create the control library project.</span></span> <span data-ttu-id="4621d-141">Vytvořte nový vlastní ovládací prvek a jeho odpovídající vlastní návrháře.</span><span class="sxs-lookup"><span data-stu-id="4621d-141">You will create a new custom control and its corresponding custom designer.</span></span>

### <a name="to-create-the-control-library-project"></a><span data-ttu-id="4621d-142">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="4621d-142">To create the control library project</span></span>

1. <span data-ttu-id="4621d-143">Přidáte do řešení projekt Knihovna ovládacích prvků formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="4621d-143">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="4621d-144">Pojmenujte projekt "MarqueeControlLibrary."</span><span class="sxs-lookup"><span data-stu-id="4621d-144">Name the project "MarqueeControlLibrary."</span></span>

2. <span data-ttu-id="4621d-145">Pomocí **Průzkumníka řešení**, odstraňte výchozí ovládací prvek projektu tak, že odstraníte zdrojový soubor s názvem "UserControl1.cs" nebo "UserControl1.vb", v závislosti na vámi zvolený jazyk.</span><span class="sxs-lookup"><span data-stu-id="4621d-145">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span> <span data-ttu-id="4621d-146">Další informace najdete v tématu [jak: Odebrat, odstranit a vyloučit položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4621d-146">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="4621d-147">Přidat nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-147">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="4621d-148">Zadejte nový zdrojový soubor základní název typu "MarqueeControl."</span><span class="sxs-lookup"><span data-stu-id="4621d-148">Give the new source file a base name of "MarqueeControl."</span></span>

4. <span data-ttu-id="4621d-149">Pomocí **Průzkumníka řešení**, vytvořte novou složku v `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-149">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="4621d-150">Další informace najdete v tématu [jak: Přidání nových položek projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4621d-150">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="4621d-151">Název nové složky "Návrhu."</span><span class="sxs-lookup"><span data-stu-id="4621d-151">Name the new folder "Design."</span></span>

5. <span data-ttu-id="4621d-152">Klikněte pravým tlačítkem myši **návrhu** složky a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="4621d-152">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="4621d-153">Zadejte zdrojový soubor základní název "MarqueeControlRootDesigner."</span><span class="sxs-lookup"><span data-stu-id="4621d-153">Give the source file a base name of "MarqueeControlRootDesigner."</span></span>

6. <span data-ttu-id="4621d-154">Budete muset používat typy ze sestavení System.Design, proto přidat tento odkaz `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-154">You will need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4621d-155">Použití sestavení System.Design, musí váš projekt cílit na plnou verzi rozhraní .NET Framework není rozhraní .NET Framework Client Profile.</span><span class="sxs-lookup"><span data-stu-id="4621d-155">To use the System.Design assembly, your project must target the full version of the .NET Framework, not the .NET Framework Client Profile.</span></span> <span data-ttu-id="4621d-156">Chcete-li změnit cílovou architekturu, [jak: Cílení na určitou verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="4621d-156">To change the target framework, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

## <a name="referencing-the-custom-control-project"></a><span data-ttu-id="4621d-157">Odkazování na projekt vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-157">Referencing the Custom Control Project</span></span>

<span data-ttu-id="4621d-158">Budete používat `MarqueeControlTest` projekt k testování vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-158">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="4621d-159">Projekt testů dozví o vlastní ovládací prvek přidáte odkaz na projekt `MarqueeControlLibrary` sestavení.</span><span class="sxs-lookup"><span data-stu-id="4621d-159">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

### <a name="to-reference-the-custom-control-project"></a><span data-ttu-id="4621d-160">Chcete-li odkazovat na projekt, vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4621d-160">To reference the custom control project</span></span>

- <span data-ttu-id="4621d-161">V `MarqueeControlTest` projektu, přidejte odkaz na projekt `MarqueeControlLibrary` sestavení.</span><span class="sxs-lookup"><span data-stu-id="4621d-161">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="4621d-162">Nezapomeňte použít **projekty** kartu **přidat odkaz** dialogové okno namísto odkazování `MarqueeControlLibrary` sestavení přímo.</span><span class="sxs-lookup"><span data-stu-id="4621d-162">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="defining-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="4621d-163">Definování vlastního ovládacího prvku a jeho vlastní návrháři</span><span class="sxs-lookup"><span data-stu-id="4621d-163">Defining a Custom Control and Its Custom Designer</span></span>
 <span data-ttu-id="4621d-164">Vlastní ovládací prvek bude odvozovat <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-164">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="4621d-165">Díky tomu váš ovládací prvek obsahující další ovládací prvky a navíc nabízí spoustu výchozí funkce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-165">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

 <span data-ttu-id="4621d-166">Vlastní ovládací prvek bude mít přidružený vlastní designer.</span><span class="sxs-lookup"><span data-stu-id="4621d-166">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="4621d-167">To umožňuje vytvořit jedinečný návrhové prostředí navržených speciálně pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4621d-167">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

 <span data-ttu-id="4621d-168">Přidružte ovládací prvek pomocí jeho návrháře pomocí <xref:System.ComponentModel.DesignerAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-168">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="4621d-169">Vzhledem k tomu, že vyvíjíte celý chování vlastního ovládacího prvku v době návrhu, se implementovat vlastní návrháře <xref:System.ComponentModel.Design.IRootDesigner> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4621d-169">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="4621d-170">Chcete-li definovat vlastní ovládací prvek a jeho vlastní návrháři</span><span class="sxs-lookup"><span data-stu-id="4621d-170">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="4621d-171">Otevřít `MarqueeControl` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-171">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-172">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="4621d-172">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="4621d-173">Přidat <xref:System.ComponentModel.DesignerAttribute> k `MarqueeControl` deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-173">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="4621d-174">Tento návrhář přidruží vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-174">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="4621d-175">Otevřít `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-175">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-176">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="4621d-176">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="4621d-177">Změňte deklaraci `MarqueeControlRootDesigner` dědit z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-177">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="4621d-178">Použít <xref:System.ComponentModel.ToolboxItemFilterAttribute> k určení návrháře interakci s **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="4621d-178">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

     <span data-ttu-id="4621d-179">**Poznámka:** definice `MarqueeControlRootDesigner` třídy byl uzavřený do obor názvů s názvem "MarqueeControlLibrary.Design."</span><span class="sxs-lookup"><span data-stu-id="4621d-179">**Note** The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called "MarqueeControlLibrary.Design."</span></span> <span data-ttu-id="4621d-180">Toto prohlášení umístí návrháře speciální oboru názvů vyhrazený pro typy související s návrhem.</span><span class="sxs-lookup"><span data-stu-id="4621d-180">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="4621d-181">Definovat konstruktor pro `MarqueeControlRootDesigner` třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-181">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="4621d-182">Vložit <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz v těle konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4621d-182">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="4621d-183">To bude hodit pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="4621d-183">This will be useful for debugging purposes.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a><span data-ttu-id="4621d-184">Vytvoření Instance vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-184">Creating an Instance of Your Custom Control</span></span>
 <span data-ttu-id="4621d-185">Sledovat vlastní chování ovládacího prvku v době návrhu, umístí instance ovládacího prvku na formulář v nástrojích pro `MarqueeControlTest` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-185">To observe the custom design-time behavior of your control, you will place an instance of your control on the form in `MarqueeControlTest` project.</span></span>

### <a name="to-create-an-instance-of-your-custom-control"></a><span data-ttu-id="4621d-186">K vytvoření instance vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-186">To create an instance of your custom control</span></span>

1. <span data-ttu-id="4621d-187">Přidat nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlTest` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-187">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="4621d-188">Zadejte nový zdrojový soubor základní název "DemoMarqueeControl."</span><span class="sxs-lookup"><span data-stu-id="4621d-188">Give the new source file a base name of "DemoMarqueeControl."</span></span>

2. <span data-ttu-id="4621d-189">Otevřít `DemoMarqueeControl` soubor **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-189">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-190">V horní části souboru, importovat `MarqueeControlLibrary` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="4621d-190">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. <span data-ttu-id="4621d-191">Změňte deklaraci `DemoMarqueeControl` dědit z `MarqueeControl` třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-191">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

2. <span data-ttu-id="4621d-192">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="4621d-192">Build the project.</span></span>

3. <span data-ttu-id="4621d-193">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="4621d-193">Open `Form1` in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="4621d-194">Najít **MarqueeControlTest součásti** kartu **nástrojů** a otevřete ho.</span><span class="sxs-lookup"><span data-stu-id="4621d-194">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="4621d-195">Přetáhněte `DemoMarqueeControl` z **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="4621d-195">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="4621d-196">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="4621d-196">Build the project.</span></span>

## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="4621d-197">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="4621d-197">Setting Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="4621d-198">Pokud vyvíjíte vlastní možnosti času návrhu, bude potřeba ladění ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="4621d-198">When you are developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="4621d-199">Neexistuje jednoduchý způsob, jak nastavení projektu pro povolení ladění v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-199">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="4621d-200">Další informace najdete v tématu [názorný postup: Ovládací prvky ladění vlastního Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="4621d-200">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="4621d-201">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="4621d-201">To set up the project for design-time debugging</span></span>

1. <span data-ttu-id="4621d-202">Klikněte pravým tlačítkem myši `MarqueeControlLibrary` projektu a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4621d-202">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="4621d-203">V dialogovém okně "Stránky vlastností MarqueeControlLibrary" vyberte **ladění** stránky.</span><span class="sxs-lookup"><span data-stu-id="4621d-203">In the "MarqueeControlLibrary Property Pages" dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="4621d-204">V **spustit akci** vyberte **spustit externí Program**.</span><span class="sxs-lookup"><span data-stu-id="4621d-204">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="4621d-205">Bude ladění samostatnou instanci sady Visual Studio, proto klikněte na symbol tří teček (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Procházet pro Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="4621d-205">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="4621d-206">Název spustitelného souboru devenv.exe, a pokud jste nainstalovali do výchozího umístění, její cesta 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4621d-206">The name of the executable file is devenv.exe, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>

4. <span data-ttu-id="4621d-207">Kliknutím na OK zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4621d-207">Click OK to close the dialog box.</span></span>

5. <span data-ttu-id="4621d-208">Klikněte pravým tlačítkem myši `MarqueeControlLibrary` projektu a vyberte "Nastavit jako spouštěný projekt" Povolit této konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="4621d-208">Right-click the `MarqueeControlLibrary` project and select "Set as StartUp Project" to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="4621d-209">CheckPoint</span><span class="sxs-lookup"><span data-stu-id="4621d-209">Checkpoint</span></span>

<span data-ttu-id="4621d-210">Nyní jste připraveni k ladění chování návrhu vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-210">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="4621d-211">Jakmile určíte, že je správně nastavené ladicího prostředí budete testovat přidružení mezi vlastního ovládacího prvku a vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="4621d-211">Once you have determined that the debugging environment is set up correctly, you will test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="4621d-212">K testování ladicí prostředí a návrháře přidružení</span><span class="sxs-lookup"><span data-stu-id="4621d-212">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="4621d-213">Otevřít `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu** a umístit zarážky na <xref:System.Diagnostics.Trace.WriteLine%2A> příkazu.</span><span class="sxs-lookup"><span data-stu-id="4621d-213">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="4621d-214">Stisknutím klávesy F5 pro spuštění relace ladění.</span><span class="sxs-lookup"><span data-stu-id="4621d-214">Press F5 to start the debugging session.</span></span> <span data-ttu-id="4621d-215">Všimněte si, že je vytvořena nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4621d-215">Note that a new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="4621d-216">V nové instanci sady Visual Studio otevřete řešení "MarqueeControlTest".</span><span class="sxs-lookup"><span data-stu-id="4621d-216">In the new instance of Visual Studio, open the "MarqueeControlTest" solution.</span></span> <span data-ttu-id="4621d-217">Řešení můžete snadno vyhledat tak, že vyberete **posledních projektů** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="4621d-217">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="4621d-218">Soubor řešení "MarqueeControlTest.sln", bude uveden jako naposledy použitých souborů.</span><span class="sxs-lookup"><span data-stu-id="4621d-218">The "MarqueeControlTest.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="4621d-219">Otevřít `DemoMarqueeControl` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="4621d-219">Open the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="4621d-220">Všimněte si, že instanci ladění aplikace Visual Studio získá fokus a provádění zastaví na zarážku.</span><span class="sxs-lookup"><span data-stu-id="4621d-220">Note that the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="4621d-221">Stisknutím klávesy F5 pokračovat v relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="4621d-221">Press F5 to continue the debugging session.</span></span>

<span data-ttu-id="4621d-222">V tomto okamžiku všechno, co je v místo, kde můžete k vývoji a ladění vlastního ovládacího prvku a jeho přidružený vlastní designer.</span><span class="sxs-lookup"><span data-stu-id="4621d-222">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="4621d-223">Zbývající část tohoto návodu bude soustředit se na podrobnosti implementace funkce ovládacího prvku a návrháře.</span><span class="sxs-lookup"><span data-stu-id="4621d-223">The remainder of this walkthrough will concentrate on the details of implementing features of the control and the designer.</span></span>

## <a name="implementing-your-custom-control"></a><span data-ttu-id="4621d-224">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-224">Implementing Your Custom Control</span></span>

<span data-ttu-id="4621d-225">`MarqueeControl` Je <xref:System.Windows.Forms.UserControl> stačí nepatrné přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="4621d-225">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="4621d-226">Poskytuje dvě metody: `Start`, která spustí animace běžícího textu a `Stop`, které zastaví animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-226">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="4621d-227">Protože `MarqueeControl` obsahuje podřízené ovládací prvky, které implementují `IMarqueeWidget` rozhraní, `Start` a `Stop` výčet každé podřízené ovládací prvky a volání `StartMarquee` a `StopMarquee` metody, v uvedeném pořadí, na všechny podřízené ovládací prvky který implementuje `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="4621d-227">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="4621d-228">Vzhled `MarqueeBorder` a `MarqueeText` ovládacích prvků je závislé na rozložení, tak `MarqueeControl` přepsání <xref:System.Windows.Forms.Control.OnLayout%2A> metoda a volání <xref:System.Windows.Forms.Control.PerformLayout%2A> na podřízené ovládací prvky tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="4621d-228">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="4621d-229">Toto je rozsah `MarqueeControl` vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="4621d-229">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="4621d-230">Běhové funkce jsou implementované `MarqueeBorder` a `MarqueeText` ovládací prvky a funkce návrhu jsou implementované `MarqueeBorderDesigner` a `MarqueeControlRootDesigner` třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-230">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="4621d-231">Pro implementaci vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4621d-231">To implement your custom control</span></span>

1. <span data-ttu-id="4621d-232">Otevřít `MarqueeControl` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-232">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-233">Implementace `Start` a `Stop` metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-233">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="4621d-234">Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-234">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a><span data-ttu-id="4621d-235">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4621d-235">Creating a Child Control for Your Custom Control</span></span>

<span data-ttu-id="4621d-236">`MarqueeControl` Bude hostovat dva druhy podřízeného ovládacího prvku: `MarqueeBorder` ovládacího prvku a `MarqueeText` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-236">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="4621d-237">`MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světla" kolem okraje.</span><span class="sxs-lookup"><span data-stu-id="4621d-237">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="4621d-238">Indikátory flash v pořadí, takže se budou zobrazovat Přesun celého ohraničení.</span><span class="sxs-lookup"><span data-stu-id="4621d-238">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="4621d-239">Rychlost, jakou světel flash řídí vlastnost s názvem `UpdatePeriod`.</span><span class="sxs-lookup"><span data-stu-id="4621d-239">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="4621d-240">Několik dalších vlastních vlastností určují další aspekty vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-240">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="4621d-241">Dvě metody volá `StartMarquee` a `StopMarquee`, řídit, kdy animace spouští a zastavuje.</span><span class="sxs-lookup"><span data-stu-id="4621d-241">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="4621d-242">`MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec.</span><span class="sxs-lookup"><span data-stu-id="4621d-242">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="4621d-243">Podobně jako `MarqueeBorder` ovládacího prvku, rychlost, jakou začne blikat text je řízena `UpdatePeriod` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4621d-243">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="4621d-244">`MarqueeText` Ovládací prvek má také `StartMarquee` a `StopMarquee` metody společně s `MarqueeBorder` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-244">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="4621d-245">V době návrhu `MarqueeControlRootDesigner` umožňuje typy těchto dvou ovládacích prvků mají být přidány do `MarqueeControl` v libovolné kombinaci.</span><span class="sxs-lookup"><span data-stu-id="4621d-245">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="4621d-246">Společné funkce dvou ovládacích prvků se promítnou do rozhraní volá `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="4621d-246">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="4621d-247">Díky tomu `MarqueeControl` zjišťovat všechny Marquee související podřízené ovládací prvky a udělit jim zvláštní zacházení.</span><span class="sxs-lookup"><span data-stu-id="4621d-247">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="4621d-248">K implementaci funkce pravidelné animace, budete používat <xref:System.ComponentModel.BackgroundWorker> objekty z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4621d-248">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4621d-249">Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale po mnoho `IMarqueeWidget` objekty jsou k dispozici, jedno vlákno uživatelského rozhraní, možná nebudete moct držet krok s animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-249">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="4621d-250">Chcete-li vytvořit podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4621d-250">To create a child control for your custom control</span></span>

1. <span data-ttu-id="4621d-251">Přidat novou položku třídy a `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-251">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="4621d-252">Zadejte nový zdrojový soubor základní název "IMarqueeWidget."</span><span class="sxs-lookup"><span data-stu-id="4621d-252">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="4621d-253">Otevřít `IMarqueeWidget` zdrojový soubor v **Editor kódu** a změnit deklarace z `class` k `interface`:</span><span class="sxs-lookup"><span data-stu-id="4621d-253">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="4621d-254">Přidejte následující kód, který `IMarqueeWidget` rozhraní ke zveřejnění dvě metody a vlastnosti, která manipulovat s animace běžícího textu:</span><span class="sxs-lookup"><span data-stu-id="4621d-254">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="4621d-255">Přidat nový **vlastní ovládací prvek** položkou `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-255">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="4621d-256">Zadejte nový zdrojový soubor základní název "MarqueeText."</span><span class="sxs-lookup"><span data-stu-id="4621d-256">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="4621d-257">Přetáhněte <xref:System.ComponentModel.BackgroundWorker> z **nástrojů** do vaší `MarqueeText` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-257">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="4621d-258">Tato součást vám umožní `MarqueeText` ovládací prvek aktualizovalo samo asynchronně.</span><span class="sxs-lookup"><span data-stu-id="4621d-258">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="4621d-259">V okně Vlastnosti nastavte <xref:System.ComponentModel.BackgroundWorker> komponenty `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastností `true`.</span><span class="sxs-lookup"><span data-stu-id="4621d-259">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="4621d-260">Tato nastavení umožňují <xref:System.ComponentModel.BackgroundWorker> komponenty pravidelně zvýšit <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí a zrušení asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="4621d-260">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="4621d-261">Další informace najdete v tématu [BackgroundWorker – komponenta](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="4621d-261">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="4621d-262">Otevřít `MarqueeText` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-262">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-263">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="4621d-263">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="4621d-264">Změňte deklaraci `MarqueeText` dědit z <xref:System.Windows.Forms.Label> a provádět `IMarqueeWidget` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="4621d-264">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="4621d-265">Deklarujte proměnné instance, které odpovídají vystavené vlastnosti a inicializace v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4621d-265">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="4621d-266">`isLit` Pole určuje, zda text je nutné překreslit barevně dána `LightColor` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4621d-266">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="4621d-267">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="4621d-267">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="4621d-268">`StartMarquee` a `StopMarquee` vyvolání metody <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metod ke spuštění a ukončení animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-268">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="4621d-269"><xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atributy jsou použity `UpdatePeriod` vlastnost, aby se zobrazovalo ve vlastní části okna Vlastnosti volá "Marquee."</span><span class="sxs-lookup"><span data-stu-id="4621d-269">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="4621d-270">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-270">Implement the property accessors.</span></span> <span data-ttu-id="4621d-271">Bude vystavovat dvě vlastnosti do klientů: `LightColor` a `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="4621d-271">You will expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="4621d-272"><xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atributy jsou použity tyto vlastnosti, takže vlastnosti se zobrazí v části vlastní okna Vlastnosti volá "Marquee."</span><span class="sxs-lookup"><span data-stu-id="4621d-272">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="4621d-273">Implementace obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.</span><span class="sxs-lookup"><span data-stu-id="4621d-273">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="4621d-274"><xref:System.ComponentModel.BackgroundWorker.DoWork> Počet milisekund, po prodlevě obslužná rutina události `UpdatePeriod` poté vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události, dokud váš kód přestane animace voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="4621d-274">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="4621d-275"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Obslužná rutina události přepíná mezi stavu světlé a tmavé vzhled blikat text.</span><span class="sxs-lookup"><span data-stu-id="4621d-275">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="4621d-276">Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> způsob povolení animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-276">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="4621d-277">Sestavte řešení stisknutím klávesy F6.</span><span class="sxs-lookup"><span data-stu-id="4621d-277">Press F6 to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="4621d-278">Vytvoření MarqueeBorder podřízený ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4621d-278">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="4621d-279">`MarqueeBorder` Je o něco složitější než ovládací prvek `MarqueeText` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-279">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="4621d-280">Obsahuje více vlastností a animace v <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je složitější.</span><span class="sxs-lookup"><span data-stu-id="4621d-280">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="4621d-281">V zásadě je podobný tomu `MarqueeText` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-281">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="4621d-282">Vzhledem k tomu, `MarqueeBorder` ovládací prvek může mít podřízené ovládací prvky, musí se jednat o seznámen <xref:System.Windows.Forms.Control.Layout> události.</span><span class="sxs-lookup"><span data-stu-id="4621d-282">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="4621d-283">Vytvoření ovládacího prvku MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="4621d-283">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="4621d-284">Přidat nový **vlastní ovládací prvek** položkou `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-284">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="4621d-285">Zadejte nový zdrojový soubor základní název "MarqueeBorder."</span><span class="sxs-lookup"><span data-stu-id="4621d-285">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="4621d-286">Přetáhněte <xref:System.ComponentModel.BackgroundWorker> z **nástrojů** do vaší `MarqueeBorder` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-286">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="4621d-287">Tato součást vám umožní `MarqueeBorder` ovládací prvek aktualizovalo samo asynchronně.</span><span class="sxs-lookup"><span data-stu-id="4621d-287">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="4621d-288">V okně Vlastnosti nastavte <xref:System.ComponentModel.BackgroundWorker> komponenty `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastností `true`.</span><span class="sxs-lookup"><span data-stu-id="4621d-288">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="4621d-289">Tato nastavení umožňují <xref:System.ComponentModel.BackgroundWorker> komponenty pravidelně zvýšit <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí a zrušení asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="4621d-289">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="4621d-290">Další informace najdete v tématu [BackgroundWorker – komponenta](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="4621d-290">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="4621d-291">V okně Vlastnosti klikněte na tlačítko události.</span><span class="sxs-lookup"><span data-stu-id="4621d-291">In the Properties window, click the Events button.</span></span> <span data-ttu-id="4621d-292">Připojte obslužné rutiny pro <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.</span><span class="sxs-lookup"><span data-stu-id="4621d-292">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="4621d-293">Otevřít `MarqueeBorder` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-293">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-294">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="4621d-294">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="4621d-295">Změňte deklaraci `MarqueeBorder` dědit z <xref:System.Windows.Forms.Panel> a provádět `IMarqueeWidget` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4621d-295">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="4621d-296">Deklarace výčtů dvě pro správu `MarqueeBorder` stav ovládacího prvku: `MarqueeSpinDirection`, který určuje směr, ve kterém světel "dokola" ohraničení, a `MarqueeLightShape`, která určuje tvar světla (čtvereček nebo cyklické).</span><span class="sxs-lookup"><span data-stu-id="4621d-296">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="4621d-297">Tato deklarace před umístit `MarqueeBorder` deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-297">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="4621d-298">Deklarujte proměnné instance, které odpovídají vystavené vlastnosti a inicializace v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4621d-298">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="4621d-299">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="4621d-299">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="4621d-300">`StartMarquee` a `StopMarquee` vyvolání metody <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metod ke spuštění a ukončení animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-300">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="4621d-301">Vzhledem k tomu, `MarqueeBorder` ovládacího prvku může obsahovat podřízené ovládací prvky, `StartMarquee` metoda výčet všech podřízených ovládacích prvků a volání `StartMarquee` na ty, které implementují `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="4621d-301">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="4621d-302">`StopMarquee` Metoda má podobné implementace.</span><span class="sxs-lookup"><span data-stu-id="4621d-302">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="4621d-303">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-303">Implement the property accessors.</span></span> <span data-ttu-id="4621d-304">`MarqueeBorder` Ovládací prvek má několik vlastností pro řízení její vzhled.</span><span class="sxs-lookup"><span data-stu-id="4621d-304">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="4621d-305">Implementace obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.</span><span class="sxs-lookup"><span data-stu-id="4621d-305">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="4621d-306"><xref:System.ComponentModel.BackgroundWorker.DoWork> Počet milisekund, po prodlevě obslužná rutina události `UpdatePeriod` poté vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události, dokud váš kód přestane animace voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="4621d-306">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="4621d-307"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Zvýší pozice indikátor "základní", ze kterého je určen stav světlý/tmavý další indikátory, a volá obslužná rutina události <xref:System.Windows.Forms.Control.Refresh%2A> metoda způsobit repaint samotný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4621d-307">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="4621d-308">Implementace pomocných metod `IsLit` a `DrawLight`.</span><span class="sxs-lookup"><span data-stu-id="4621d-308">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="4621d-309">`IsLit` Metody určuje barvy světla na dané pozici.</span><span class="sxs-lookup"><span data-stu-id="4621d-309">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="4621d-310">Světla, které jsou "lit" vykresleny barvou dána `LightColor` vlastnost a ty, které jsou "tmavě" jsou vykreslovány vedle barevně dána `DarkColor` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4621d-310">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="4621d-311">`DrawLight` Metoda vykreslí světla odpovídající barvou, tvar a pozici.</span><span class="sxs-lookup"><span data-stu-id="4621d-311">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="4621d-312">Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> a <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-312">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="4621d-313"><xref:System.Windows.Forms.Control.OnPaint%2A> Metoda vykreslí světla podél okrajů `MarqueeBorder` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-313">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="4621d-314">Vzhledem k tomu, <xref:System.Windows.Forms.Control.OnPaint%2A> metoda závisí na velikosti `MarqueeBorder` ovládací prvek, musíte ji volat pokaždé, když se změní rozložení.</span><span class="sxs-lookup"><span data-stu-id="4621d-314">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="4621d-315">Za tím účelem přepsání <xref:System.Windows.Forms.Control.OnLayout%2A> a volat <xref:System.Windows.Forms.Control.Refresh%2A>.</span><span class="sxs-lookup"><span data-stu-id="4621d-315">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="4621d-316">Vytvoření vlastního návrháře a stínové vlastnosti filtru</span><span class="sxs-lookup"><span data-stu-id="4621d-316">Creating a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="4621d-317">`MarqueeControlRootDesigner` Třída poskytuje implementaci pro Návrhář kořenových aktivit.</span><span class="sxs-lookup"><span data-stu-id="4621d-317">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="4621d-318">Kromě tohoto návrháře, který pracuje `MarqueeControl`, budete potřebovat vlastní návrháře, který je speciálně přidružený `MarqueeBorder` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-318">In addition to this designer, which operates on the `MarqueeControl`, you will need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="4621d-319">Tento návrhář obsahuje vlastní chování, které je vhodné v rámci vlastní kořenového návrháře.</span><span class="sxs-lookup"><span data-stu-id="4621d-319">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="4621d-320">Konkrétně `MarqueeBorderDesigner` "stínové", který se určité vlastnosti vyfiltrujte `MarqueeBorder` ovládacího prvku, změna jejich interakce s prostředím návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-320">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="4621d-321">Zachycení volání přistupující objekt vlastnosti komponenty se označuje jako "stínováním."</span><span class="sxs-lookup"><span data-stu-id="4621d-321">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="4621d-322">Umožňuje sledovat hodnotu nastavenou uživatelem designeru a volitelně předat tuto hodnotu na komponentu navržen.</span><span class="sxs-lookup"><span data-stu-id="4621d-322">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="4621d-323">V tomto příkladu <xref:System.Windows.Forms.Control.Visible%2A> a <xref:System.Windows.Forms.Control.Enabled%2A> vlastnosti se stínovaný podle `MarqueeBorderDesigner`, což zabrání uživateli v provádění `MarqueeBorder` ovládací prvek neviditelný nebo zakázaný v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-323">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="4621d-324">Návrháři můžete také přidávat a odebírat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-324">Designers can also add and remove properties.</span></span> <span data-ttu-id="4621d-325">V tomto příkladu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost bude odebrána v době návrhu, protože `MarqueeBorder` řízení prostřednictvím kódu programu nastavuje výplň na základě velikosti světla určené `LightSize` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4621d-325">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="4621d-326">Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner>, který má metody, které můžete změnit atributy, vlastnosti a události, které jsou vystavené ovládací prvek v době návrhu:</span><span class="sxs-lookup"><span data-stu-id="4621d-326">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="4621d-327">Při změně veřejné rozhraní komponenty pomocí těchto metod, musí dodržovat tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="4621d-327">When changing the public interface of a component using these methods, you must follow these rules:</span></span>

- <span data-ttu-id="4621d-328">Přidat nebo odebrat položky `PreFilter` pouze metody</span><span class="sxs-lookup"><span data-stu-id="4621d-328">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="4621d-329">Upravit existující položky v `PostFilter` pouze metody</span><span class="sxs-lookup"><span data-stu-id="4621d-329">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="4621d-330">Vždy nejprve volat základní implementaci `PreFilter` metody</span><span class="sxs-lookup"><span data-stu-id="4621d-330">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="4621d-331">Vždy volat základní implementaci poslední `PostFilter` metody</span><span class="sxs-lookup"><span data-stu-id="4621d-331">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="4621d-332">Týkajícími se tato pravidla zajišťuje, že všechny návrháře v prostředí návrhu mají konzistentní zobrazení všech součástí navržen.</span><span class="sxs-lookup"><span data-stu-id="4621d-332">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="4621d-333"><xref:System.ComponentModel.Design.ComponentDesigner> Třída obsahuje slovník pro správu hodnoty stínové vlastnosti, které která vás zbaví nutnosti vytvářet konkrétní instanci proměnné.</span><span class="sxs-lookup"><span data-stu-id="4621d-333">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="4621d-334">Vytvoření vlastního návrháře na stínové a filtrovat vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4621d-334">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="4621d-335">Klikněte pravým tlačítkem myši **návrhu** složky a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="4621d-335">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="4621d-336">Zadejte zdrojový soubor základní název "MarqueeBorderDesigner."</span><span class="sxs-lookup"><span data-stu-id="4621d-336">Give the source file a base name of "MarqueeBorderDesigner."</span></span>

2. <span data-ttu-id="4621d-337">Otevřít `MarqueeBorderDesigner` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-337">Open the `MarqueeBorderDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-338">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="4621d-338">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="4621d-339">Změňte deklaraci `MarqueeBorderDesigner` dědit z <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span><span class="sxs-lookup"><span data-stu-id="4621d-339">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="4621d-340">Vzhledem k tomu, `MarqueeBorder` ovládacího prvku může obsahovat podřízené ovládací prvky, `MarqueeBorderDesigner` dědí z <xref:System.Windows.Forms.Design.ParentControlDesigner>, která zpracovává interakce nadřazený podřízený.</span><span class="sxs-lookup"><span data-stu-id="4621d-340">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="4621d-341">Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span><span class="sxs-lookup"><span data-stu-id="4621d-341">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="4621d-342">Implementace <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-342">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="4621d-343">Tato implementace stínové vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4621d-343">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a><span data-ttu-id="4621d-344">Zpracování změny součásti</span><span class="sxs-lookup"><span data-stu-id="4621d-344">Handling Component Changes</span></span>
 <span data-ttu-id="4621d-345">`MarqueeControlRootDesigner` Třída poskytuje vlastní návrhové prostředí pro vaše `MarqueeControl` instancí.</span><span class="sxs-lookup"><span data-stu-id="4621d-345">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="4621d-346">Většinu funkcí návrhu je zděděno od <xref:System.Windows.Forms.Design.DocumentDesigner> třída; se vašeho kódu implementovat úpravami dva: zpracování změny součásti a přidání příkazy návrháře.</span><span class="sxs-lookup"><span data-stu-id="4621d-346">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class; your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

 <span data-ttu-id="4621d-347">Uživatelé návrhu jejich `MarqueeControl` instancí, váš Návrhář kořenových aktivit budou sledovat změny `MarqueeControl` a jeho podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="4621d-347">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="4621d-348">Návrhové prostředí nabízí pohodlný služby <xref:System.ComponentModel.Design.IComponentChangeService>pro sledování se změní na stav součásti.</span><span class="sxs-lookup"><span data-stu-id="4621d-348">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

 <span data-ttu-id="4621d-349">Získat odkaz na tuto službu prostředí s dotazem <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-349">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="4621d-350">Pokud je dotaz úspěšný, návrháře připojit obslužné rutiny pro <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> události a provádět libovolné kroky je třeba udržovat konzistentní stav v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-350">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

 <span data-ttu-id="4621d-351">V případě třídy `MarqueeControlRootDesigner` třídu bude volat <xref:System.Windows.Forms.Control.Refresh%2A> metodu na každý `IMarqueeWidget` obsažen v objektu `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-351">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="4621d-352">To způsobí, že `IMarqueeWidget` objektu samotného při vlastnosti svého nadřazeného objektu, jako jsou odpovídajícím způsobem repaint <xref:System.Windows.Forms.Control.Size%2A> se změní.</span><span class="sxs-lookup"><span data-stu-id="4621d-352">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="4621d-353">Pro případ změn komponenty</span><span class="sxs-lookup"><span data-stu-id="4621d-353">To handle component changes</span></span>

1. <span data-ttu-id="4621d-354">Otevřít `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu** a přepsat <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-354">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="4621d-355">Volat základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotázat <xref:System.ComponentModel.Design.IComponentChangeService>.</span><span class="sxs-lookup"><span data-stu-id="4621d-355">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="4621d-356">Implementace <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4621d-356">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="4621d-357">Test typ odeslání součásti, a pokud se jedná `IMarqueeWidget`, volání jeho <xref:System.Windows.Forms.Control.Refresh%2A> – metoda.</span><span class="sxs-lookup"><span data-stu-id="4621d-357">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="4621d-358">Příkazy návrháře přidání do vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="4621d-358">Adding Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="4621d-359">Návrháře příkaz je příkaz nabídky propojené s obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="4621d-359">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="4621d-360">Příkazy návrháře se přidají do komponenty nabídku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-360">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="4621d-361">Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="4621d-361">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="4621d-362">Ať už přidáte dva příkazy návrháře: **Spustit Test** a **zastavení testu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-362">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="4621d-363">Tato operace vám umožní zobrazit chování za běhu `MarqueeControl` v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-363">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="4621d-364">Tyto příkazy se přidají do `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="4621d-364">These verbs will be added to the `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="4621d-365">Když **spustit Test** je vyvolána, příkaz obslužná rutina události zavolá `StartMarquee` metodu na `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-365">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="4621d-366">Když **zastavit testovací** je vyvolána, příkaz obslužná rutina události zavolá `StopMarquee` metodu na `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-366">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="4621d-367">Provádění `StartMarquee` a `StopMarquee` metody volat tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget`, takže omezením `IMarqueeWidget` ovládací prvky se také účastní testu.</span><span class="sxs-lookup"><span data-stu-id="4621d-367">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="4621d-368">Příkazy návrháře přidat do vlastní návrháři</span><span class="sxs-lookup"><span data-stu-id="4621d-368">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="4621d-369">V `MarqueeControlRootDesigner` třídy, přidejte obslužné rutiny události s názvem `OnVerbRunTest` a `OnVerbStopTest`.</span><span class="sxs-lookup"><span data-stu-id="4621d-369">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="4621d-370">Připojení těchto obslužných rutin událostí k jejich odpovídající příkazy návrháře.</span><span class="sxs-lookup"><span data-stu-id="4621d-370">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="4621d-371">`MarqueeControlRootDesigner` dědí <xref:System.ComponentModel.Design.DesignerVerbCollection> ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-371">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="4621d-372">Vytvoříte dvě nové <xref:System.ComponentModel.Design.DesignerVerb> objekty a přidat je do této kolekce v <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-372">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a><span data-ttu-id="4621d-373">Vytvoření vlastního editoru UITypeEditor.</span><span class="sxs-lookup"><span data-stu-id="4621d-373">Creating a Custom UITypeEditor</span></span>

<span data-ttu-id="4621d-374">Při vytváření vlastního návrhu prostředí pro uživatele, je často žádoucí, vytvořte vlastní interakci se v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-374">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="4621d-375">Můžete to udělat tak, že vytvoříte <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="4621d-375">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span> <span data-ttu-id="4621d-376">Další informace najdete v tématu [jak: Vytvoření editoru typů uživatelského rozhraní](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4621d-376">For more information, see [How to: Create a UI Type Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).</span></span>

<span data-ttu-id="4621d-377">`MarqueeBorder` Ovládacího prvku poskytuje několik vlastností v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-377">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="4621d-378">Dva z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty.</span><span class="sxs-lookup"><span data-stu-id="4621d-378">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="4621d-379">Pro ilustraci použití Editoru typů uživatelského rozhraní, `MarqueeLightShape` vlastnost bude mít přiřazený <xref:System.Drawing.Design.UITypeEditor> třídy.</span><span class="sxs-lookup"><span data-stu-id="4621d-379">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="4621d-380">Chcete-li vytvořit vlastní typ uživatelského rozhraní editoru</span><span class="sxs-lookup"><span data-stu-id="4621d-380">To create a custom UI type editor</span></span>

1. <span data-ttu-id="4621d-381">Otevřít `MarqueeBorder` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-381">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="4621d-382">V definici `MarqueeBorder` třídy, deklarujte třídu s názvem `LightShapeEditor` , která je odvozena z <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="4621d-382">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="4621d-383">Deklarovat <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance proměnné s názvem `editorService`.</span><span class="sxs-lookup"><span data-stu-id="4621d-383">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="4621d-384">Přepsat <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-384">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="4621d-385">Tato implementace vrátí <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, který informuje návrhové prostředí, jak má zobrazit `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="4621d-385">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="4621d-386">Přepsat <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-386">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="4621d-387">Tato implementace dotazuje návrhové prostředí pro <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> objektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-387">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="4621d-388">Pokud úspěšné, vytvoří `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-388">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="4621d-389"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Je vyvolána metoda pro spuštění `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="4621d-389">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="4621d-390">Hodnota vrácená z toto volání se vrátí do vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="4621d-390">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="4621d-391">Vytvoření ovládacího prvku zobrazení pro vaše vlastní editor UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="4621d-391">Creating a View Control for your Custom UITypeEditor</span></span>

1. <span data-ttu-id="4621d-392">`MarqueeLightShape` Vlastnost podporuje dva typy světla tvarů: `Square` a `Circle`.</span><span class="sxs-lookup"><span data-stu-id="4621d-392">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="4621d-393">Můžete vytvořit vlastní ovládací prvek používat výhradně pro účely graficky zobrazení tyto hodnoty v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-393">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="4621d-394">Budou používat tento vlastní ovládací prvek vaše <xref:System.Drawing.Design.UITypeEditor> pracovat v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-394">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="4621d-395">Chcete-li vytvořit ovládací prvek zobrazení pro vaše vlastní uživatelské rozhraní editoru typů</span><span class="sxs-lookup"><span data-stu-id="4621d-395">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="4621d-396">Přidat nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-396">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="4621d-397">Zadejte nový zdrojový soubor základní název "LightShapeSelectionControl."</span><span class="sxs-lookup"><span data-stu-id="4621d-397">Give the new source file a base name of "LightShapeSelectionControl."</span></span>

2. <span data-ttu-id="4621d-398">Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládacích prvků z **nástrojů** na `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-398">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="4621d-399">Pojmenujte je `squarePanel` a `circlePanel`.</span><span class="sxs-lookup"><span data-stu-id="4621d-399">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="4621d-400">Uspořádejte je vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="4621d-400">Arrange them side by side.</span></span> <span data-ttu-id="4621d-401">Nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost objektu i <xref:System.Windows.Forms.Panel> ovládacích prvků do (60, 60).</span><span class="sxs-lookup"><span data-stu-id="4621d-401">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to (60, 60).</span></span> <span data-ttu-id="4621d-402">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `squarePanel` ovládací prvek (8, 10).</span><span class="sxs-lookup"><span data-stu-id="4621d-402">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to (8, 10).</span></span> <span data-ttu-id="4621d-403">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `circlePanel` ovládací prvek (80, 10).</span><span class="sxs-lookup"><span data-stu-id="4621d-403">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to (80, 10).</span></span> <span data-ttu-id="4621d-404">Nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost `LightShapeSelectionControl` do (150, 80).</span><span class="sxs-lookup"><span data-stu-id="4621d-404">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to (150, 80).</span></span>

3. <span data-ttu-id="4621d-405">Otevřít `LightShapeSelectionControl` zdrojový soubor v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="4621d-405">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="4621d-406">V horní části souboru, importovat <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="4621d-406">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. <span data-ttu-id="4621d-407">Implementace <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro `squarePanel` a `circlePanel` ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="4621d-407">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="4621d-408">Tyto metody volat <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> na konec vlastního <xref:System.Drawing.Design.UITypeEditor> relace úprav.</span><span class="sxs-lookup"><span data-stu-id="4621d-408">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. <span data-ttu-id="4621d-409">Deklarovat <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance proměnné s názvem `editorService`.</span><span class="sxs-lookup"><span data-stu-id="4621d-409">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. <span data-ttu-id="4621d-410">Deklarace `MarqueeLightShape` instance proměnné s názvem `lightShapeValue`.</span><span class="sxs-lookup"><span data-stu-id="4621d-410">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. <span data-ttu-id="4621d-411">V `LightShapeSelectionControl` konstruktoru, připojte <xref:System.Windows.Forms.Control.Click> obslužných rutin událostí k `squarePanel` a `circlePanel` ovládacích prvků <xref:System.Windows.Forms.Control.Click> události.</span><span class="sxs-lookup"><span data-stu-id="4621d-411">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="4621d-412">Navíc definovat přetížení konstruktoru, který přiřazuje `MarqueeLightShape` hodnotu z prostředí návrhu tak, aby `lightShapeValue` pole.</span><span class="sxs-lookup"><span data-stu-id="4621d-412">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. <span data-ttu-id="4621d-413">V <xref:System.ComponentModel.Component.Dispose%2A> metoda, odpojit <xref:System.Windows.Forms.Control.Click> obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="4621d-413">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. <span data-ttu-id="4621d-414">V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4621d-414">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="4621d-415">Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl.Designer.vb a odeberte výchozí definice <xref:System.ComponentModel.Component.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-415">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

5. <span data-ttu-id="4621d-416">Implementace `LightShape` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4621d-416">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. <span data-ttu-id="4621d-417">Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4621d-417">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="4621d-418">Tato implementace nakreslí plný čtvereček a kruh.</span><span class="sxs-lookup"><span data-stu-id="4621d-418">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="4621d-419">Vybrané hodnoty se budou rovněž zvýrazněna kreslením ohraničení kolem jeden tvar nebo druhé.</span><span class="sxs-lookup"><span data-stu-id="4621d-419">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a><span data-ttu-id="4621d-420">Testování vlastní ovládací prvek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="4621d-420">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="4621d-421">V tomto okamžiku můžete vytvořit `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="4621d-421">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="4621d-422">Testování vaší implementace tak, že vytvoříte ovládací prvek, který dědí z `MarqueeControl` třídy a používat ho ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="4621d-422">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="4621d-423">Chcete-li vytvořit vlastní implementaci typu MarqueeControl</span><span class="sxs-lookup"><span data-stu-id="4621d-423">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="4621d-424">Otevřít `DemoMarqueeControl` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="4621d-424">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="4621d-425">Tím se vytvoří instance `DemoMarqueeControl` zadejte a zobrazí jej v instanci `MarqueeControlRootDesigner` typu.</span><span class="sxs-lookup"><span data-stu-id="4621d-425">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="4621d-426">V **nástrojů**, otevřete **MarqueeControlLibrary součásti** kartu. Zobrazí se `MarqueeBorder` a `MarqueeText` ovládací prvky, které jsou k dispozici pro výběr.</span><span class="sxs-lookup"><span data-stu-id="4621d-426">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="4621d-427">Přetáhněte instance `MarqueeBorder` na ovládací prvek `DemoMarqueeControl` návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="4621d-427">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="4621d-428">Ukotvit to `MarqueeBorder` ovládacího prvku na nadřazený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4621d-428">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="4621d-429">Přetáhněte instance `MarqueeText` na ovládací prvek `DemoMarqueeControl` návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="4621d-429">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="4621d-430">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="4621d-430">Build the solution.</span></span>

6. <span data-ttu-id="4621d-431">Klikněte pravým tlačítkem myši `DemoMarqueeControl` a z místní nabídky vyberte **spustit Test** možnosti spuštění animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-431">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="4621d-432">Klikněte na tlačítko **zastavit testovací** k ukončení animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-432">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="4621d-433">Otevřít **Form1** v návrhovém zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4621d-433">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="4621d-434">Umístěte dvě <xref:System.Windows.Forms.Button> ovládacích prvků na formuláři.</span><span class="sxs-lookup"><span data-stu-id="4621d-434">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="4621d-435">Pojmenujte je `startButton` a `stopButton`a změnit <xref:System.Windows.Forms.Control.Text%2A> hodnot vlastností do **Start** a **Zastavit**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4621d-435">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="4621d-436">Implementace <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro obě <xref:System.Windows.Forms.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="4621d-436">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="4621d-437">V **nástrojů**, otevřete **MarqueeControlTest součásti** kartu. Zobrazí se `DemoMarqueeControl` k dispozici pro výběr.</span><span class="sxs-lookup"><span data-stu-id="4621d-437">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="4621d-438">Přetáhněte instance `DemoMarqueeControl` na **Form1** návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="4621d-438">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="4621d-439">V <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí, vyvolat `Start` a `Stop` metody `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-439">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

```vb
Private Sub startButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Start()
End Sub 'startButton_Click

Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
Me.demoMarqueeControl1.Stop()
End Sub 'stopButton_Click
```

```csharp
private void startButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Start();
}

private void stopButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Stop();
}
```

1. <span data-ttu-id="4621d-440">Nastavte `MarqueeControlTest` projekt jako spouštěný projekt a potom ho spusťte.</span><span class="sxs-lookup"><span data-stu-id="4621d-440">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="4621d-441">Zobrazení formuláře se zobrazí vaše `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-441">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="4621d-442">Klikněte na tlačítko **Start** tlačítko pro spuštění animace.</span><span class="sxs-lookup"><span data-stu-id="4621d-442">Click the **Start** button to start the animation.</span></span> <span data-ttu-id="4621d-443">Měli byste vidět začne blikat text a světla přesouvat ohraničení.</span><span class="sxs-lookup"><span data-stu-id="4621d-443">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4621d-444">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4621d-444">Next Steps</span></span>

<span data-ttu-id="4621d-445">`MarqueeControlLibrary` Ukazuje jednoduchý provádění vlastní ovládací prvky a přidružené designeru.</span><span class="sxs-lookup"><span data-stu-id="4621d-445">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="4621d-446">Složitější této ukázky můžete provést několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="4621d-446">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="4621d-447">Změňte hodnoty vlastností `DemoMarqueeControl` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="4621d-447">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="4621d-448">Přidat další `MarqueBorder` ovládací prvky, ukotvit je v rámci jejich nadřazené instance k vytvoření efektu vnořené.</span><span class="sxs-lookup"><span data-stu-id="4621d-448">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="4621d-449">Experiment s různými nastaveními pro `UpdatePeriod` a vlastnosti související s světla.</span><span class="sxs-lookup"><span data-stu-id="4621d-449">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="4621d-450">Vytváření vlastních implementací `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="4621d-450">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="4621d-451">Můžete například vytvořit blikající "neon přihlášení" nebo znak animovaný s více bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="4621d-451">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="4621d-452">Dále přizpůsobte možnosti času návrhu.</span><span class="sxs-lookup"><span data-stu-id="4621d-452">Further customize the design-time experience.</span></span> <span data-ttu-id="4621d-453">Můžete zkusit stínováním více vlastností než <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>, a můžete přidat nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4621d-453">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="4621d-454">Přidáte nové příkazy návrháře pro zjednodušení běžné úkoly jako ukotvení podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="4621d-454">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="4621d-455">Licence `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="4621d-455">License the `MarqueeControl`.</span></span> <span data-ttu-id="4621d-456">Další informace najdete v tématu [jak: Licencování komponent a ovládacích prvků](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4621d-456">For more information, see [How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span></span>

- <span data-ttu-id="4621d-457">Řídíte způsob, jakým vaše ovládací prvky serializují a jak vytvořit kód pro ně.</span><span class="sxs-lookup"><span data-stu-id="4621d-457">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="4621d-458">Další informace najdete v tématu [dynamické generování zdrojového kódu a kompilace](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="4621d-458">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4621d-459">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4621d-459">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- <span data-ttu-id="4621d-460">[Postupy: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4621d-460">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>
- <span data-ttu-id="4621d-461">[Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4621d-461">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- <span data-ttu-id="4621d-462">[Vlastní návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4621d-462">[Custom Designers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span></span>
