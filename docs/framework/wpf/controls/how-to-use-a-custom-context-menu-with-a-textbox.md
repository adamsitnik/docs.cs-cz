---
title: 'Postupy: Použití vlastní místní nabídky u objektu TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: 5b1b0ea569831361c4680102e8229fe3755bffda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742338"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a><span data-ttu-id="9774e-102">Postupy: Použití vlastní místní nabídky u objektu TextBox</span><span class="sxs-lookup"><span data-stu-id="9774e-102">How to: Use a Custom Context Menu with a TextBox</span></span>
<span data-ttu-id="9774e-103">Tento příklad ukazuje, jak definovat a implementovat jednoduchý vlastní místní nabídky pro <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="9774e-103">This example shows how to define and implement a simple custom context menu for a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9774e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9774e-104">Example</span></span>  
 <span data-ttu-id="9774e-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad definuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který obsahuje vlastní místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="9774e-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example defines a <xref:System.Windows.Controls.TextBox> control that includes a custom context menu.</span></span>  
  
 <span data-ttu-id="9774e-106">V místní nabídce je definován pomocí <xref:System.Windows.Controls.ContextMenu> elementu.</span><span class="sxs-lookup"><span data-stu-id="9774e-106">The context menu is defined using a <xref:System.Windows.Controls.ContextMenu> element.</span></span>  <span data-ttu-id="9774e-107">V místní nabídce, samotné se skládá z řady <xref:System.Windows.Controls.MenuItem> elementy a <xref:System.Windows.Controls.Separator> elementy.</span><span class="sxs-lookup"><span data-stu-id="9774e-107">The context menu itself consists of a series of <xref:System.Windows.Controls.MenuItem> elements and <xref:System.Windows.Controls.Separator> elements.</span></span>  <span data-ttu-id="9774e-108">Každý <xref:System.Windows.Controls.MenuItem> element definuje příkaz v místní nabídce; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atribut definuje zobrazovaný text pro příkaz nabídky a <xref:System.Windows.Controls.MenuItem.Click> atribut určuje metodu obslužné rutiny pro každou položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="9774e-108">Each <xref:System.Windows.Controls.MenuItem> element defines a command in the context menu; the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribute defines the display text for the menu command, and the <xref:System.Windows.Controls.MenuItem.Click> attribute specifies a handler method for each menu item.</span></span>  <span data-ttu-id="9774e-109"><xref:System.Windows.Controls.Separator> Element pouze zajistí, že dělicí řádku mají být vykresleny mezi položkami nabídky předchozí a dalších.</span><span class="sxs-lookup"><span data-stu-id="9774e-109">The <xref:System.Windows.Controls.Separator> element simply causes a separating line to be rendered between the previous and subsequent menu items.</span></span>  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a><span data-ttu-id="9774e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9774e-110">Example</span></span>  
 <span data-ttu-id="9774e-111">Následující příklad ukazuje implementaci kód pro předchozí definice kontextové nabídky, stejně jako kód, který povolí nebo zakáže v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="9774e-111">The following example shows the implementation code for the preceding context menu definition, as well as the code that enables and disables the context menu.</span></span>  <span data-ttu-id="9774e-112"><xref:System.Windows.Controls.ContextMenu.Opened> Událost se používá k dynamicky povolit nebo zakázat některé příkazy v závislosti na aktuální stav <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="9774e-112">The <xref:System.Windows.Controls.ContextMenu.Opened> event is used to dynamically enable or disable certain commands depending on the current state of the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="9774e-113">Chcete-li obnovit výchozí místní nabídku, použijte <xref:System.Windows.DependencyObject.ClearValue%2A> metoda smazat hodnotu <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9774e-113">To restore the default context menu, use the <xref:System.Windows.DependencyObject.ClearValue%2A> method to clear the value of the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property.</span></span>  <span data-ttu-id="9774e-114">Chcete-li zcela zakázat v místní nabídce, nastavte <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost odkaz s hodnotou null (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9774e-114">To disable the context menu altogether, set the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property to a null reference (`Nothing` in Visual Basic).</span></span>  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a><span data-ttu-id="9774e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9774e-115">See also</span></span>
- [<span data-ttu-id="9774e-116">Použití kontroly pravopisu s místní nabídkou</span><span class="sxs-lookup"><span data-stu-id="9774e-116">Use Spell Checking with a Context Menu</span></span>](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)
- [<span data-ttu-id="9774e-117">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="9774e-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="9774e-118">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="9774e-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
