---
title: 'Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 533c341e2fae528ec896bf38bafa13974af1d127
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360034"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku
Tento příklad ukazuje způsob vykreslení zavřeného tvaru použitím <xref:System.Windows.Shapes.Polygon> elementu. Vykreslení zavřeného tvaru, vytvořit <xref:System.Windows.Shapes.Polygon> elementu a použijte jeho <xref:System.Windows.Shapes.Polygon.Points%2A> vlastnosti a určit tak vrcholů obrazce. Řádek je automaticky vykreslit, která se připojuje první a poslední bod. Nakonec zadejte <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, nebo obojí.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], platnou syntaxi pro body je mezerami oddělený seznam párů oddělených čárkou x a y souřadnice.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Ačkoli v příkladu se používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala polygonů, můžete použít elementy mnohoúhelníku (a všechny ostatní prvky tvar) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje netextový obsah.  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).
