---
title: 'Postupy: Vykreslení obrázku v oblasti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 2b88982e7a8d196c31869dc74aac636d78f68386
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207809"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Postupy: Vykreslení obrázku v oblasti
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ImageBrush> třídu pro vykreslení oblasti obrázkem. <xref:System.Windows.Media.ImageBrush> Zobrazí jedné image, která je určená jeho <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad barvy <xref:System.Windows.Controls.Control.Background%2A> tlačítka pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Ve výchozím nastavení <xref:System.Windows.Media.ImageBrush> roztáhne, aby jeho image pro úplně naplnění oblasti, kterou vymalováváte. V předchozím příkladu je na obrázku roztažený tak, aby vyplnil tlačítko, případně narušují bitovou kopii. Toto chování můžete ovládat nastavením <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.TileBrush> k <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill>, což způsobí, že štětce, který se zachovat poměr stran obrázku.  
  
 Pokud jste nastavili <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti <xref:System.Windows.Media.ImageBrush>, můžete vytvořit s opakováním vzoru. V následujícím příkladu jsou vykreslovány tlačítko s použitím vzoru, který je vytvořený z image.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> najdete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
 Tento příklad kódu je součástí většího příkladu, která je k dispozici pro <xref:System.Windows.Media.ImageBrush> třídy. Úplnou ukázku najdete v tématu [ImageBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Viz také:

- [Kreslení pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
