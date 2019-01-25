---
title: 'Postupy: Nastavení pozadí panelu Windows Forms pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: be0359e13bcab868374189c6b42df392327b8eb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645057"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="b125d-102">Postupy: Nastavení pozadí panelu Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="b125d-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="b125d-103">Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek mohl zobrazit barvu pozadí a obrázek na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b125d-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="b125d-104"><xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro ovládací prvky, které jsou obsaženy v panelu, jako je například popisky a přepínače.</span><span class="sxs-lookup"><span data-stu-id="b125d-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="b125d-105">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavená, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní všechny panelu.</span><span class="sxs-lookup"><span data-stu-id="b125d-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="b125d-106">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je hodnota nastavena, obrázek se zobrazí za ovládací prvky, které jsou obsaženy v panelu.</span><span class="sxs-lookup"><span data-stu-id="b125d-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="b125d-107">Následující postup vyžaduje, **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b125d-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="b125d-108">Informace o tom, jak nastavit takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b125d-108">For information about how to set up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b125d-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="b125d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b125d-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b125d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b125d-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b125d-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="b125d-112">Chcete-li nastavit na pozadí v Návrháři formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="b125d-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="b125d-113">Vyberte <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b125d-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="b125d-114">V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost pro zobrazení okna se třemi kartami.</span><span class="sxs-lookup"><span data-stu-id="b125d-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="b125d-115">Vyberte **vlastní** kartu k zobrazení palety barev.</span><span class="sxs-lookup"><span data-stu-id="b125d-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="b125d-116">Vyberte **webové** nebo **systému** kartě zobrazíte seznam předdefinovaných názvů pro barvy a pak vyberte barvu.</span><span class="sxs-lookup"><span data-stu-id="b125d-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="b125d-117">V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b125d-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="b125d-118">V **otevřít** dialogovém okně vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="b125d-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b125d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b125d-119">See also</span></span>
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="b125d-120">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="b125d-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [<span data-ttu-id="b125d-121">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="b125d-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [<span data-ttu-id="b125d-122">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="b125d-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
