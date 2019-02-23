---
title: TableLayoutPanel – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
ms.openlocfilehash: 9813a1b969d0232ec842b91385d0ad893b71c0d6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747324"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="8bbf2-102">TableLayoutPanel – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8bbf2-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="8bbf2-103"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek uspořádá její obsah do mřížky.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="8bbf2-104">Protože je prováděna rozložení i v době návrhu a běhu, můžete změnit dynamicky se změnami prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="8bbf2-105">To umožňuje ovládací prvky v panelu proporcionálně velikost, tak můžou reagovat na změny, jako je například změna velikosti nadřazeného ovládacího prvku nebo text délka mění kvůli lokalizace.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8bbf2-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8bbf2-106">In This Section</span></span>  
 [<span data-ttu-id="8bbf2-107">Přehled ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-107">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="8bbf2-108">Představuje obecné koncepty <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek, který vám umožní vytvořit rozložení řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="8bbf2-109">Doporučené postupy pro ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-109">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="8bbf2-110">Popisuje doporučení, která vám pomohou maximálně využívat funkce rozložení <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="8bbf2-111">Chování AutoSize v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="8bbf2-112">Popisuje způsoby <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek podporuje automatické velikosti chování.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="8bbf2-113">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="8bbf2-114">Ukazuje, jak a ukotvení podřízených ovládacích prvků v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="8bbf2-115">Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci</span><span class="sxs-lookup"><span data-stu-id="8bbf2-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="8bbf2-116">Ukazuje použití <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na formulář, jež odpovídá lokalizaci vytvářet.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="8bbf2-117">Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat</span><span class="sxs-lookup"><span data-stu-id="8bbf2-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="8bbf2-118">Ukazuje použití <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na formulář, který odpovídá Změna velikosti vytvářet.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1.  [<span data-ttu-id="8bbf2-119">Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-119">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [<span data-ttu-id="8bbf2-120">Postupy: Rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-120">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [<span data-ttu-id="8bbf2-121">Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-121">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="8bbf2-122">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8bbf2-122">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="reference"></a><span data-ttu-id="8bbf2-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="8bbf2-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="8bbf2-124">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="8bbf2-125">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.TableLayoutSettings> typu.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="8bbf2-126">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8bbf2-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8bbf2-127">Related Sections</span></span>  
 [<span data-ttu-id="8bbf2-128">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="8bbf2-128">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="8bbf2-129">Poskytuje přehled o tématech vztahujících se k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="8bbf2-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="8bbf2-130">Viz také [lokalizace aplikace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="8bbf2-130">Also see [Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span></span>
