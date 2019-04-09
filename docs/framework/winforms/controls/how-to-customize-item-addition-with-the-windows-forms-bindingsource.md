---
title: 'Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 0a2f8491d0f027ca834257e2ec3a08d0b8bdb7ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129543"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="647d4-102">Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="647d4-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="647d4-103">Při použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby ovládacího prvku Windows Forms ke zdroji dat bude možná potřeba k přizpůsobení vytvoření nové položky.</span><span class="sxs-lookup"><span data-stu-id="647d4-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="647d4-104"><xref:System.Windows.Forms.BindingSource> Komponenta odešle toto jednoduché tím, že poskytuje <xref:System.Windows.Forms.BindingSource.AddingNew> událost, která se obvykle vyvolá, když je potřeba vytvořit novou položku vázaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="647d4-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="647d4-105">Vaše obslužná rutina události můžete zadat jakýkoli vlastní chování, je třeba (např. volání metody na webovou službu nebo získání nového objektu z objektu pro vytváření tříd).</span><span class="sxs-lookup"><span data-stu-id="647d4-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="647d4-106">Při přidání položky pomocí manipulace <xref:System.Windows.Forms.BindingSource.AddingNew> události, přidání nelze zrušit.</span><span class="sxs-lookup"><span data-stu-id="647d4-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="647d4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="647d4-107">Example</span></span>  
 <span data-ttu-id="647d4-108">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládací prvek na objekt pro vytváření tříd pomocí <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="647d4-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="647d4-109">Pokud uživatel klikne <xref:System.Windows.Forms.DataGridView> ovládacího prvku nový řádek, <xref:System.Windows.Forms.BindingSource.AddingNew> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="647d4-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="647d4-110">Vytvoří novou obslužnou rutinu události `DemoCustomer` objektu, který je přiřazen <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="647d4-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="647d4-111">To způsobí, že nový `DemoCustomer` objektu, který chcete přidat do <xref:System.Windows.Forms.BindingSource> seznamu komponenty a který se má zobrazit na novém řádku z <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="647d4-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="647d4-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="647d4-112">Compiling the Code</span></span>  
 <span data-ttu-id="647d4-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="647d4-113">This example requires:</span></span>  
  
-   <span data-ttu-id="647d4-114">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="647d4-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="647d4-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="647d4-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="647d4-116">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="647d4-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647d4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="647d4-117">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="647d4-118">BindingSource – komponenta</span><span class="sxs-lookup"><span data-stu-id="647d4-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="647d4-119">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="647d4-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
