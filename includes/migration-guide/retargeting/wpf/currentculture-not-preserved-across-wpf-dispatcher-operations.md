---
ms.openlocfilehash: cce19d6c9afa5f5ce9bb17b5b5d92f2060a08414
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804593"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>CurrentCulture nezachová v objektu WPF Dispatcher operace

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.6, se změní na <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> v rámci <xref:System.Windows.Threading.Dispatcher?displayProperty=name> ztratí na konci této operace dispečera. Podobně změny <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> provedené mimo dispečera operace nemusí odrážet při, že se spustí operace. Prakticky mluvy, to znamená, že <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> změny nemusí tok mezi zpětná volání rozhraní WPF a jiný kód v aplikaci WPF. Toto je z důvodu změn v <xref:System.Threading.ExecutionContext?displayProperty=name> , který způsobí, že <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> uloží na začátku kontextu spuštění v rámci aplikace využívající rozhraní .NET Framework 4.6. WPF dispatcher operace ukládání kontextu spuštění pro operace begin a obnovení předchozí kontext po dokončení operace. Protože <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> jsou teď součástí daného kontextu, nejsou trvalé změny v rámci operace dispečer mimo provoz.|
|Doporučení|Touto změnou ovlivněny aplikace může obejít uložením požadovaný <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> v poli a vracet se změnami všechny operace těla dispečer (včetně obslužné rutiny zpětných volání události uživatelského rozhraní), který správné <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> jsou nastavené. Případně protože kontextu ExecutionContext změnit základní tato WPF změna ovlivní pouze aplikace určené pro rozhraní .NET Framework 4.6 nebo novější, pomocí cílení na rozhraní .NET Framework 4.5.2.Apps, který cílit na .NET Framework 4.6 nebo novější můžete také pracovat se lze vyvarovat této přerušení vyřešit tak, že nastavíte následující kompatibility přepínače:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Tento problém byl vyřešen ve WPF v rozhraní .NET Framework 4.6.2. Také jsme opravili .NET Framework 4.6, 4.6.1 prostřednictvím [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikace cílené na rozhraní .NET Framework 4.6 nebo novější, automaticky získá správné chování v aplikaci WPF – <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) by zachovaná napříč operace dispečera.|
|Scope|Vedlejší|
|Version|4.6|
|type|Změna cílení|

