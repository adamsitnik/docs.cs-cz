---
title: 'Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: 6bd2c0aca7e24ed903e31f1c27e7e173ade6086b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619951"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="5af82-102">Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="5af82-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="5af82-103">Data můžete jednoduše sdílet mezi formuláři pomocí <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="5af82-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="5af82-104">Chcete třeba zobrazit jeden formulář jen pro čtení, která shrnuje data zdroje dat a jiné Upravitelný formulář, který obsahuje podrobné informace o aktuálně vybrané položky ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="5af82-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="5af82-105">Tento příklad ukazuje tento scénář.</span><span class="sxs-lookup"><span data-stu-id="5af82-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5af82-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5af82-106">Example</span></span>  
 <span data-ttu-id="5af82-107">Následující příklad kódu ukazuje, jak sdílet <xref:System.Windows.Forms.BindingSource> a vázaných dat mezi formuláři.</span><span class="sxs-lookup"><span data-stu-id="5af82-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="5af82-108">V tomto příkladu, sdílený <xref:System.Windows.Forms.BindingSource> je předán konstruktoru podřízeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="5af82-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="5af82-109">Podřízený formulář umožňuje uživateli upravit data pro aktuálně vybrané položky v hlavním formuláři.</span><span class="sxs-lookup"><span data-stu-id="5af82-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5af82-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Událost pro <xref:System.Windows.Forms.BindingSource> komponenta je zpracována v příklad k zajištění toho, že dvě různými formami zůstaly synchronizované.</span><span class="sxs-lookup"><span data-stu-id="5af82-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="5af82-111">Další informace o tom, proč se to, najdete v článku [jak: Zajištění více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="5af82-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5af82-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5af82-112">Compiling the Code</span></span>  
 <span data-ttu-id="5af82-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5af82-113">This example requires:</span></span>  
  
-   <span data-ttu-id="5af82-114">Odkazy na sestavení systému, System.Windows.Forms, System.Drawing, System.Data a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="5af82-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="5af82-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5af82-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5af82-116">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="5af82-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="5af82-117">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5af82-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af82-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5af82-118">See also</span></span>
- [<span data-ttu-id="5af82-119">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="5af82-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="5af82-120">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="5af82-120">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)
- [<span data-ttu-id="5af82-121">Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="5af82-121">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
