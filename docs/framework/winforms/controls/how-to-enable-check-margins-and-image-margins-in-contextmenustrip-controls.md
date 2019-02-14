---
title: 'Postupy: Povolení okrajů pro zaškrtnutí a okrajů obrázků v ovládacích prvcích ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ShowCheckMargin property [Windows Forms]
- ShowImageMargin property [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: eb584e71-59da-4012-aaca-dbe1c7c7a156
ms.openlocfilehash: d38b905eab1907a17375271b458d93a1383efa69
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260930"
---
# <a name="how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls"></a><span data-ttu-id="48d21-102">Postupy: Povolení okrajů pro zaškrtnutí a okrajů obrázků v ovládacích prvcích ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="48d21-102">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>
<span data-ttu-id="48d21-103">Můžete přizpůsobit <xref:System.Windows.Forms.ToolStripMenuItem> objekty ve vaší <xref:System.Windows.Forms.MenuStrip> ovládací prvek s značky zaškrtnutí a vlastní Image.</span><span class="sxs-lookup"><span data-stu-id="48d21-103">You can customize the <xref:System.Windows.Forms.ToolStripMenuItem> objects in your <xref:System.Windows.Forms.MenuStrip> control with check marks and custom images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48d21-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="48d21-104">Example</span></span>  
 <span data-ttu-id="48d21-105">Následující příklad kódu ukazuje, jak vytvořit položky nabídky, které mají značky zaškrtnutí a vlastní Image.</span><span class="sxs-lookup"><span data-stu-id="48d21-105">The following code example demonstrates how to create menu items that have check marks and custom images.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
 <span data-ttu-id="48d21-106">Nastavte <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> vlastnosti, které chcete určit, když se ve vašich položkách nabídky zobrazí značky zaškrtnutí a vlastní Image.</span><span class="sxs-lookup"><span data-stu-id="48d21-106">Set the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> properties to specify when check marks and custom images appear in your menu items.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48d21-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="48d21-107">Compiling the Code</span></span>  
 <span data-ttu-id="48d21-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="48d21-108">This example requires:</span></span>  
  
-   <span data-ttu-id="48d21-109">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="48d21-109">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="48d21-110">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="48d21-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="48d21-111">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="48d21-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d21-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48d21-112">See also</span></span>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="48d21-113">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="48d21-113">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
