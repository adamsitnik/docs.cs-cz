---
title: 'Postupy: Vyberte položku v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: ed3e68fbe77f194ed04d15f99a48657a32a13b50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644713"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Postupy: Vyberte položku v ovládacím prvku Windows Forms ListView
Tento příklad ukazuje, jak prostřednictvím kódu programu vyberte položku ve Windows Forms <xref:System.Windows.Forms.ListView> ovládacího prvku. Výběr položky pomocí programu nezmění automaticky fokus <xref:System.Windows.Forms.ListView> ovládacího prvku. Z tohoto důvodu se obvykle také chcete nastavit položku jako fokus při výběru položky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` , který obsahuje alespoň jednu položku.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> obory názvů.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
