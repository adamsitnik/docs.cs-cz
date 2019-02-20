---
title: Operace přetažení a podpora schránky
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 281d102ecd02623e7e18ebf4fc569538ebbdaf7f
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442006"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="30f87-102">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="30f87-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="30f87-103">Operace přetažení myší uživatelů v rámci aplikace založené na Windows můžete povolit řeší řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, a <xref:System.Windows.Forms.Control.DragDrop> události.</span><span class="sxs-lookup"><span data-stu-id="30f87-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="30f87-104">Můžete také implementovat podporu vyjmutí/zkopírování/vložení uživatele a uživatelská data přenášet do schránky. v rámci vaší aplikace pro systém Windows pomocí jednoduchý způsob volání.</span><span class="sxs-lookup"><span data-stu-id="30f87-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30f87-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="30f87-105">In This Section</span></span>  
 [<span data-ttu-id="30f87-106">Návod: Operace a přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30f87-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="30f87-107">Vysvětluje, jak spustit operaci přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="30f87-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="30f87-108">Postupy: Provádění operací přetažení myší mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="30f87-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="30f87-109">Ukazuje, jak k provádění operací přetažení myší napříč aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="30f87-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="30f87-110">Postupy: Přidání dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="30f87-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="30f87-111">Popisuje způsob, jak prostřednictvím kódu programu vložení informací do schránky.</span><span class="sxs-lookup"><span data-stu-id="30f87-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="30f87-112">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="30f87-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="30f87-113">Popisuje, jak přístup k datům uloženým ve schránce.</span><span class="sxs-lookup"><span data-stu-id="30f87-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="30f87-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="30f87-114">Related Sections</span></span>  
 [<span data-ttu-id="30f87-115">Funkce přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30f87-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="30f87-116">Popisuje metody, události a třídy používané k implementaci chování a přetažení.</span><span class="sxs-lookup"><span data-stu-id="30f87-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="30f87-117">Popisuje složitými rozhraními události, která žádá oprávnění pokračovat v provádění operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="30f87-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="30f87-118">Popisuje složitými rozhraními metody, která je zásadním zahájení operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="30f87-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="30f87-119">Viz také [jak: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="30f87-119">Also see [How to: Send Data to the Active MDI Child](how-to-send-data-to-the-active-mdi-child.md).</span></span>
