---
title: 'Postupy: Animace trojrozměrné rotace pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 87176df26405a69cb2c3d63620def0575b750b52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010264"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Postupy: Animace trojrozměrné rotace pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)
V následujícím příkladu <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> se využívá k Prognózování 3D objekt otočit. Tato animace používá následující klíčové snímky:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> slouží k vytvoření hladkého, lineární interpolaci mezi hodnotami.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> slouží k vytvoření i s náhlými "přeskakování" mezi hodnotami (žádné interpolace).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> slouží k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> vlastnost. V následujícím příkladu této části se animace spustila vypnout pomalé, ale na konci časového úseku, zrychluje exponenciálně zvyšuje.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Animace trojrozměrného otočení pomocí scénářů](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animace trojrozměrného otočení pomocí Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animace 3D otočení pomocí kvaternionů](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animace trojrozměrné rotace pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
