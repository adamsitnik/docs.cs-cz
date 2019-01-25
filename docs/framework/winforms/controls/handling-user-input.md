---
title: Zpracování uživatelského vstupu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: a60ad943edae3775b00be99c08ad992af935ac13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636446"
---
# <a name="handling-user-input"></a><span data-ttu-id="5cf60-102">Zpracování uživatelského vstupu</span><span class="sxs-lookup"><span data-stu-id="5cf60-102">Handling User Input</span></span>
<span data-ttu-id="5cf60-103">Toto téma popisuje hlavní události klávesnice a myši poskytované <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5cf60-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5cf60-104">Při zpracování události, ovládací prvek autoři by měly přepsat chráněnou `On` *EventName* metody spíše než připojením delegáta k události.</span><span class="sxs-lookup"><span data-stu-id="5cf60-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="5cf60-105">Přehled událostí, naleznete v tématu [vyvolávání událostí z komponenty](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="5cf60-105">For a review of events, see [Raising Events from a Component](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cf60-106">Pokud neexistuje žádná data přidružená k události, instance základní třídy <xref:System.EventArgs> je předán jako argument `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="5cf60-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="5cf60-107">Události klávesnice</span><span class="sxs-lookup"><span data-stu-id="5cf60-107">Keyboard Events</span></span>  
 <span data-ttu-id="5cf60-108">Jsou běžné události klávesnice, které dokáže zpracovat váš ovládací prvek <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, a <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="5cf60-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="5cf60-109">Název události</span><span class="sxs-lookup"><span data-stu-id="5cf60-109">Event Name</span></span>|<span data-ttu-id="5cf60-110">Metoda přepsání.</span><span class="sxs-lookup"><span data-stu-id="5cf60-110">Method to Override</span></span>|<span data-ttu-id="5cf60-111">Popis události</span><span class="sxs-lookup"><span data-stu-id="5cf60-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="5cf60-112">Vyvolána, pouze když se stiskne klávesa, původně.</span><span class="sxs-lookup"><span data-stu-id="5cf60-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="5cf60-113">Vyvolá se pokaždé, když se stiskne klávesa.</span><span class="sxs-lookup"><span data-stu-id="5cf60-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="5cf60-114">Pokud je klávesa stisknuta, <xref:System.Windows.Forms.Control.KeyPress> událost se vyvolá při opakovaném rychlostí definované v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="5cf60-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="5cf60-115">Vyvoláno, když se uvolní klávesa.</span><span class="sxs-lookup"><span data-stu-id="5cf60-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5cf60-116">Zpracování vstupu klávesnice je podstatně složitější než přepsání události v předchozí tabulce a je nad rámec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5cf60-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="5cf60-117">Další informace najdete v tématu [uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5cf60-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="5cf60-118">Události myši</span><span class="sxs-lookup"><span data-stu-id="5cf60-118">Mouse Events</span></span>  
 <span data-ttu-id="5cf60-119">Události myši, které dokáže zpracovat váš ovládací prvek se <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, a <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="5cf60-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="5cf60-120">Název události</span><span class="sxs-lookup"><span data-stu-id="5cf60-120">Event Name</span></span>|<span data-ttu-id="5cf60-121">Metoda přepsání.</span><span class="sxs-lookup"><span data-stu-id="5cf60-121">Method to Override</span></span>|<span data-ttu-id="5cf60-122">Popis události</span><span class="sxs-lookup"><span data-stu-id="5cf60-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="5cf60-123">Vyvoláno, když se stiskne tlačítko myši, zatímco je ukazatel nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5cf60-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="5cf60-124">Vyvoláno, když ukazatel poprvé vstoupí oblasti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5cf60-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="5cf60-125">Vyvoláno, když ukazatel myši setrvá na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="5cf60-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="5cf60-126">Vyvoláno, když ukazatel opustí oblasti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5cf60-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="5cf60-127">Vyvolá se při přesunutí ukazatele myši do oblasti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5cf60-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="5cf60-128">Vyvoláno, když se uvolní tlačítko myši, zatímco je ukazatel myši nad ovládací prvek nebo ukazatel opustí oblasti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5cf60-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="5cf60-129">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseDown> událostí.</span><span class="sxs-lookup"><span data-stu-id="5cf60-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="5cf60-130">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseMove> událostí.</span><span class="sxs-lookup"><span data-stu-id="5cf60-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="5cf60-131">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseUp> událostí.</span><span class="sxs-lookup"><span data-stu-id="5cf60-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="5cf60-132">Pro úplný zdrojový kód `FlashTrackBar` ukázkový, přečtěte si téma [jak: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="5cf60-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf60-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cf60-133">See also</span></span>
- [<span data-ttu-id="5cf60-134">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cf60-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [<span data-ttu-id="5cf60-135">Definování události</span><span class="sxs-lookup"><span data-stu-id="5cf60-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="5cf60-136">Události</span><span class="sxs-lookup"><span data-stu-id="5cf60-136">Events</span></span>](../../../../docs/standard/events/index.md)
- [<span data-ttu-id="5cf60-137">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cf60-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
