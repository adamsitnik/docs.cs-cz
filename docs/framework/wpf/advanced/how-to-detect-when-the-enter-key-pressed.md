---
title: 'Postupy: Detekce stisknuté klávesy Enter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004821"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Postupy: Detekce stisknuté klávesy Enter
Tento příklad ukazuje, jak zjistit, kdy se na klávesnici stiskne klávesa <xref:System.Windows.Input.Key.Enter>.  
  
 Tento příklad se skládá ze souboru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a souboru kódu na pozadí.  
  
## <a name="example"></a>Příklad  
 Když uživatel stiskne v <xref:System.Windows.Controls.TextBox> klíč <xref:System.Windows.Input.Key.Enter>, vstup v textovém poli se zobrazí v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Následující kód XAML vytvoří uživatelské rozhraní, které se skládá z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Následující kód za vytvoří obslužnou rutinu události <xref:System.Windows.UIElement.KeyDown>.  Pokud je Stisknutá klávesa <xref:System.Windows.Input.Key.Enter>, zobrazí se v <xref:System.Windows.Controls.TextBlock> zpráva.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vstupu](input-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
