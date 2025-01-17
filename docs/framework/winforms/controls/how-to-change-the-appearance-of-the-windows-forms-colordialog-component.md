---
title: 'Postupy: Změna vzhledu komponenty Windows Forms ColorDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: d2bb9e06d9d84a9b61c67510e9c012066f69d55e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595449"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Postupy: Změna vzhledu komponenty Windows Forms ColorDialog
Můžete nakonfigurovat vzhledu Windows Forms <xref:System.Windows.Forms.ColorDialog> komponentu s celou řadou její vlastnosti. Dialogové okno obsahuje dvě části – ten, který zobrazuje základní barvy a ten, který umožňuje uživateli definovat vlastní barvy.  
  
 Většina vlastností omezení jaké barev, může uživatel vybrat z dialogového okna. Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `true`, uživatel může definovat vlastní barvy. <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Vlastnost `true` Pokud dialogovém rozbalen a definovat vlastní barvy; jinak uživatel musí kliknout na tlačítko "Definovat vlastní barvy". Když <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> je nastavena na `true`, zobrazí dialogové okno v sadě základních barev všechny barvy k dispozici. Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat dithered pro bitové barvy, jsou k dispozici k výběru pouze plné barvy.  
  
 Pokud <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> je nastavena na `true`, v dialogovém okně se zobrazí tlačítko Nápověda. Když uživatel klikne na tlačítko Nápověda <xref:System.Windows.Forms.ColorDialog> komponenty <xref:System.Windows.Forms.CommonDialog.HelpRequest> událost se vyvolá.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Konfigurace vzhledu dialogové okno barev  
  
1. Nastavte <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, a <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> vlastnosti na požadované hodnoty.  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ColorDialog>
- [Komponenta ColorDialog](colordialog-component-windows-forms.md)
- [Přehled komponenty ColorDialog](colordialog-component-overview-windows-forms.md)
