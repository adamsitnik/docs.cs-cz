---
title: 'Postupy: Tisk klientské oblasti formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: 2c808b480c38fc34006dcdf5832a814dfef1c62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505624"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="caa2b-102">Postupy: Tisk klientské oblasti formuláře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caa2b-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="caa2b-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje rychlý tisk obrázek formuláře bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty.</span><span class="sxs-lookup"><span data-stu-id="caa2b-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="caa2b-104">Následující postup ukazuje, jak vytisknout jenom klientské oblasti formuláře, bez záhlaví, ohraničení a posuvníky.</span><span class="sxs-lookup"><span data-stu-id="caa2b-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="caa2b-105">Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="caa2b-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="caa2b-106">Tisk klientské oblasti formuláře</span><span class="sxs-lookup"><span data-stu-id="caa2b-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="caa2b-107">V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="caa2b-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="caa2b-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="caa2b-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="caa2b-109">V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="caa2b-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="caa2b-110">Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).</span><span class="sxs-lookup"><span data-stu-id="caa2b-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="caa2b-111">V některých operačních systémů, textové nebo grafické vykreslené <xref:System.Drawing.Graphics> metody nestiskne správně.</span><span class="sxs-lookup"><span data-stu-id="caa2b-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="caa2b-112">V takovém případě použijte metodu kompatibilní tisku: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="caa2b-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa2b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caa2b-113">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>
- [<span data-ttu-id="caa2b-114">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="caa2b-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
- [<span data-ttu-id="caa2b-115">Postupy: Tisk klientských a neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="caa2b-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [<span data-ttu-id="caa2b-116">Postupy: Tisk posuvného formuláře</span><span class="sxs-lookup"><span data-stu-id="caa2b-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
