---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: ab088e3f34f3f03be2073864a440006259fe5679
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591339"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu
Při vytváření ovládacích prvků, které pracují s daty, někdy najdete je nezbytné pro vytvoření vazby ovládacího prvku do typu, nikoli objekt. K této situaci dochází především v době návrhu, když dat nemusí být k dispozici, ale své ovládací prvky vázané na data potřebují k zobrazení informací z veřejného rozhraní typu. Například může vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládací prvek na objekt zveřejněné jako webová služba a chcete <xref:System.Windows.Forms.DataGridView> ovládací prvek popisek její sloupce v době návrhu s členem názvů vlastního typu.  
  
 Můžete snadno vytvoření vazby ovládacího prvku na typ s <xref:System.Windows.Forms.BindingSource> komponenty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládacího prvku pomocí vlastního typu <xref:System.Windows.Forms.BindingSource> komponenty. Při spuštění v příkladu, můžete si všimnout <xref:System.Windows.Forms.DataGridView> je označené jako sloupce, které odpovídají vlastnosti `Customer` objektu před ovládací prvek naplněný daty. V příkladu má tlačítko Přidat zákazníka k přidání dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Když kliknete na tlačítko Nový `Customer` přidán <xref:System.Windows.Forms.BindingSource>. Ve skutečném scénáři může být volání webové služby nebo jiného zdroje dat získat data.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
