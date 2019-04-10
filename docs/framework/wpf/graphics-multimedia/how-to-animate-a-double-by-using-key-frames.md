---
title: 'Postupy: Animace dvojice pomocí klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 33d567b1bb91060a5b0e1da67236a27815262474
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208774"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="a6e7b-102">Postupy: Animace dvojice pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="a6e7b-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="a6e7b-103">Tento příklad ukazuje, jak animovat hodnotu vlastnosti, která přijímá <xref:System.Double> použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6e7b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6e7b-104">Example</span></span>  
 <span data-ttu-id="a6e7b-105">Následující příklad přesune obdélník obrazovce.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="a6e7b-106">V příkladu se používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> u <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a6e7b-107">Tuto animaci, která se stále opakuje, používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a6e7b-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="a6e7b-108">Během první tři sekundy, používá instanci <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> třídy přesunout obdélník podél cesty stabilní rychlostí z jeho výchozí pozice na 500 pozici.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="a6e7b-109">Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="a6e7b-110">Na konci čtvrtý druhý používá instanci <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> třídy náhle obdélník přesunout na další pozici.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="a6e7b-111">Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> vytvořit i s náhlými rozdíly mezi jednotlivými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="a6e7b-112">V tomto příkladu obdélníku je počáteční pozice a se pak náhle objeví na 500 pozici.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3.  <span data-ttu-id="a6e7b-113">Do dvou sekund konečná používá instanci <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> třídy přesunout obdélník zpět na počáteční pozici.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="a6e7b-114">Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="a6e7b-115">V tomto příkladu obdélník začíná přesunutím pomalu a pak zrychluje exponenciálně na konci časového úseku.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a6e7b-116">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="a6e7b-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="a6e7b-117">Pro zajištění konzistence s další příklady animace, kód verze tohoto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objektu, který chcete použít <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="a6e7b-118">Můžete také při použití jedné animace v kódu, je jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda namísto použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="a6e7b-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="a6e7b-119">Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="a6e7b-119">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e7b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6e7b-120">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [<span data-ttu-id="a6e7b-121">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="a6e7b-121">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="a6e7b-122">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="a6e7b-122">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
