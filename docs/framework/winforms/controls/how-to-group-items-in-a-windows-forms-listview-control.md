---
title: 'Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 52030b78b95d88432a5cac9b089ab87ca6d4f534
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500704"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView
S funkcí seskupování <xref:System.Windows.Forms.ListView> ovládacího prvku, lze zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce záhlaví vodorovné skupin, které obsahují názvů skupin. Můžete použít <xref:System.Windows.Forms.ListView> skupiny, aby měli procházení rozsáhlých seznamů jednodušší seskupováním položek podle abecedy, datum, nebo jiné logické seskupení. Následující obrázek ukazuje některé seskupených položek.  
  
 ![Skupiny ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
Položky jsou seskupeny ListView  
  
 Chcete-li povolit seskupování, musíte nejdřív vytvořit jeden nebo více skupin v Návrháři nebo prostřednictvím kódu programu. Po definování skupinu můžete přiřadit <xref:System.Windows.Forms.ListView> položky do skupin. Můžete také přesouvání položek z jedné skupiny do jiné prostřednictvím kódu programu.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> jsou k dispozici pouze na skupiny [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. Ve starších operačních systémech jakýkoli kód týkajících se skupin nemá žádný vliv a skupin nebude zobrazovat. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Přidání skupin  
  
1.  Použití <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Chcete-li odebrat skupiny  
  
1.  Použití <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Metoda odebere jednu skupinu; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda odebere všechny skupiny ze seznamu.  
  
    > [!NOTE]
    >  Odebrání skupinového neodebírá položky v rámci dané skupiny.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>K přiřazení položky do skupin nebo přesouvat položky mezi skupinami  
  
1.  Nastavte <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> vlastnost jednotlivých položek.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Funkce Windows XP a ovládací prvky Windows Forms](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
