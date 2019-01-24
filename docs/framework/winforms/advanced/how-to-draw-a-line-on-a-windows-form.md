---
title: 'Postupy: Nakreslit čáru na formuláři Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: 4274072b55c79cfe88e906d1401d275b414ebe97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586745"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="264ac-102">Postupy: Nakreslit čáru na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="264ac-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="264ac-103">V tomto příkladu nakreslí čáru na formuláři.</span><span class="sxs-lookup"><span data-stu-id="264ac-103">This example draws a line on a form.</span></span> <span data-ttu-id="264ac-104">Obvykle při kreslení ve formuláři je zpracovat formuláře <xref:System.Windows.Forms.Control.Paint> události a provádět kreslení pomocí <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnost <xref:System.Windows.Forms.PaintEventArgs>, jak je znázorněno v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="264ac-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="264ac-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="264ac-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="264ac-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="264ac-106">Compiling the Code</span></span>  
 <span data-ttu-id="264ac-107">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="264ac-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="264ac-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="264ac-108">Robust Programming</span></span>  
 <span data-ttu-id="264ac-109">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objekty.</span><span class="sxs-lookup"><span data-stu-id="264ac-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264ac-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="264ac-110">See also</span></span>
- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="264ac-111">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="264ac-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="264ac-112">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="264ac-112">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="264ac-113">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="264ac-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
