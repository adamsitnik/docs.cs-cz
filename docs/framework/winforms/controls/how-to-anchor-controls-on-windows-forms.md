---
title: 'Postupy: Ukotvení ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: b48761bda2baad4f7d1e6db9b41d73d6d54bc081
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211279"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Postupy: Ukotvení ovládacích prvků ve Windows Forms

Pokud navrhujete formulář, který uživatel může změnit velikost v době běhu, by měl ovládací prvky na formuláři změnit velikost a umístění správně. Změna velikosti ovládacích prvků dynamicky pomocí formuláře, můžete použít <xref:System.Windows.Forms.Control.Anchor%2A> vlastností ovládacích prvků Windows Forms. <xref:System.Windows.Forms.Control.Anchor%2A> Definuje vlastnost pozice ukotvení pro ovládací prvek. Když je ovládací prvek ukotven k formuláři a změně velikosti formuláře, ovládací prvek udržuje vzdálenost mezi ovládacím prvkem a pozice ukotvení. Například, pokud máte <xref:System.Windows.Forms.TextBox> ovládací prvek, který je ukotven doleva, doprava a dolů ve formuláři, při změně velikosti formuláře <xref:System.Windows.Forms.TextBox> vodorovně řídit změní tak, aby udržuje stejnou vzdálenost od pravá a levá strana formuláře. Kromě toho ovládací prvek umístí samotné svisle tak, aby jeho umístění je vždy stejnou vzdálenost od dolní části formuláře. Pokud není ukotven ovládacího prvku a změně velikosti formuláře, dojde ke změně pozice ovládacího prvku vzhledem k okrajům formuláře.

<xref:System.Windows.Forms.Control.Anchor%2A> Vlastnost komunikuje <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost. Další informace najdete v tématu [přehled vlastnosti AutoSize](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Ukotvit ovládací prvek ve formuláři

1. V sadě Visual Studio vyberte ovládací prvek, který chcete ukotvit.

    > [!NOTE]
    > Můžete ukotvit více ovládacích prvků současně klávesy CTRL, kliknutím na každý ovládací prvek a vyberte ho a budete postupovat zbývající část tohoto postupu.

2. V **vlastnosti** okna, klikněte na šipku vpravo od <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost.

     Editoru se zobrazí, který ukazuje na křížek.

3. Pokud chcete nastavit anchor, klikněte na tlačítko vlevo nahoře, pravé nebo dolní část křížového.

     Ovládací prvky jsou ukotven k horní a levé ve výchozím nastavení.

4. Na straně ovládacího prvku, který není ukotven, klikněte na tento arm křížové.

5. Zavřete <xref:System.Windows.Forms.Control.Anchor%2A> editoru vlastností klikněte <xref:System.Windows.Forms.Control.Anchor%2A> znovu název vlastnosti.

Při formuláři se zobrazí v době běhu, zůstane umístěné ve stejné vzdálenosti od levého okraje formuláře změní velikost ovládacího prvku. Vzdálenost od levého okraje ukotvené vždy zůstává definovaný vzdálenost, když je ovládací prvek umístěný v Návrháři formulářů Windows.

> [!NOTE]
> Některé ovládací prvky, jako například <xref:System.Windows.Forms.ComboBox> řídit, omezení jejich výšku. Ukotvení ovládacího prvku do dolní části formuláře nebo kontejneru nelze vynutit překročí limit výšku ovládacího prvku.

Zděděný ovládací prvky musí být `Protected` mohli být ukotven. Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho `Modifiers` vlastnost **vlastnosti** okna.

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Ukotvování ovládacích prvků ve Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)
