---
title: 'Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 5fd1caabbc876d5b71deae2d9b1b9cf232d17700
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723241"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="bdfe9-102">Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="bdfe9-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="bdfe9-103">Nástup <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku Windows Forms vývojářům umožňuje poskytovat koncovým uživatelům s jednoduchou datovou navigaci a manipulaci s uživatelským rozhraním ve formulářích vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="bdfe9-104"><xref:System.Windows.Forms.BindingNavigator> Je ovládací prvek <xref:System.Windows.Forms.ToolStrip> předkonfigurované ovládacím prvkem tlačítka pro přechod na první, poslední, další a předchozí záznam v datové sady, jakož i tlačítka můžete přidávat a odstraňovat záznamy.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="bdfe9-105">Přidání tlačítek do <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je snadné, protože se jedná <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="bdfe9-106">Příklady najdete v tématu [jak: Přidat načíst, uložit, a tlačítka Storno pro Windows Forms BindingNavigator – ovládací prvek](load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="bdfe9-106">For examples, see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
 <span data-ttu-id="bdfe9-107">Pro každé tlačítko na <xref:System.Windows.Forms.BindingNavigator> řídit, neexistuje odpovídající člen <xref:System.Windows.Forms.BindingSource> komponenta, která umožňuje programově stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="bdfe9-108">Například <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metodu <xref:System.Windows.Forms.BindingSource> komponenty, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metody a tak dále.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="bdfe9-109">V důsledku toho povolení <xref:System.Windows.Forms.BindingNavigator> ovládací prvek pro procházení záznamů dat je jednoduše nastavení jeho <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnosti na příslušné <xref:System.Windows.Forms.BindingSource> komponenty ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="bdfe9-110">K nastavení ovládacího prvku BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="bdfe9-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="bdfe9-111">Přidat <xref:System.Windows.Forms.BindingSource> součást s názvem `bindingSource1` a dva <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `textBox1` a `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="bdfe9-112">Vytvoření vazby `bindingSource1` k datům a ovládací prvky textbox `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="bdfe9-113">Chcete-li to provést, vložte následující kód do formuláře a volání `LoadData` z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metody zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="bdfe9-114">Přidat <xref:System.Windows.Forms.BindingNavigator> ovládací prvek s názvem `bindingNavigator1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="bdfe9-115">Nastavte <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost `bindingNavigator1` k `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="bdfe9-116">Můžete to provést pomocí návrháře nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="bdfe9-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfe9-117">Example</span></span>  
 <span data-ttu-id="bdfe9-118">Následující příklad kódu je kompletní příklad pro kroků uvedených dříve v tomto.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bdfe9-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bdfe9-119">Compiling the Code</span></span>  
 <span data-ttu-id="bdfe9-120">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bdfe9-120">This example requires:</span></span>  
  
-   <span data-ttu-id="bdfe9-121">Odkazy na sestavení systému, System.Data, System.Drawing, System.Windows.Forms a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="bdfe9-122">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bdfe9-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bdfe9-123">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="bdfe9-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfe9-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdfe9-124">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="bdfe9-125">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="bdfe9-125">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="bdfe9-126">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bdfe9-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
