---
title: 'Postupy: Určení modifikační klávesy, která byla stisknuta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 571af49cdf82b876cfb72a7c7636874c8d155fb7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213933"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Postupy: Určení modifikační klávesy, která byla stisknuta
Když vytvoříte aplikaci, která přijímá stisknutí kláves uživatele, můžete také sledovat modifikační klávesy, jako je například klávesy SHIFT, ALT a CTRL. Při stisknutí modifikační klávesa v kombinaci s další klíče nebo pomocí kliknutí myší, může vaše aplikace reagovat odpovídajícím způsobem. Například pokud se stiskne písmeno S, to může způsobit jednoduše "s" se zobrazí na obrazovce, ale pokud stisknutí kláves CTRL + S, může být aktuální dokument uložen. Pokud zpracováváte <xref:System.Windows.Forms.Control.KeyDown> událostí, <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> přijatá událost obslužné rutiny Určuje, která modifikátor stisknutí kláves. Další možností <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> Určuje znak, která byla stisknuta stejně jako jakékoli modifikační klávesy, v kombinaci s bitový operátor OR. Nicméně pokud obsluhujete <xref:System.Windows.Forms.Control.KeyPress> událost nebo událost myši, obslužná rutina události neobdrží tyto informace. V takovém případě musíte použít <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnost <xref:System.Windows.Forms.Control> třídy. V obou případech je nutné provést bitový operátor AND příslušné <xref:System.Windows.Forms.Keys> hodnoty a hodnoty, které testujete. <xref:System.Windows.Forms.Keys> Výčet nabízí varianty každého modifikační klávesa, takže je důležité, abyste provedli bitový a správnou hodnotu. Například je reprezentována klávesu SHIFT <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> a <xref:System.Windows.Forms.Keys.LShiftKey> správnou hodnotu pro testování SHIFT je modifikační klávesa <xref:System.Windows.Forms.Keys.Shift>. Obdobně test pro CTRL a ALT jako modifikátory jste měli by používat <xref:System.Windows.Forms.Keys.Control> a <xref:System.Windows.Forms.Keys.Alt> hodnoty v uvedeném pořadí.  
  
> [!NOTE]
>  Programátoři v jazyce Visual Basic se dostanete také informace o klíči prostřednictvím <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> vlastnost  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>K určení modifikační klávesy, která byla stisknuta  
  
-   Použít bitový `AND` operátor s <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnosti a hodnotu <xref:System.Windows.Forms.Keys> výčet k určení, zda je konkrétní modifikační klávesa stisknuta. Následující příklad kódu ukazuje, jak určit, zda je klávesa SHIFT stisknuta v rámci <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Vstup z klávesnice v aplikaci Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Postupy: Určení, že CapsLock – Pokud je v jazyce Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
