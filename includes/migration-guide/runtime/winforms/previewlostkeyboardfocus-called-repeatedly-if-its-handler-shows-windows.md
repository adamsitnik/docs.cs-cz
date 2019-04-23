---
ms.openlocfilehash: addfd55fd01b13e9088e4706ff846fc624aafa68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803705"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus je voláno opakovaně její obslužná rutina se zobrazí okno se zprávou Windows Forms

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> způsobí, že obslužná rutina obslužnou rutinu znovu vyvolána při zavření okna se zprávou, může mít za následek nekonečnou smyčku okna se zprávou.|
|Doporučení|Chcete-li tento problém obejít dvěma způsoby:<ol><li>Může se jim vyhnout voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> místo <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>Může se jim vyhnout tím, že zobrazuje zprávy <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> obslužné rutiny události (nikoli <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> obslužná rutina události).</li></ol>|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
