---
title: ToolBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: 1cbb8d54a544b70b4a484c06c6bb2e9ca25029da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156322"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="9b944-102">ToolBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9b944-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="9b944-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b944-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="9b944-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b944-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9b944-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9b944-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="9b944-106">Části panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="9b944-106">ToolBar Parts</span></span>  
 <span data-ttu-id="9b944-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b944-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="9b944-108">Část</span><span class="sxs-lookup"><span data-stu-id="9b944-108">Part</span></span>|<span data-ttu-id="9b944-109">Type</span><span class="sxs-lookup"><span data-stu-id="9b944-109">Type</span></span>|<span data-ttu-id="9b944-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9b944-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9b944-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="9b944-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="9b944-112">Objekt, který obsahuje ovládací prvky na <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="9b944-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="9b944-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="9b944-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="9b944-114">Objekt, který obsahuje ovládací prvky, které jsou v oblasti přetečení <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="9b944-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="9b944-115">Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar>, šablona může obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="9b944-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="9b944-116">( <xref:System.Windows.Controls.ItemsPresenter> Zobrazuje každou položku v <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).</span><span class="sxs-lookup"><span data-stu-id="9b944-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="9b944-117">Pokud <xref:System.Windows.Controls.ItemsPresenter> není za přímé podřízeného člena <xref:System.Windows.Controls.ScrollViewer>, je třeba zadat <xref:System.Windows.Controls.ItemsPresenter> názvu, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="9b944-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="9b944-118">Stavy panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="9b944-118">ToolBar States</span></span>  
 <span data-ttu-id="9b944-119">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b944-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="9b944-120">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="9b944-120">VisualState Name</span></span>|<span data-ttu-id="9b944-121">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9b944-121">VisualStateGroup Name</span></span>|<span data-ttu-id="9b944-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9b944-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9b944-123">Platné</span><span class="sxs-lookup"><span data-stu-id="9b944-123">Valid</span></span>|<span data-ttu-id="9b944-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9b944-124">ValidationStates</span></span>|<span data-ttu-id="9b944-125">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="9b944-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9b944-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9b944-126">InvalidFocused</span></span>|<span data-ttu-id="9b944-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9b944-127">ValidationStates</span></span>|<span data-ttu-id="9b944-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="9b944-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9b944-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9b944-129">InvalidUnfocused</span></span>|<span data-ttu-id="9b944-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9b944-130">ValidationStates</span></span>|<span data-ttu-id="9b944-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="9b944-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="9b944-132">Příklad šablony ControlTemplate nástrojů</span><span class="sxs-lookup"><span data-stu-id="9b944-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="9b944-133">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b944-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="9b944-134">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="9b944-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9b944-135">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9b944-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b944-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b944-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9b944-137">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="9b944-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9b944-138">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9b944-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9b944-139">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9b944-139">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="9b944-140">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9b944-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
