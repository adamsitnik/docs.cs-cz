---
title: 'Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 85c1d398c1aabbb73d5ae34186775e2c63666cfb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309443"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="828d2-102">Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu</span><span class="sxs-lookup"><span data-stu-id="828d2-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="828d2-103">Běžné úlohy při vývoji aplikace se přidání ovládacích prvků pro a odebírání ovládacích prvků z kontejneru ovládacích prvků ve formulářích (například <xref:System.Windows.Forms.Panel> nebo <xref:System.Windows.Forms.GroupBox> ovládací prvek nebo dokonce i samotný formulář).</span><span class="sxs-lookup"><span data-stu-id="828d2-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="828d2-104">V době návrhu můžete přetáhnout ovládací prvky přímo na panelu nebo skupiny.</span><span class="sxs-lookup"><span data-stu-id="828d2-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="828d2-105">V době běhu, udržovat tyto ovládací prvky `Controls` kolekce, která uchovává informace o jaké ovládací prvky jsou umístěny na ně.</span><span class="sxs-lookup"><span data-stu-id="828d2-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="828d2-106">Následující příklad kódu se vztahuje na libovolný ovládací prvek, který udržuje sadu ovládacích prvků na ní.</span><span class="sxs-lookup"><span data-stu-id="828d2-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="828d2-107">Přidání ovládacího prvku do kolekce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="828d2-107">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="828d2-108">Vytvořte instanci ovládacího prvku na Přidat.</span><span class="sxs-lookup"><span data-stu-id="828d2-108">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="828d2-109">Nastavení vlastností nového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="828d2-109">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="828d2-110">Přidejte ovládací prvek `Controls` kolekce nadřazeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="828d2-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="828d2-111">Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="828d2-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="828d2-112">Vyžaduje formulář s <xref:System.Windows.Forms.Panel> ovládací prvek a zda vytvořena metoda zpracování událostí na tlačítku pro `NewPanelButton_Click`, již existuje.</span><span class="sxs-lookup"><span data-stu-id="828d2-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="828d2-113">Odebrání ovládacích prvků z kolekce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="828d2-113">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="828d2-114">Odeberte obslužnou rutinu události z události.</span><span class="sxs-lookup"><span data-stu-id="828d2-114">Remove the event handler from the event.</span></span> <span data-ttu-id="828d2-115">V jazyce Visual Basic použijte [RemoveHandler – příkaz](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) – klíčové slovo; ve Vizuálu C#, použijte [-= – operátor (C# odkaz)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="828d2-115">In Visual Basic, use the [RemoveHandler Statement](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) keyword; in Visual C#, use the [-= Operator (C# Reference)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span></span>  
  
2. <span data-ttu-id="828d2-116">Použití `Remove` metoda odstranit požadovaný ovládací prvek z panelu `Controls` kolekce.</span><span class="sxs-lookup"><span data-stu-id="828d2-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="828d2-117">Volání <xref:System.Windows.Forms.Control.Dispose%2A> metoda a uvolnit tak prostředky používané ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="828d2-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="828d2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="828d2-118">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="828d2-119">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="828d2-119">Panel Control</span></span>](panel-control-windows-forms.md)
