---
title: 'Postupy: Otočení objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: d1c4700a5dc8f6ed99043552999d8f014116da8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189639"
---
# <a name="how-to-rotate-an-object"></a>Postupy: Otočení objektu
Tento příklad ukazuje, jak otočení objektu. V příkladu se nejdřív vytvoří <xref:System.Windows.Media.RotateTransform> a určuje jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> ve stupních.  
  
 V následujícím příkladu se otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů o jeho levého horního rohu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> určete bod, o tom, které je objekt otočen. Tato středový bod je vyjádřen v souřadnicového prostoru elementu, který je transformovat. Ve výchozím nastavení otočení platí pro (0; 0), což je levého horního rohu objekt, který má transformovat.  
  
 Následující příklad otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů po směru hodinových ručiček kolem bodu (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Následující obrázek znázorňuje výsledkem použití <xref:System.Windows.Media.Transform> dvěma objekty.  
  
 ![45 stupňů rotace s různými středy](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dva objekty, které otáčet 45 stupňů z různých rotačních centra  
  
 <xref:System.Windows.Shapes.Polyline> v předchozích příkladech je <xref:System.Windows.UIElement>. Při použití <xref:System.Windows.Media.Transform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.UIElement>, můžete použít <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti a určit původ pro každý <xref:System.Windows.Media.Transform> , která se vztahují na prvek. Vzhledem k tomu, <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost relativních souřadnic, center elementu, který můžete využít transformace, i, pokud neznáte jeho velikost. Další informace a příklad najdete v tématu [určení počátku transformace použitím relativní hodnoty](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Transform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
