---
ms.openlocfilehash: de40d16dbb5e7a7a49ae0988342b3eb75bc078c5
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804437"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture a CurrentUICulture téct přes úlohy

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> se ukládají do vlákna <xref:System.Threading.ExecutionContext?displayProperty=name>, který průchodu asynchronních operací. To znamená, že se změní na <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> se projeví v úlohách, které jsou dále běží asynchronně. Tím se liší od chování z předchozích verzí rozhraní .NET Framework (což by resetování <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> ve všech asynchronních úloh).|
|Doporučení|Touto změnou ovlivněny aplikace může obejít explicitním nastavením požadovaný <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> jako první operace asynchronní úlohy. Alternativně staré chování (ne průchodu <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) může být přihlášení ke službě tak, že nastavíte následující přepínače kompatibility:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Tento problém byl vyřešen ve WPF v rozhraní .NET Framework 4.6.2. Také jsme opravili .NET Framework 4.6, 4.6.1 prostřednictvím [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikace cílené na rozhraní .NET Framework 4.6 nebo novější, automaticky získá správné chování v aplikaci WPF – <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) by zachovaná napříč operace dispečera.|
|Scope|Vedlejší|
|Version|4.6|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|

