---
title: 'Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 6f36914387519b027fcf4cb6bf1e7654e551b3eb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328020"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="15557-102">Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="15557-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="15557-103">Můžete zarovnání a roztažení ovládacích prvků <xref:System.Windows.Forms.TableLayoutPanel> s <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="15557-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15557-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="15557-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="15557-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="15557-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="15557-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="15557-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="15557-107">Zarovnání a roztažení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="15557-107">To align and stretch a control</span></span>  
  
1. <span data-ttu-id="15557-108">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="15557-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="15557-109">Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do buňky levého horního <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15557-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="15557-110"><xref:System.Windows.Forms.Button> Ovládací prvek je uprostřed buňky.</span><span class="sxs-lookup"><span data-stu-id="15557-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3. <span data-ttu-id="15557-111">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="15557-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="15557-112"><xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly šířka buňky.</span><span class="sxs-lookup"><span data-stu-id="15557-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4. <span data-ttu-id="15557-113">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="15557-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="15557-114"><xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly výška buňky.</span><span class="sxs-lookup"><span data-stu-id="15557-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5. <span data-ttu-id="15557-115">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="15557-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="15557-116"><xref:System.Windows.Forms.Button> Ovládací prvek roztáhne a vyplní buňky.</span><span class="sxs-lookup"><span data-stu-id="15557-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6. <span data-ttu-id="15557-117">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="15557-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="15557-118"><xref:System.Windows.Forms.Button> Ovládací prvek vrátí na původní velikost a přesune do levého horního rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="15557-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="15557-119">**Návrháře formulářů Windows** nastavil <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="15557-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7. <span data-ttu-id="15557-120">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="15557-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="15557-121"><xref:System.Windows.Forms.Button> Ovládacího prvku přesune do pravého dolního rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="15557-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8. <span data-ttu-id="15557-122">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="15557-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="15557-123"><xref:System.Windows.Forms.Button> Ovládacího prvku přesune na střed buňku.</span><span class="sxs-lookup"><span data-stu-id="15557-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15557-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15557-124">See also</span></span>

- [<span data-ttu-id="15557-125">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="15557-125">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
