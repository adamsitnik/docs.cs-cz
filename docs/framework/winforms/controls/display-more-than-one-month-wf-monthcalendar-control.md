---
title: 'Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
ms.openlocfilehash: c2252ccf1c8fec0dcaba634e6da093ab976ce1f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614767"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar
Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek mohl zobrazit až 12 měsíců po jednom. Ve výchozím nastavení ovládací prvek zobrazuje pouze jeden měsíc, ale můžete určit, kolik měsíců se zobrazí a jak jsou uspořádány v ovládacím prvku. Pokud změníte rozměry kalendáře, ovládací prvek svou velikost, proto ujistěte se, že je dostatek volného místa ve formuláři pro nové dimenze.  
  
### <a name="to-display-multiple-months"></a>Chcete-li zobrazit více měsíců  
  
- Nastavte <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na počet měsíců k zobrazení vodorovně a svisle.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)
- [Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku](how-to-change-monthcalendar-control-appearance.md)
