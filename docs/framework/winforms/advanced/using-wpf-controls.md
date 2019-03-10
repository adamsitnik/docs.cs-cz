---
title: Používání ovládacích prvků WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 24b88e456628c5a0bdc3cded60b0e52a92057851
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713797"
---
# <a name="using-wpf-controls"></a><span data-ttu-id="ff854-102">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="ff854-102">Using WPF Controls</span></span>
<span data-ttu-id="ff854-103">Ovládací prvky Windows Presentation Foundation (WPF) můžete použít ve svých aplikacích pomocí formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ff854-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="ff854-104">I když jsou dvě technologie jiné zobrazení, jejich vzájemnou spolupráci plynule.</span><span class="sxs-lookup"><span data-stu-id="ff854-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="ff854-105">Návrhář formulářů Windows poskytuje vizuální návrhové prostředí pro hostování ovládacích prvků Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="ff854-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="ff854-106">Ovládací prvek WPF je hostitelem speciální ovládacího prvku Windows Forms, který je pojmenován <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="ff854-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="ff854-107">Tento ovládací prvek umožňuje ovládacího prvku WPF se účastnit rozložení formuláře a přijímat zprávy klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="ff854-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="ff854-108">V době návrhu, můžete uspořádat <xref:System.Windows.Forms.Integration.ElementHost> řídit stejně jako libovolný ovládací prvek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ff854-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="ff854-109">Můžete také použít ovládací prvky Windows Forms ve svých aplikacích založeného na WPF.</span><span class="sxs-lookup"><span data-stu-id="ff854-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="ff854-110">Další informace najdete v tématu [návrh XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ff854-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff854-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ff854-111">In This Section</span></span>  
 [<span data-ttu-id="ff854-112">Postupy: Kopírování a vložení ovládacího prvku ElementHost během návrhu</span><span class="sxs-lookup"><span data-stu-id="ff854-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="ff854-113">Ukazuje, jak zkopírovat ovládací prvek Windows Presentation Foundation ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="ff854-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="ff854-114">Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="ff854-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="ff854-115">Ukazuje způsob použití funkcí rozložení Windows Forms, jako je například ukotvení a zarovnávacích čar, k uspořádání ovládacích prvků Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="ff854-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>
  
 [<span data-ttu-id="ff854-116">Návod: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="ff854-116">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="ff854-117">Ukazuje, jak vytvořit ovládací prvek Windows Presentation Foundation pro použití ve svých aplikacích pomocí formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ff854-117">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>
  
 [<span data-ttu-id="ff854-118">Návod: Přiřazení obsahu WPF ve Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="ff854-118">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="ff854-119">Ukazuje, jak vybrat typy ovládacích prvků Windows Presentation Foundation, který chcete zobrazit ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="ff854-119">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="ff854-120">Návod: Určení stylu obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="ff854-120">Walkthrough: Styling WPF Content</span></span>](walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="ff854-121">Zobrazuje pracovní postupy mezi návrháři formulářů Windows a [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] pro aplikování stylů pro ovládací prvky Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="ff854-121">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ff854-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ff854-122">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="ff854-123">Popisuje třídy, která vám pomůže hostitelských ovládacích prvků Windows Presentation Foundation ve svých aplikacích pomocí formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ff854-123">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="ff854-124">Popisuje třídy, která vám pomůže hostitelské ovládací prvky Windows Forms v aplikaci založené na Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="ff854-124">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff854-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ff854-125">Related Sections</span></span>  
 [<span data-ttu-id="ff854-126">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="ff854-126">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="ff854-127">Popisuje interoperabilitu mezi Windows Presentation Foundation a Windows Forms technologií.</span><span class="sxs-lookup"><span data-stu-id="ff854-127">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="ff854-128">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ff854-128">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 <span data-ttu-id="ff854-129">Popisuje postup návrhu ovládacích prvků Windows Presentation Foundation v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ff854-129">Describes how to design Windows Presentation Foundation controls in Visual Studio.</span></span>
