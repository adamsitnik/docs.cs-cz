---
title: 'Postupy: Použití několika transformací na objekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 26dcd4a64fc7aa2c3cb9cc599ceaef292efb1b6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192755"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>Postupy: Použití několika transformací na objekt
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TransformGroup> do skupiny dva nebo více <xref:System.Windows.Media.Transform> objekty do jednoho složeného <xref:System.Windows.Media.Transform>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.TransformGroup> použít <xref:System.Windows.Media.ScaleTransform> a <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [Přehled transformace](transforms-overview.md)
- [Ukázka 2D transformace](https://go.microsoft.com/fwlink/?LinkID=158252)
