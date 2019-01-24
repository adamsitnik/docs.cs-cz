---
title: 'Průvodce: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: b4c5001e671db9d615f3bcbc0a35b7b36b45bb01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506859"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="2f270-102">Průvodce: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f270-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="2f270-103">Tento návod ukazuje, jak můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složený ovládací prvek a hostujte ho v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a formuláře pomocí <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2f270-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="2f270-104">V tomto návodu budete implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> , který obsahuje dva podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2f270-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="2f270-105"><xref:System.Windows.Controls.UserControl> Zobrazí trojrozměrného kužel (3D).</span><span class="sxs-lookup"><span data-stu-id="2f270-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="2f270-106">Vykreslování 3D objekty je mnohem snazší díky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] než s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f270-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="2f270-107">Proto je vhodné na hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> třídy za účelem vytvoření 3D grafiky v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f270-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="2f270-108">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="2f270-108">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="2f270-109">Vytváří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="2f270-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

-   <span data-ttu-id="2f270-110">Vytvoření projektu Windows Forms hostitele.</span><span class="sxs-lookup"><span data-stu-id="2f270-110">Creating the Windows Forms host project.</span></span>

-   <span data-ttu-id="2f270-111">Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="2f270-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f270-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f270-112">Prerequisites</span></span>

<span data-ttu-id="2f270-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="2f270-113">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="2f270-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2f270-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="2f270-115">Vytvořte uživatelský ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2f270-115">Create the UserControl</span></span>

1.  <span data-ttu-id="2f270-116">Vytvoření **Knihovna uživatelských ovládacích prvků WPF** projekt s názvem `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="2f270-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2.  <span data-ttu-id="2f270-117">Otevřete UserControl1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f270-117">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

3.  <span data-ttu-id="2f270-118">Generovaného kódu nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2f270-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="2f270-119">Tento kód definuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> , který obsahuje dva podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2f270-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="2f270-120">První podřízený ovládací prvek je <xref:System.Windows.Controls.Label?displayProperty=nameWithType> ovládacího prvku; druhá je <xref:System.Windows.Controls.Viewport3D> ovládací prvek, který zobrazí 3D kužel.</span><span class="sxs-lookup"><span data-stu-id="2f270-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="2f270-121">Vytvoření projektu hostitel</span><span class="sxs-lookup"><span data-stu-id="2f270-121">Create the host project</span></span>

1.  <span data-ttu-id="2f270-122">Přidat **aplikace WPF (.NET Framework)** projekt s názvem `WpfUserControlHost` do řešení.</span><span class="sxs-lookup"><span data-stu-id="2f270-122">Add a **WPF App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="2f270-123">Další informace najdete v tématu [jak: Vytvoření nového projektu aplikace WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="2f270-123">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>

2.  <span data-ttu-id="2f270-124">V **Průzkumníka řešení**, přidejte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="2f270-124">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3.  <span data-ttu-id="2f270-125">Přidat odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení:</span><span class="sxs-lookup"><span data-stu-id="2f270-125">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    -   <span data-ttu-id="2f270-126">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="2f270-126">PresentationCore</span></span>

    -   <span data-ttu-id="2f270-127">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="2f270-127">PresentationFramework</span></span>

    -   <span data-ttu-id="2f270-128">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="2f270-128">WindowsBase</span></span>

4.  <span data-ttu-id="2f270-129">Přidejte odkaz na `HostingWpfUserControlInWf` projektu.</span><span class="sxs-lookup"><span data-stu-id="2f270-129">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5.  <span data-ttu-id="2f270-130">V Průzkumníku řešení nastavte `WpfUserControlHost` projekt jako spouštěný projekt.</span><span class="sxs-lookup"><span data-stu-id="2f270-130">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="2f270-131">Hostování uživatelský ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2f270-131">Host the UserControl</span></span>

1.  <span data-ttu-id="2f270-132">V Návrháři formulářů Windows otevřete Form1.</span><span class="sxs-lookup"><span data-stu-id="2f270-132">In the Windows Forms Designer, open Form1.</span></span>

2.  <span data-ttu-id="2f270-133">V okně Vlastnosti klikněte na tlačítko **události**a potom dvakrát klikněte <xref:System.Windows.Forms.Form.Load> událost k vytvoření obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="2f270-133">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="2f270-134">Otevře se Editor kódu do nově vytvořeného `Form1_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="2f270-134">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3.  <span data-ttu-id="2f270-135">Nahraďte kód v Form1.cs s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="2f270-135">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="2f270-136">`Form1_Load` Obslužná rutina události vytvoří instanci `UserControl1` a přidá itto <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku kolekce podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2f270-136">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="2f270-137"><xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je přidán do kolekce podřízených ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="2f270-137">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4.  <span data-ttu-id="2f270-138">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2f270-138">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f270-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f270-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="2f270-140">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f270-140">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="2f270-141">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f270-141">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="2f270-142">Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="2f270-142">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="2f270-143">Hostování složeného ovládacího prvku WPF ve Windows Forms vzorku</span><span class="sxs-lookup"><span data-stu-id="2f270-143">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)