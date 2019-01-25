---
title: 'Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 003ddd68de22d60b771ca525cfa5cc6b2e1e1e3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650769"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí návrháře
<xref:System.Windows.Forms.DataGridView> Řízení umožňuje určení výchozích stylů buňky a datových formátů pro celý ovládací prvek, pro konkrétní sloupce, pro záhlaví řádků a sloupců a pro střídavé řádky k vytvoření účetní knihy efektu buňky. Ve výchozím nastavení nastavený styly sloupců a střídavé řádky se přepíšou výchozí styly nastavit pro celý ovládací prvek. Kromě toho stylů, které jste nastavili v kódu pro jednotlivé řádky a buňky přepsat výchozí styly.  
  
 Další informace o styly buňky v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md). Nastavení stylů střídavých řádků, najdete v článku [jak: Nastavení stylů střídavých řádků pro Windows Forms DataGridView pomocí návrháře](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Můžete také nastavit pomocí stylů <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost ovlivnit všechny řádky, které se přidají do ovládacího prvku. Další informace o šabloně řádku, naleznete v tématu [jak: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Následující postup vyžaduje **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Nastavení výchozích stylů pro všechny buňky v ovládacím prvku  
  
1.  Vyberte <xref:System.Windows.Forms.DataGridView> ovládací prvek v návrháři.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, nebo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> vlastnost. **Sestavení objektu CellStyle** zobrazí se dialogové okno.  
  
3.  Definování styl nastavením vlastností, pomocí **ve verzi Preview** podokně zkontrolujte zvolené volby.  
  
> [!NOTE]
>  Pokud jsou povolené vizuální styly, záhlaví řádků a sloupců (s výjimkou <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky ve stylu podle aktuálního motivu přepsání <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> hodnot vlastností.  
>   
>  Můžete nastavit stylů buňky pro více vybraných <xref:System.Windows.Forms.DataGridView> ovládací prvky pomocí návrháře, ale jen pokud mají stejné hodnoty pro vlastnost stylu buňky, kterou chcete upravit. Pokud se všechny styly buňky liší pro tuto vlastnost **vlastnosti** okna **sestavení objektu CellStyle** dialogové okno bude prázdné.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Nastavení výchozích stylů buňky v jednotlivých sloupcích  
  
1.  Klikněte pravým tlačítkem myši <xref:System.Windows.Forms.DataGridView> ovládací prvek v návrháři a zvolte **upravit sloupce**.  
  
2.  Vyberte sloupec **vybrané sloupce** seznamu.  
  
3.  V **vlastnosti sloupce** mřížky, klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost. **Sestavení objektu CellStyle** zobrazí se dialogové okno.  
  
4.  Definování styl nastavením vlastností, pomocí **ve verzi Preview** podokně zkontrolujte zvolené volby.  
  
### <a name="to-format-data-in-cells"></a>K formátování dat v buňkách  
  
1.  Použijte jednu z předchozích postupů k zobrazení **sestavení objektu CellStyle** dialogovém související vlastnost Výchozí styl buňky.  
  
2.  V **Tvůrce CellStyle** dialogového okna klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> Vlastnost. **Formátovací řetězec** zobrazí se dialogové okno.  
  
3.  Vyberte typ formátu a úpravě podobností o typ (například počet zobrazovaných desetinných míst), pomocí **ukázka** políčka potvrďte zvolené volby.  
  
4.  Pokud vytváříte vazbu <xref:System.Windows.Forms.DataGridView> ovládacího prvku na zdroj dat, která by mohla obsahovat hodnoty null, vyplňte **hodnotu Null** textového pole. Tato hodnota se zobrazí, když hodnota buňky je roven nulovému odkazu (`Nothing` v jazyce Visual Basic) nebo <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí návrháře](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
