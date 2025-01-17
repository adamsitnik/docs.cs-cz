---
title: 'Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: 82d0499cb40f79a3110b8432fbee66774bcc14a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013306"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar
Důležitou funkcí Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je, že uživatel může vybrat rozsah. Tato funkce je vylepšením oproti funkci Výběr data <xref:System.Windows.Forms.DateTimePicker> ovládací prvek, který pouze umožňuje uživateli vybrat hodnotu jednoho data a času. Můžete nastavit rozsah kalendářních dat nebo získat oblast výběru nastaven uživatelem s použitím vlastnosti <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku. Následující příklad kódu ukazuje, jak nastavit oblast výběru.  
  
### <a name="to-select-a-range-of-dates"></a>Vybrat rozsah kalendářních dat  
  
1. Vytvoření <xref:System.DateTime> objekty, které představují první a poslední datum v rozsahu.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2. Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> vlastnost.  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     – nebo –  
  
     Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> a <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> vlastnosti.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)
- [Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku](how-to-change-monthcalendar-control-appearance.md)
- [Postupy: Zobrazení konkrétních dnů Bold s Windows Forms MonthCalendar – ovládací prvek](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](display-more-than-one-month-wf-monthcalendar-control.md)
