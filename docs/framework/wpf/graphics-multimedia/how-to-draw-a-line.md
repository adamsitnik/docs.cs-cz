---
title: 'Postupy: Vykreslení čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: c11dfb9523834ec2e622cb2e62bd6982a1a78fd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947651"
---
# <a name="how-to-draw-a-line"></a>Postupy: Vykreslení čáry
Tento příklad ukazuje, jak s použitím kreslení čar <xref:System.Windows.Shapes.Line> elementu.  
  
 Chcete-li nakreslit čáru, vytvořte <xref:System.Windows.Shapes.Line> elementu. Použijte jeho <xref:System.Windows.Shapes.Line.X1%2A> a <xref:System.Windows.Shapes.Line.Y1%2A> vlastnosti, které chcete nastavit jeho počáteční bod; a použít jeho <xref:System.Windows.Shapes.Line.X2%2A> a <xref:System.Windows.Shapes.Line.Y2%2A> vlastnosti a nastavte její koncový bod. Nakonec nastavte svůj <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vzhledem k tomu, že je neviditelný řádek bez tah.  
  
 Nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> – element pro řádek nemá žádný účinek, protože nemá žádné vnitřní řádku.  
  
 Následující příklad nakreslí tři řádky uvnitř <xref:System.Windows.Controls.Canvas> elementu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Shapes.Line>
- [Ukázka elementy obrazce](https://go.microsoft.com/fwlink/?LinkID=160037)
