---
title: 'Postupy: Vytvoření oblouku elipsy'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: aae304b9963f3a8e5833b4d8ba0a54777a750225
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183648"
---
# <a name="how-to-create-an-elliptical-arc"></a>Postupy: Vytvoření oblouku elipsy
Tento příklad ukazuje, jak nakreslit oblouk elipsy. K vytvoření oblouku elipsy, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.ArcSegment> třídy.  
  
## <a name="example"></a>Příklad  
 V následujících příkladech oblouku elipsy linie z (10,100) (200,100). Oblouk <xref:System.Windows.Media.ArcSegment.Size%2A> 100 podle 50 v pixelech nezávislých na zařízení, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stupňů, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> nastavení `true`a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 [xaml]  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], syntaxe atributů lze použít k popisu cesty.  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](path-markup-syntax.md) stránky.)  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit oblouku elipsy explicitně pomocí značky object. Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 V tomto příkladu je součástí větší ukázky. Úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md)
- [Vytvoření kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md)
