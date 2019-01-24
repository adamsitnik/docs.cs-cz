---
title: 'Postupy: Implementace rozhraní PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: c239cb3005d2748f9cba55a5bb0b5d564828f51b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717889"
---
# <a name="how-to-implement-prioritybinding"></a>Postupy: Implementace rozhraní PriorityBinding
<xref:System.Windows.Data.PriorityBinding> v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funguje tak, že zadáte seznam vazby. Seznam vazby je nejnižší priorita seřazené od nejvyšší prioritou. Vrátí-li nejvyšší prioritou vazby hodnotu úspěšně při zpracování nejsou nikdy potřeba zpracovat v seznamu vazeb. Může to být případ, který nejvyšší prioritou vazby trvá dlouhou dobu k vyhodnocení, další nejvyšší prioritu, která vrací hodnotu úspěšně bude používat, dokud vazbu s vyšší prioritou vrací hodnotu úspěšně.  
  
## <a name="example"></a>Příklad  
 K předvedení jak <xref:System.Windows.Data.PriorityBinding> funguje, `AsyncDataSource` objekt byl vytvořen s následujícími třemi vlastnostmi: `FastDP`, `SlowerDP`, a `SlowestDP`.  
  
 Přístupová metoda get `FastDP` vrací hodnotu `_fastDP` datový člen.  
  
 Přístupová metoda get `SlowerDP` čeká 3 sekund před vrácením hodnoty `_slowerDP` datový člen.  
  
 Přístupová metoda get `SlowestDP` čeká na 5 sekund před vrácením hodnoty `_slowestDP` datový člen.  
  
> [!NOTE]
>  V tomto příkladu je pouze pro demonstrační účely. [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Nedoporučujeme pokyny k definování vlastností, které jsou řádů pomalejší, než bude sada polí. Další informace najdete v tématu [NIB: Volba mezi vlastností a metod](https://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> Vlastnost vytvoří vazbu na výše uvedené `AsyncDS` pomocí <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Když zpracovává modul vazby <xref:System.Windows.Data.Binding> objekty, začíná prvním <xref:System.Windows.Data.Binding>, který je vázán na `SlowestDP` vlastnost. Když to <xref:System.Windows.Data.Binding> je zpracování nevrací hodnotu úspěšně vzhledem k tomu, že se je v režimu spánku po dobu 5 sekund, takže další <xref:System.Windows.Data.Binding> zpracování elementu. Další <xref:System.Windows.Data.Binding> nevrací hodnotu úspěšně protože uspává se na 3 sekundy. Vazby pak přesune do další <xref:System.Windows.Data.Binding> element, který je vázán na `FastDP` vlastnost. To <xref:System.Windows.Data.Binding> vrací hodnotu "Rychlého Value". <xref:System.Windows.Controls.TextBlock> Nyní zobrazuje hodnotu "Rychlého Value".  
  
 Po uplynutí 3 sekundy `SlowerDP` vlastnost vrací hodnotu "Pomalejší hodnotu". <xref:System.Windows.Controls.TextBlock> Zobrazí hodnotu "Pomalejší hodnotu".  
  
 Po uplynutí 5 sekund `SlowestDP` vlastnost vrací hodnotu "Nejpomalejší hodnota". Že vazba má nejvyšší prioritu, protože je uvedená jako první. <xref:System.Windows.Controls.TextBlock> Nyní zobrazuje hodnotu "Nejpomalejší hodnota".  
  
 Zobrazit <xref:System.Windows.Data.PriorityBinding> informace o tom, co se považuje za úspěšná návratová hodnota z vazby.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
