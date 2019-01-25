---
title: 'Postupy: Vytvoření LineSegment v PathGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: 9aa17a361e8e0ca5b43b2646c38926e0123818c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712126"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a><span data-ttu-id="638d4-102">Postupy: Vytvoření LineSegment v PathGeometry</span><span class="sxs-lookup"><span data-stu-id="638d4-102">How to: Create a LineSegment in a PathGeometry</span></span>
<span data-ttu-id="638d4-103">Tento příklad ukazuje, jak vytvořit úsek čáry.</span><span class="sxs-lookup"><span data-stu-id="638d4-103">This example shows how to create a line segment.</span></span> <span data-ttu-id="638d4-104">Chcete-li vytvořit úsek čáry, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.LineSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="638d4-104">To create a line segment, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.LineSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="638d4-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="638d4-105">Example</span></span>  
 <span data-ttu-id="638d4-106">Následující příklady nakreslit <xref:System.Windows.Media.LineSegment> z (10, 50) na (200, 70).</span><span class="sxs-lookup"><span data-stu-id="638d4-106">The following examples draw a <xref:System.Windows.Media.LineSegment> from (10, 50) to (200, 70).</span></span> <span data-ttu-id="638d4-107">Následující obrázek znázorňuje výsledný <xref:System.Windows.Media.LineSegment>; mřížky na pozadí byla přidána do souřadnicový systém zobrazení.</span><span class="sxs-lookup"><span data-stu-id="638d4-107">The following illustration shows the resulting <xref:System.Windows.Media.LineSegment>; a grid background was added to show the coordinate system.</span></span>  
  
 <span data-ttu-id="638d4-108">![LineSegment v PathFigure](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment")</span><span class="sxs-lookup"><span data-stu-id="638d4-108">![A LineSegment in a PathFigure](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment")</span></span>  
<span data-ttu-id="638d4-109">LineSegment vykreslovány z (10,50) (200,70)</span><span class="sxs-lookup"><span data-stu-id="638d4-109">A LineSegment drawn from (10,50) to (200,70)</span></span>  
  
 <span data-ttu-id="638d4-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="638d4-110">[xaml]</span></span>  
  
 <span data-ttu-id="638d4-111">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít syntaxi atributů k popisu cesty.</span><span class="sxs-lookup"><span data-stu-id="638d4-111">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use attribute syntax to describe a path.</span></span>  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1"    
  Data="M 10,50 L 200,70" />  
```  
  
 <span data-ttu-id="638d4-112">[xaml]</span><span class="sxs-lookup"><span data-stu-id="638d4-112">[xaml]</span></span>  
  
 <span data-ttu-id="638d4-113">(Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="638d4-113">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="638d4-114">Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="638d4-114">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="638d4-115">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], mohou také nakreslit úsek čáry pomocí syntaxe elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="638d4-115">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a line segment by using object element syntax.</span></span> <span data-ttu-id="638d4-116">Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.</span><span class="sxs-lookup"><span data-stu-id="638d4-116">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1">  
  <Path.Data>  
    <PathGeometry>  
      <PathFigure StartPoint="10,50">  
        <LineSegment Point="200,70" />  
      </PathFigure>  
    </PathGeometry>  
  </Path.Data>  
</Path>  
```  
  
```csharp  
PathFigure myPathFigure = new PathFigure();  
myPathFigure.StartPoint = new Point(10, 50);  
  
LineSegment myLineSegment = new LineSegment();  
myLineSegment.Point = new Point(200, 70);  
  
PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();  
myPathSegmentCollection.Add(myLineSegment);  
  
myPathFigure.Segments = myPathSegmentCollection;  
  
PathFigureCollection myPathFigureCollection = new PathFigureCollection();  
myPathFigureCollection.Add(myPathFigure);  
  
PathGeometry myPathGeometry = new PathGeometry();  
myPathGeometry.Figures = myPathFigureCollection;  
  
Path myPath = new Path();  
myPath.Stroke = Brushes.Black;  
myPath.StrokeThickness = 1;  
myPath.Data = myPathGeometry;  
```  
  
```vb  
Dim myPathFigure As New PathFigure()  
            myPathFigure.StartPoint = New Point(10, 50)  
  
            Dim myLineSegment As New LineSegment()  
            myLineSegment.Point = New Point(200, 70)  
  
            Dim myPathSegmentCollection As New PathSegmentCollection()  
            myPathSegmentCollection.Add(myLineSegment)  
  
            myPathFigure.Segments = myPathSegmentCollection  
  
            Dim myPathFigureCollection As New PathFigureCollection()  
            myPathFigureCollection.Add(myPathFigure)  
  
            Dim myPathGeometry As New PathGeometry()  
            myPathGeometry.Figures = myPathFigureCollection  
  
            Dim myPath As New Path()  
            myPath.Stroke = Brushes.Black  
            myPath.StrokeThickness = 1  
            myPath.Data = myPathGeometry  
```  
  
 <span data-ttu-id="638d4-117">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="638d4-117">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638d4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="638d4-118">See also</span></span>
- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [<span data-ttu-id="638d4-119">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="638d4-119">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
