---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803694"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="81834-101">Textové pole WPF vybraný text se zobrazí odlišnou barvou, když do textového pole je neaktivní</span><span class="sxs-lookup"><span data-stu-id="81834-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="81834-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="81834-102">Details</span></span>|<span data-ttu-id="81834-103">V rozhraní .NET Framework 4.5, když je neaktivní ovládacího prvku WPF textového pole (nemá fokus), zobrazí se vybraný text v poli jinou barvou, než když je aktivní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="81834-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="81834-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="81834-104">Suggestion</span></span>|<span data-ttu-id="81834-105">Může se obnovit předchozí chování (.NET Framework 4.0) tak, že nastavíte <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnost <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="81834-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="81834-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="81834-106">Scope</span></span>|<span data-ttu-id="81834-107">Edge</span><span class="sxs-lookup"><span data-stu-id="81834-107">Edge</span></span>|
|<span data-ttu-id="81834-108">Version</span><span class="sxs-lookup"><span data-stu-id="81834-108">Version</span></span>|<span data-ttu-id="81834-109">4.5</span><span class="sxs-lookup"><span data-stu-id="81834-109">4.5</span></span>|
|<span data-ttu-id="81834-110">Type</span><span class="sxs-lookup"><span data-stu-id="81834-110">Type</span></span>|<span data-ttu-id="81834-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="81834-111">Runtime</span></span>|
|<span data-ttu-id="81834-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="81834-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
