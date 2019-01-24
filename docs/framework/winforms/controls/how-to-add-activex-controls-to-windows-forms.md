---
title: 'Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 2fa5d81c196e1730eafb177b20b5cba64b2daae1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721142"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows
Zatímco Návrhář formulářů Windows je optimalizována pro hostitelské ovládací prvky Windows Forms, lze také umístit ovládací prvky ActiveX v modelu Windows Forms.  
  
> [!CAUTION]
>  Existují omezení výkonu pro Windows Forms, kdy ovládací prvky ActiveX jsou k nim přidány.  
  
 Předtím, než přidáte do svého formuláře ovládací prvky ActiveX, musíte je přidat do panelu nástrojů. Další informace najdete v tématu [komponenty modelu COM, dialogové okno přizpůsobení panelu nástrojů](https://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Chcete-li přidat ovládací prvek ActiveX do formuláře Windows  
  
-   Poklepejte na ovládací prvek na panelu nástrojů.  
  
     Visual Studio přidá všechny odkazy na ovládací prvek ve vašem projektu. Další informace o co je potřeba vzít v úvahu při použití ovládacích prvků ActiveX do formulářů Windows, naleznete v tématu [aspekty hostování ovládacího prvku ActiveX ve formuláři Windows](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Importér ovládacích prvků ActiveX Windows Forms (AxImp.exe) vytvoří argumenty událostí jiného typu než se čekalo na Import knihoven DLL ActiveX. Argumenty vytvořené AxImp.exe se nějak takto: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, když `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` se očekává. Mějte na paměti, že tato nesrovnalost nebrání kód funguje normálně. Podrobnosti najdete v tématu [Importér ovládacích prvků Windows Forms ActiveX (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Viz také:
- [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)
- [Ovládacích prvků a programovatelných objektů porovnáno v různých jazycích a knihovnách](https://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
