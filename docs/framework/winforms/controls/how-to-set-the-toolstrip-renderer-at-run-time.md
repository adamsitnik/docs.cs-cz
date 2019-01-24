---
title: 'Postupy: Nastavení vykreslovacího modulu prvku ToolStrip za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripManager class [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 525e2347-0804-49aa-b9a3-9b2cabbf1c35
ms.openlocfilehash: ddedae5bd7a58b7d8babca7f92bb261a10d2ddee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511992"
---
# <a name="how-to-set-the-toolstrip-renderer-at-run-time"></a><span data-ttu-id="f6226-102">Postupy: Nastavení vykreslovacího modulu prvku ToolStrip za běhu</span><span class="sxs-lookup"><span data-stu-id="f6226-102">How to: Set the ToolStrip Renderer at Run Time</span></span>
<span data-ttu-id="f6226-103">Můžete přizpůsobit vzhled vašich <xref:System.Windows.Forms.ToolStrip> ovládacího prvku tak, že vytvoříte vlastní `ProfessionalColorTable` třídy.</span><span class="sxs-lookup"><span data-stu-id="f6226-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> control by creating a custom `ProfessionalColorTable` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6226-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6226-104">Example</span></span>  
 <span data-ttu-id="f6226-105">Následující příklad kódu ukazuje, jak vytvořit vlastní `ProfessionalColorTable` třídy.</span><span class="sxs-lookup"><span data-stu-id="f6226-105">The following code example demonstrates how to create a custom `ProfessionalColorTable` class.</span></span> <span data-ttu-id="f6226-106">Tato třída definuje pro přechody <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f6226-106">This class defines gradients for a <xref:System.Windows.Forms.MenuStrip> and a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
 <span data-ttu-id="f6226-107">Použít tento příklad kódu, kompilaci a spuštění aplikace a pak klikněte na **změnit barvy** použít přechody definovaný ve vlastní `ProfessionalColorTable` třídy.</span><span class="sxs-lookup"><span data-stu-id="f6226-107">To use this code example, compile and run the application, and then click **Change Colors** to apply the gradients defined in the custom `ProfessionalColorTable` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="defining-a-custom-professionalcolortable-class"></a><span data-ttu-id="f6226-108">Definování vlastní professionalcolortable – třída</span><span class="sxs-lookup"><span data-stu-id="f6226-108">Defining a Custom ProfessionalColorTable class</span></span>  
 <span data-ttu-id="f6226-109">Vlastní přechody jsou definovány v `CustomProfessionalColors` třídy.</span><span class="sxs-lookup"><span data-stu-id="f6226-109">The custom gradients are defined in the `CustomProfessionalColors` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#30)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#30)]  
  
## <a name="assigning-a-custom-renderer"></a><span data-ttu-id="f6226-110">Přiřazení vlastní zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="f6226-110">Assigning a Custom Renderer</span></span>  
 <span data-ttu-id="f6226-111">Vytvořte nový `ToolStripProfessionalRenderer` s `CustomProfessionalColors` třídy a přiřaďte ho <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f6226-111">Create a new `ToolStripProfessionalRenderer` with a `CustomProfessionalColors` class, and assign it to the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#22)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6226-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f6226-112">Compiling the Code</span></span>  
 <span data-ttu-id="f6226-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f6226-113">This example requires:</span></span>  
  
-   <span data-ttu-id="f6226-114">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f6226-114">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f6226-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f6226-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f6226-116">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f6226-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f6226-117">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f6226-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6226-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6226-118">See also</span></span>
- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.ProfessionalColorTable>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [<span data-ttu-id="f6226-119">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f6226-119">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
