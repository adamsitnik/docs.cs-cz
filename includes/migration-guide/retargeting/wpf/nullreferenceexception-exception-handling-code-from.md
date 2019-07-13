---
ms.openlocfilehash: 122741d13294c8b137ce48e28f0aa39c6e36265a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859130"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException v kódu z ImageSourceConverter.ConvertFrom pro zpracování výjimek

|   |   |
|---|---|
|Podrobnosti|Chyba v kód pro zpracování výjimek <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> způsobit nesprávné <xref:System.NullReferenceException?displayProperty=name> vyvolání namísto zamýšlené výjimky ( <xref:System.IO.DirectoryNotFoundException?displayProperty=name> nebo <xref:System.IO.FileNotFoundException?displayProperty=name>). Tato změna řeší tuto chybu tak, aby metoda vyvolá nyní správná výjimka. <p/>Tím, že výchozí všechny aplikace, které cílí na rozhraní .NET Framework 4.6.2 a starší i nadále throw <xref:System.NullReferenceException?displayProperty=name> z důvodu kompatibility. Vývojáři cílí na .NET Framework 4.7 výše by se zobrazit správné výjimky.|
|Doporučení|Vývojáři, kteří chtějí vrátit k získání <xref:System.NullReferenceException?displayProperty=name> při cílení na rozhraní .NET Framework 4.7 nebo novější můžete přidat/merge následujícího souboru App.config jejich aplikace:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

