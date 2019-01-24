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
# <a name="how-to-create-a-reflection"></a>Postupy: Vytvoření reflexe
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.VisualBrush> k vytvoření reflexe. Protože <xref:System.Windows.Media.VisualBrush> tuto funkci můžete použít k vytváření zajímavé vizuálních efektů, jako je například odrazů a zvětšení, můžete zobrazit existujícího vizuálu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vytvoření obrazu <xref:System.Windows.Controls.Border> , která obsahuje několik elementů. Následující obrázek ukazuje výstup, který tento příklad vytvoří.  
  
 ![A odráží vizuální objekty](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Reflektovaný vizuální objekty  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Úplnou ukázku, která obsahuje příklady, které ukazují, jak zvětšit části obrazovky a jak vytvořit odrazů, naleznete v tématu [VisualBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.VisualBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
