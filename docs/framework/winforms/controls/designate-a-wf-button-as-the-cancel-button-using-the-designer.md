---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 9d11528d7d7fed13f531faeb09f38c4564f970be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520474"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno pomocí návrháře
Na formuláři Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Storno. Pokaždé, když uživatel stiskne klávesu ESC, bez ohledu na to, který má jiný ovládací prvek ve formuláři fokus, je kliknutí na tlačítko Storno. Toto tlačítko je obvykle naprogramovaný tak, aby uživateli umožňuje rychle operaci ukončit bez potvrzení na každou akci.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-cancel-button"></a>Chcete-li určit tlačítka Storno  
  
1.  Vyberte formulář, na kterém je umístěn tlačítku.  
  
2.  V **vlastnosti** okno, nastavte formuláře <xref:System.Windows.Forms.Form.CancelButton%2A> vlastnost <xref:System.Windows.Forms.Button> název ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Přehled ovládacího prvku Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka přijmout pomocí návrháře](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
