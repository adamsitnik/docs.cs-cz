---
title: FlowLayoutPanel – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 2b08566f4b13ed54bfc0bb83c39777410251dafa
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441767"
---
# <a name="flowlayoutpanel-control-overview"></a>FlowLayoutPanel – přehled ovládacího prvku
<xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek uspořádá jeho obsah ve směru toku vodorovně nebo svisle. Můžete zabalit obsah ovládacího prvku z jednoho řádku na další nebo z jednoho sloupce na další. Namísto obtékání můžete alternativně oříznout jeho obsah.  
  
 Směr toku můžete zadat tak, že nastavíte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost. <xref:System.Windows.Forms.FlowLayoutPanel> Ovládacího prvku správně obrátí jeho směr toku v rozložení doleva (RTL). Můžete také určit, zda <xref:System.Windows.Forms.FlowLayoutPanel> obsah ovládacího prvku zalomen nebo oříznut tak, že nastavíte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Automaticky řídit velikosti jeho obsah, při nastavení <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`. Poskytuje také **FlowBreak** vlastnost jeho podřízeným ovládacím prvkům. Nastavení hodnoty vlastnosti FlowBreak k `true` způsobí, že <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek zastavit rozvrhování ovládacích prvků v aktuální směr toku a zalomení na další řádek nebo sloupec.  
  
 Libovolný ovládací prvek Windows Forms může být podřízený <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek, včetně dalších instancí <xref:System.Windows.Forms.FlowLayoutPanel>. Díky této možnosti lze vytvořit sofistikované rozložení, které se přizpůsobí vaše formuláře dimenzí v době běhu.  
  
 Viz také [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Ovládací prvek FlowLayoutPanel](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
