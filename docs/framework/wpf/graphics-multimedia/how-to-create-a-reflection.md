---
title: 'Postupy: Vytvoření reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 0fae98966481003c7906f5cbb34afaea666d583d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559031"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="bd37d-102">Postupy: Vytvoření reflexe</span><span class="sxs-lookup"><span data-stu-id="bd37d-102">How to: Create a Reflection</span></span>
<span data-ttu-id="bd37d-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.VisualBrush> k vytvoření reflexe.</span><span class="sxs-lookup"><span data-stu-id="bd37d-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="bd37d-104">Protože <xref:System.Windows.Media.VisualBrush> tuto funkci můžete použít k vytváření zajímavé vizuálních efektů, jako je například odrazů a zvětšení, můžete zobrazit existujícího vizuálu.</span><span class="sxs-lookup"><span data-stu-id="bd37d-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd37d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd37d-105">Example</span></span>  
 <span data-ttu-id="bd37d-106">Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vytvoření obrazu <xref:System.Windows.Controls.Border> , která obsahuje několik elementů.</span><span class="sxs-lookup"><span data-stu-id="bd37d-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="bd37d-107">Následující obrázek ukazuje výstup, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="bd37d-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="bd37d-108">![A odráží vizuální objekty](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="bd37d-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="bd37d-109">Reflektovaný vizuální objekty</span><span class="sxs-lookup"><span data-stu-id="bd37d-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="bd37d-110">Úplnou ukázku, která obsahuje příklady, které ukazují, jak zvětšit části obrazovky a jak vytvořit odrazů, naleznete v tématu [VisualBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160049).</span><span class="sxs-lookup"><span data-stu-id="bd37d-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd37d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd37d-111">See also</span></span>
- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="bd37d-112">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="bd37d-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
