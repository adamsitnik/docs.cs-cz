---
title: 'Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: 6e2e89baf17c63ea3ad4814cd761449baeb78405
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627509"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="2fac7-102">Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="2fac7-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="2fac7-103">Značky vložení v <xref:System.Windows.Forms.ListView> ovládací prvek zobrazuje uživatele, kteří bodu vloženy Přetahované položky.</span><span class="sxs-lookup"><span data-stu-id="2fac7-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="2fac7-104">Když uživatel přetáhne položku do bodu mezi dvě další položky, značky vložení ukazuje očekávané nové umístění položky.</span><span class="sxs-lookup"><span data-stu-id="2fac7-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fac7-105">Označit funkce vložení dostupná pouze na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2fac7-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2fac7-106">Ve starších operačních systémech jakýkoli kód týkající se značky vložení nemá žádný vliv a značky vložení nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="2fac7-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="2fac7-107">Další informace naleznete v tématu <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="2fac7-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="2fac7-108">Následující obrázek ukazuje značky vložení:</span><span class="sxs-lookup"><span data-stu-id="2fac7-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="2fac7-109">![Značky vložení ListView](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="2fac7-109">![A ListView Insertion Mark](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="2fac7-110">Následující příklad kódu ukazuje, jak tuto funkci používat.</span><span class="sxs-lookup"><span data-stu-id="2fac7-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fac7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fac7-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2fac7-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2fac7-112">Compiling the Code</span></span>  
 <span data-ttu-id="2fac7-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2fac7-113">This example requires:</span></span>  
  
-   <span data-ttu-id="2fac7-114">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2fac7-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2fac7-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2fac7-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2fac7-116">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="2fac7-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="2fac7-117">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2fac7-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fac7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fac7-118">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="2fac7-119">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="2fac7-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="2fac7-120">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="2fac7-120">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="2fac7-121">Funkce Windows XP a ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2fac7-121">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
- [<span data-ttu-id="2fac7-122">Návod: Operace a přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2fac7-122">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
