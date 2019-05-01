---
title: 'Postupy: Implementace rozhraní PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: aaf2caff1e2684e08c7eb65125536f1070203d70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020852"
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="2b8ae-102">Postupy: Implementace rozhraní PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="2b8ae-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="2b8ae-103"><xref:System.Windows.Data.PriorityBinding> v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funguje tak, že zadáte seznam vazby.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="2b8ae-104">Seznam vazby je nejnižší priorita seřazené od nejvyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="2b8ae-105">Vrátí-li nejvyšší prioritou vazby hodnotu úspěšně při zpracování nejsou nikdy potřeba zpracovat v seznamu vazeb.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="2b8ae-106">Může to být případ, který nejvyšší prioritou vazby trvá dlouhou dobu k vyhodnocení, další nejvyšší prioritu, která vrací hodnotu úspěšně bude používat, dokud vazbu s vyšší prioritou vrací hodnotu úspěšně.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b8ae-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b8ae-107">Example</span></span>  
 <span data-ttu-id="2b8ae-108">K předvedení jak <xref:System.Windows.Data.PriorityBinding> funguje, `AsyncDataSource` objekt byl vytvořen s následujícími třemi vlastnostmi: `FastDP`, `SlowerDP`, a `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="2b8ae-109">Přístupová metoda get `FastDP` vrací hodnotu `_fastDP` datový člen.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="2b8ae-110">Přístupová metoda get `SlowerDP` čeká 3 sekund před vrácením hodnoty `_slowerDP` datový člen.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="2b8ae-111">Přístupová metoda get `SlowestDP` čeká na 5 sekund před vrácením hodnoty `_slowestDP` datový člen.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b8ae-112">V tomto příkladu je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="2b8ae-113">[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Nedoporučujeme pokyny k definování vlastností, které jsou řádů pomalejší, než bude sada polí.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="2b8ae-114">Další informace najdete v tématu [výběr mezi vlastností a metod](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2b8ae-114">For more information, see [Choosing Between Properties and Methods](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span></span>  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="2b8ae-115"><xref:System.Windows.Controls.TextBlock.Text%2A> Vlastnost vytvoří vazbu na výše uvedené `AsyncDS` pomocí <xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="2b8ae-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="2b8ae-116">Když zpracovává modul vazby <xref:System.Windows.Data.Binding> objekty, začíná prvním <xref:System.Windows.Data.Binding>, který je vázán na `SlowestDP` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="2b8ae-117">Když to <xref:System.Windows.Data.Binding> je zpracování nevrací hodnotu úspěšně vzhledem k tomu, že se je v režimu spánku po dobu 5 sekund, takže další <xref:System.Windows.Data.Binding> zpracování elementu.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="2b8ae-118">Další <xref:System.Windows.Data.Binding> nevrací hodnotu úspěšně protože uspává se na 3 sekundy.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="2b8ae-119">Vazby pak přesune do další <xref:System.Windows.Data.Binding> element, který je vázán na `FastDP` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="2b8ae-120">To <xref:System.Windows.Data.Binding> vrací hodnotu "Rychlého Value".</span><span class="sxs-lookup"><span data-stu-id="2b8ae-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="2b8ae-121"><xref:System.Windows.Controls.TextBlock> Nyní zobrazuje hodnotu "Rychlého Value".</span><span class="sxs-lookup"><span data-stu-id="2b8ae-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="2b8ae-122">Po uplynutí 3 sekundy `SlowerDP` vlastnost vrací hodnotu "Pomalejší hodnotu".</span><span class="sxs-lookup"><span data-stu-id="2b8ae-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="2b8ae-123"><xref:System.Windows.Controls.TextBlock> Zobrazí hodnotu "Pomalejší hodnotu".</span><span class="sxs-lookup"><span data-stu-id="2b8ae-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="2b8ae-124">Po uplynutí 5 sekund `SlowestDP` vlastnost vrací hodnotu "Nejpomalejší hodnota".</span><span class="sxs-lookup"><span data-stu-id="2b8ae-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="2b8ae-125">Že vazba má nejvyšší prioritu, protože je uvedená jako první.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="2b8ae-126"><xref:System.Windows.Controls.TextBlock> Nyní zobrazuje hodnotu "Nejpomalejší hodnota".</span><span class="sxs-lookup"><span data-stu-id="2b8ae-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="2b8ae-127">Zobrazit <xref:System.Windows.Data.PriorityBinding> informace o tom, co se považuje za úspěšná návratová hodnota z vazby.</span><span class="sxs-lookup"><span data-stu-id="2b8ae-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8ae-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b8ae-128">See also</span></span>

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2b8ae-129">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="2b8ae-129">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="2b8ae-130">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="2b8ae-130">How-to Topics</span></span>](data-binding-how-to-topics.md)
