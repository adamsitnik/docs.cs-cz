---
title: 'Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: 56391777c75db288c33d1b2192355be0df50f7ee
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046124"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox

Pole pro heslo je model Windows Forms textové pole, které zobrazuje zástupné znaky, když uživatel zadá řetězec.

### <a name="to-create-a-password-text-box"></a>Vytvoření textového pole pro heslo

1. <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Nastavte vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na konkrétní znak.

    <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Vlastnost určuje znak zobrazený v textovém poli. Například pokud chcete, aby se v poli heslo zobrazovaly hvězdičky, zadejte * pro <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v okno Vlastnosti. Bez ohledu na to, jaký znak má uživatel v textovém poli, se zobrazí hvězdička.

2. Volitelné <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> Nastavte vlastnost. Vlastnost určuje, kolik znaků lze zadat do textového pole. Pokud je překročena maximální délka, systém vygeneruje zvukový signál a textové pole nepřijímá žádné další znaky. Mějte na paměti, že to nebudete chtít udělat, protože maximální délka hesla může být použita pro hackery, kteří se pokoušejí uhodnout heslo.

    Následující příklad kódu ukazuje, jak inicializovat textové pole, které bude akceptovat řetězec o délce až 14 znaků a zobrazit hvězdičky namísto řetězce. `InitializeMyControl` Procedura se neprovede automaticky, musí být volána.

    > [!IMPORTANT]
    > <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Použití vlastnosti v textovém poli vám může pomoci zajistit, že jiní uživatelé nebudou moci určit heslo uživatele, pokud budou sledovat uživatele. Tato míra zabezpečení nepokrývá žádné řazení úložiště ani přenos hesla, ke kterým může dojít z důvodu vaší logiky aplikace. Vzhledem k tomu, že zadaný text není jakýmkoli způsobem zašifrovaný, měli byste s ním zacházet stejně jako s jinými důvěrnými údaji. I když se nezobrazuje jako takový, heslo se pořád považuje za řetězec s prostým textem (Pokud jste neimplementovali nějaké další bezpečnostní opatření).

    ```vb
    Private Sub InitializeMyControl()
       ' Set to no text.
       TextBox1.Text = ""
       ' The password character is an asterisk.
       TextBox1.PasswordChar = "*"
       ' The control will allow no more than 14 characters.
       TextBox1.MaxLength = 14
    End Sub
    ```

    ```csharp
    private void InitializeMyControl()
    {
       // Set to no text.
       textBox1.Text = "";
       // The password character is an asterisk.
       textBox1.PasswordChar = '*';
       // The control will allow no more than 14 characters.
       textBox1.MaxLength = 14;
    }
    ```

    ```cpp
    private:
       void InitializeMyControl()
       {
          // Set to no text.
          textBox1->Text = "";
          // The password character is an asterisk.
          textBox1->PasswordChar = '*';
          // The control will allow no more than 14 characters.
          textBox1->MaxLength = 14;
       }
    ```

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku TextBox model Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vložení uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku model Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazit více řádků v ovládacím prvku model Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
