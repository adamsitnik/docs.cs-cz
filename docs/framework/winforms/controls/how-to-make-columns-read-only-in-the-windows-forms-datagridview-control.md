---
title: 'Postupy: Nastavení sloupců jen pro čtení v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: e57f926208e67ce894b58bdfaf5d0c3e3815b2ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514878"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Postupy: Nastavení sloupců jen pro čtení v ovládacím prvku Windows Forms DataGridView
Všechna data je určena pro úpravy. V <xref:System.Windows.Forms.DataGridView> ovládací prvek sloupec <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost hodnota určuje, zda uživatelé mohou upravovat buňky ve sloupci. Informace o tom, jak nastavit ovládací prvek zcela jen pro čtení najdete v tématu [jak: Zamezení přidávání řádků a odstranění v Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [jak: Přepnutí sloupců jen pro čtení v Windows Forms DataGridView pomocí návrháře](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Chcete-li sloupec jen pro čtení prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` sloupec s názvem `CompanyName`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
