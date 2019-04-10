---
ms.openlocfilehash: e6c93a1bc31c041f36fca3704bca32012a2b42ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236374"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Selektor SelectionChanged událostí a vlastnost SelectedValue

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, <xref:System.Windows.Controls.Primitives.Selector> vždy aktualizuje hodnotu jeho <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost vyčkat, než se <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> událost, když se změní jeho výběr. Díky tomu je vlastnost SelectedValue konzistentní s jinými vlastnostmi výběru (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> a <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), které se aktualizují před vyvoláním události.<p/>V rozhraní .NET Framework 4.7 a dřívějších verzích, aktualizace, která se SelectedValue ke kterým došlo před událostí ve většině případů, ale to nastalo po události, je-li změnit výběr se tak, že změníte <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost.|
|Doporučení|Aplikace, které se zaměřují rozhraní .NET Framework 4.7.1 nebo novější můžete zrušit to změnit a použít starší verzi chování přidáním následujícího <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na .NET Framework 4.7 nebo starší ale jsou spuštěny v rozhraní .NET Framework 4.7.1 nebo novější můžete povolit nové chování tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> .configuration souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
