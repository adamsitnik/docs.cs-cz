---
title: 'Postupy: Tisk klientské oblasti formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: 2c808b480c38fc34006dcdf5832a814dfef1c62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505624"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a>Postupy: Tisk klientské oblasti formuláře (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje rychlý tisk obrázek formuláře bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty. Následující postup ukazuje, jak vytisknout jenom klientské oblasti formuláře, bez záhlaví, ohraničení a posuvníky.  
  
 Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-client-area-of-a-form"></a>Tisk klientské oblasti formuláře  
  
1.  V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.  
  
2.  V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  V některých operačních systémů, textové nebo grafické vykreslené <xref:System.Drawing.Graphics> metody nestiskne správně. V takovém případě použijte metodu kompatibilní tisku: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>
- [Komponenta PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
- [Postupy: Tisk klientských a neklientských oblastí formuláře](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [Postupy: Tisk posuvného formuláře](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
