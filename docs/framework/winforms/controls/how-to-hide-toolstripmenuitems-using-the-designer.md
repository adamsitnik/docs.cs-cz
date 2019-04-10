---
title: 'Postupy: Skrytí ToolStripMenuItems pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 31c597a0e2cbf41484f19c8d4179823e9fb929ba
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317672"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="ec634-102">Postupy: Skrytí ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="ec634-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="ec634-103">Skrytí položek nabídky je způsob, jak ovládací prvek uživatelského rozhraní (UI) aplikace a omezit uživatelských příkazů.</span><span class="sxs-lookup"><span data-stu-id="ec634-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="ec634-104">Často můžete skrýt celou nabídku, když jsou všechny položky nabídky na něm není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ec634-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="ec634-105">To představuje méně rozptýlení pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="ec634-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="ec634-106">Kromě toho můžete chtít skrýt i zakázat nabídky nebo položku nabídky, protože skrytí samostatně nebrání uživateli přístup k příkazu nabídky pomocí klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="ec634-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="ec634-107">Další informace o deaktivace položek nabídky, naleznete v tématu [jak: Zákaz ToolStripMenuItems pomocí návrháře](how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="ec634-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec634-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ec634-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ec634-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ec634-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ec634-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ec634-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="ec634-111">Chcete-li skrýt nabídek nejvyšší úrovně a jeho podnabídky položek</span><span class="sxs-lookup"><span data-stu-id="ec634-111">To hide a top-level menu and its submenu items</span></span>  
  
1. <span data-ttu-id="ec634-112">Vyberte položku nejvyšší úrovně nabídky a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Visible%2A> nebo <xref:System.Windows.Forms.ToolStripItem.Available%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="ec634-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="ec634-113">Když skryjete položky nabídek nejvyšší úrovně, všechny položky nabídky v rámci této nabídky jsou rovněž skryté.</span><span class="sxs-lookup"><span data-stu-id="ec634-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="ec634-114">Pokud kliknete na jiném zařízení, než na <xref:System.Windows.Forms.MenuStrip> po nastavení <xref:System.Windows.Forms.ToolStripItem.Visible%2A> k `false`, celý nabídka nejvyšší úrovně a její podnabídku položky zmizí z formuláře, tedy zobrazí vliv za běhu akce.</span><span class="sxs-lookup"><span data-stu-id="ec634-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="ec634-115">Aby se zobrazila položka skrytá nabídek nejvyšší úrovně v době návrhu, klikněte na <xref:System.Windows.Forms.MenuStrip> v **komponent**v **Osnova dokumentu**, nebo v horní části mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="ec634-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec634-116">Jen zřídka se skrýt celou nabídku s výjimkou více nabídky podřízené ve scénáři sloučení dokumentu (MDI interface).</span><span class="sxs-lookup"><span data-stu-id="ec634-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="ec634-117">Chcete-li skrýt položku podnabídky</span><span class="sxs-lookup"><span data-stu-id="ec634-117">To hide a submenu item</span></span>  
  
1. <span data-ttu-id="ec634-118">Vyberte položku dílčí nabídky a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="ec634-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="ec634-119">Při skrytí položky podnabídky zůstává viditelná ve formuláři v době návrhu tak, aby ji snadno vybrat pro další práci.</span><span class="sxs-lookup"><span data-stu-id="ec634-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="ec634-120">Ve skutečnosti to bude skrytá za běhu.</span><span class="sxs-lookup"><span data-stu-id="ec634-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec634-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec634-121">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="ec634-122">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="ec634-122">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="ec634-123">Postupy: Zakázání ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="ec634-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
