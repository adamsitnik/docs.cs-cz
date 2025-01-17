---
title: 'Postupy: Určení vlastního umístění prvku Popup'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: dc516f0eb1cfcbac6662497eb4019041eefec2a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911206"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Postupy: Určení vlastního umístění prvku Popup
Tento příklad ukazuje, jak určit vlastní umístění pro <xref:System.Windows.Controls.Primitives.Popup> řídí, kdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Příklad  
 Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> volá definované instance <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegovat. Tento delegát vrátí sadu možných bodů, které jsou relativní vzhledem k levého horního rohu cílovou oblast a levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup> Umístění dochází v okamžiku, která poskytuje nejlepší viditelnost.  
  
 Následující příklad ukazuje, jak definovat umístění <xref:System.Windows.Controls.Primitives.Popup> nastavením <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Také ukazuje, jak vytvořit a přiřadit <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, aby bylo možné umístit <xref:System.Windows.Controls.Primitives.Popup>.  Delegáta zpětného volání vrátí dva <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objekty.  Pokud <xref:System.Windows.Controls.Primitives.Popup> je skryt okraji obrazovky na první pozici <xref:System.Windows.Controls.Primitives.Popup> je umístěn na druhý pozici.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Úplnou ukázku najdete v tématu [Ukázka umístění automaticky otevíraného okna](https://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Primitives.Popup>
- [Přehled prvku Popup](popup-overview.md)
- [Témata s postupy](popup-how-to-topics.md)
