---
title: 'Postupy: Animace objektu podél cesty (animace matice)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 3c90d20cac60004aa9876d9fe8d213d33c5a6883
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651439"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Postupy: Animace objektu podél cesty (animace matice)
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> třídy animace objektu podél cesty, který je definován <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje objektu podél cesty následujícím způsobem:  
  
- Se vztahuje <xref:System.Windows.Media.MatrixTransform> na objekt, aby bylo možné přesunout.  
  
- Definuje cestu s využitím <xref:System.Windows.Media.PathGeometry>.  
  
- Vytvoří <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a použije ho k animace <xref:System.Windows.Media.Matrix> vlastnost <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Přijímá <xref:System.Windows.Media.PathGeometry> a použije ho k vygenerování <xref:System.Windows.Media.Matrix> hodnoty.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028). Další informace o geometrické cesty, najdete v článku [přehled geometrie](geometry-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Ukázka animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
