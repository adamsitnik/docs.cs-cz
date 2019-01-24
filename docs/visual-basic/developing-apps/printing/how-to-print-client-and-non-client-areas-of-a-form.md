---
title: 'Postupy: Tisk klientských i Neklientských oblastí formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: b32b5bc6cfe45f38b9eb5a0df0778eb02d827d21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685076"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a>Postupy: Tisk klientských i Neklientských oblastí formuláře (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje rychlý tisk obrázek formuláře přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty. Následující postup ukazuje, jak tisk formuláře, včetně klientské oblasti a neklientská oblast. Neklientská oblast obsahuje záhlaví, ohraničení a posuňte pruhy.  
  
 Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a>Pro tisk klientských i neklientských oblastí formuláře  
  
1.  V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.  
  
2.  V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny události pro tisku `Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  V některých operačních systémů, textové nebo grafické vykreslené <xref:System.Drawing.Graphics> metody nestiskne správně. In this Case, použijte metodu kompatibilní tisku: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>
- [Komponenta PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
- [Postupy: Tisk posuvného formuláře](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
