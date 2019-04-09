---
title: 'Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: cfac0d02ec1effdd521ca68ae4cb44b5a5a7a597
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124849"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="bd48c-102">Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="bd48c-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="bd48c-103">Vzhledem k tomu, Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek zobrazuje uzly hierarchické způsobem, při přidávání uzlu musí věnovat pozornost na to, co je svého nadřazeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="bd48c-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="bd48c-104">Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.TreeView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd48c-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="bd48c-105">Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bd48c-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd48c-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="bd48c-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bd48c-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="bd48c-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bd48c-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="bd48c-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="bd48c-109">K přidávání a odebírání uzlů v Návrháři</span><span class="sxs-lookup"><span data-stu-id="bd48c-109">To add or remove nodes in the designer</span></span>  
  
1.  <span data-ttu-id="bd48c-110">Vyberte <xref:System.Windows.Forms.TreeView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd48c-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="bd48c-111">V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bd48c-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="bd48c-112">**TreeNode – Editor** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="bd48c-112">The **TreeNode Editor** appears.</span></span>  
  
3.  <span data-ttu-id="bd48c-113">Přidání uzlů, musí existovat kořenový uzel; Pokud neexistuje, musíte nejprve přidat kořenovou kliknutím **přidat kořenový** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bd48c-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="bd48c-114">Potom můžete výběrem kořenové nebo druhý uzel a kliknutím na Přidat podřízené uzly **přidat podřízenou položku** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bd48c-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4.  <span data-ttu-id="bd48c-115">Odstranit uzly, vyberte uzel odstranit a potom klikněte na tlačítko **odstranit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bd48c-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd48c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd48c-116">See also</span></span>

- [<span data-ttu-id="bd48c-117">TreeView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="bd48c-117">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="bd48c-118">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="bd48c-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="bd48c-119">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="bd48c-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="bd48c-120">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="bd48c-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="bd48c-121">Postupy: Určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="bd48c-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="bd48c-122">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bd48c-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
