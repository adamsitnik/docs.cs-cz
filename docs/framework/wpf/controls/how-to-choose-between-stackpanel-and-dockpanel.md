---
title: 'Postupy: Výběr mezi elementy StackPanel a DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: 8338421dfb1bea856c15edf9d324cec955584f9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911235"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Postupy: Výběr mezi elementy StackPanel a DockPanel
Tento příklad ukazuje, jak si vybrat mezi pomocí <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel> při zásobníku obsah <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Příklad  
 I když můžete použít buď <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.StackPanel> do zásobníku podřízené prvky dvou ovládacích prvků vždy nevytváří stejné výsledky. Například pořadí umístit podřízené prvky mohou ovlivnit velikost podřízených elementů v <xref:System.Windows.Controls.DockPanel> , ale ne v <xref:System.Windows.Controls.StackPanel>. Důvodem tohoto chování různých <xref:System.Windows.Controls.StackPanel> míry ve směru překrývání na <xref:System.Double>.<xref:System.Double.PositiveInfinity>, nicméně <xref:System.Windows.Controls.DockPanel> měří pouze dostupné velikosti.  
  
 Následující příklad ukazuje tento klíčovým rozdílem mezi <xref:System.Windows.Controls.DockPanel> a <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [Přehled panelu](panels-overview.md)
