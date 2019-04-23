---
title: 'Postupy: Změna velikosti elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 607b3a11085f746503c1b82552f1740b49d9ef5d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131700"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="ad9b4-102">Postupy: Změna velikosti elementu</span><span class="sxs-lookup"><span data-stu-id="ad9b4-102">How to: Scale an Element</span></span>
<span data-ttu-id="ad9b4-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ScaleTransform> škálování elementu.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="ad9b4-104">Použití <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti, které chcete změnit velikost elementu faktorem, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="ad9b4-105">Například <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnotu 1.5 roztáhne na 150 procento původní šířku elementu.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="ad9b4-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> hodnota 0,5 zmenšuje výšku prvku o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="ad9b4-107">Použití <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> vlastnosti k určení bodu, který je Centrum operace škálování.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="ad9b4-108">Ve výchozím nastavení <xref:System.Windows.Media.ScaleTransform> je zarovnaný na střed v okamžiku (0; 0), která odpovídá levého horního rohu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="ad9b4-109">Tato akce nemá vliv přesunutí elementu a také díky tomu se zobrazí větší, protože při použití <xref:System.Windows.Media.Transform>, změníte souřadnicového prostoru, ve kterém se objekt nachází.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="ad9b4-110">Následující příklad používá <xref:System.Windows.Media.ScaleTransform> na dvojnásobek velikosti 50podle-50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="ad9b4-111"><xref:System.Windows.Media.ScaleTransform> Má hodnotu 0 (výchozí) pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad9b4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad9b4-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="ad9b4-113">Obvykle nastavena <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> do středu objektu, který je škálovat: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).</span><span class="sxs-lookup"><span data-stu-id="ad9b4-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="ad9b4-114">Následující příklad ukazuje jiné <xref:System.Windows.Shapes.Rectangle> , který se zdvojnásobí velikost; však to <xref:System.Windows.Media.ScaleTransform> má hodnotu 25 pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, která odpovídá na střed obdélníku.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="ad9b4-115">Následující ilustrace ukazuje rozdíl mezi těmito dvěma <xref:System.Windows.Media.ScaleTransform> operace.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="ad9b4-116">Tečkovaná čára ukazuje velikost a umístění obdélníku, před Škálováním.</span><span class="sxs-lookup"><span data-stu-id="ad9b4-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="ad9b4-117">![2 x škáluje s různými středy](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="ad9b4-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="ad9b4-118">Dvě operace ScaleTransform – identické ScaleX a ScaleY hodnoty, ale jiné centra</span><span class="sxs-lookup"><span data-stu-id="ad9b4-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="ad9b4-119">Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="ad9b4-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9b4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad9b4-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="ad9b4-121">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="ad9b4-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="ad9b4-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ad9b4-122">How-to Topics</span></span>](transformations-how-to-topics.md)
