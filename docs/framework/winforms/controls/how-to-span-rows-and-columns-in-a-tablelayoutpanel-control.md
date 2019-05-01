---
title: 'Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: 02db78b07930676235e55e535fb24f6ff618d823
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012968"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel
Ovládací prvky v <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek může mít rozsah sousední řádků a sloupců.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-span-columns-and-rows"></a>Rozložit sloupců a řádků  
  
1. Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.  
  
2. Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do buňky levého horního <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
3. Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **2**. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek zahrnuje prvního a druhého sloupce.  
  
4. Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **RowSpan** vlastnost **2**. Všimněte si, <xref:System.Windows.Forms.Button> první a druhý řádek obsahuje ovládací prvek.  
  
5. Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **1**. Všimněte si, <xref:System.Windows.Forms.Button> ovládacího prvku přesune na první sloupec a zahrnuje první a druhý řádek.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
