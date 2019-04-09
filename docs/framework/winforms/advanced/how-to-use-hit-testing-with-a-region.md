---
title: 'Postupy: Použití nárazového testování s oblastí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 136f15f1364fb2aed791b4a61d0f11411b055967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150498"
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="42c5d-102">Postupy: Použití nárazového testování s oblastí</span><span class="sxs-lookup"><span data-stu-id="42c5d-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="42c5d-103">Účelem testování přístupů je určit, zda je kurzor nad daný objekt, jako je například ikony nebo tlačítko.</span><span class="sxs-lookup"><span data-stu-id="42c5d-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42c5d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="42c5d-104">Example</span></span>  
 <span data-ttu-id="42c5d-105">Následující příklad vytvoří ve tvaru plus oblast tvořící sjednocení dvě oblasti obdélníkový.</span><span class="sxs-lookup"><span data-stu-id="42c5d-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="42c5d-106">Předpokládejme, že proměnná `point` obsahuje nejnovější kliknutím na umístění.</span><span class="sxs-lookup"><span data-stu-id="42c5d-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="42c5d-107">Kód zkontroluje, zda `point` je v oblasti ve tvaru plus.</span><span class="sxs-lookup"><span data-stu-id="42c5d-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="42c5d-108">Pokud bod nachází v oblasti (položek), je oblast vyplněna neprůhledné red štětce.</span><span class="sxs-lookup"><span data-stu-id="42c5d-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="42c5d-109">V opačném případě je oblast vyplněna poloprůhledných red štětce.</span><span class="sxs-lookup"><span data-stu-id="42c5d-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="42c5d-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="42c5d-110">Compiling the Code</span></span>  
 <span data-ttu-id="42c5d-111">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="42c5d-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c5d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42c5d-112">See also</span></span>

- <xref:System.Drawing.Region>
- [<span data-ttu-id="42c5d-113">Oblasti v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="42c5d-113">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="42c5d-114">Postupy: Použití oříznutí s oblastí</span><span class="sxs-lookup"><span data-stu-id="42c5d-114">How to: Use Clipping with a Region</span></span>](how-to-use-clipping-with-a-region.md)
