---
ms.openlocfilehash: 4f92d773197c914a74dd7e9c18f5aab5309358ae
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760828"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>Ujistěte se, že System.Uri používá konzistentní vyhrazené znakovou sadu

|   |   |
|---|---|
|Podrobnosti|V <xref:System.Uri?displayProperty=fullName>určité procentuálně zakódovaný znaky, které byly někdy dekódovat jsou nyní konzistentně vlevo kódování. Tato akce proběhne přes vlastnosti a metody, které přístup k součástem cestu, dotaz, fragment nebo informací o uživateli identifikátoru URI. Chování se změní, pouze pokud obě z následujících akcí jsou splněny:<ul><li>Identifikátor URI obsahuje kódované podobě některého z následující vyhrazené znaky: <code>:</code>, <code>'</code>, <code>(</code>, <code>)</code>, <code>!</code> nebo <code>*</code>.</li><li>Identifikátor URI obsahuje znakové sady Unicode nebo kódovaný nerezervované znaků. Pokud jsou splněny obě výše uvedené, jsou zakódovány vlevo kódovaného vyhrazené znaky. V předchozích verzích rozhraní .NET Framework se dekódovat.</li></ul>|
|Doporučení|U aplikací s cílovou verzí rozhraní .NET Framework počínaje 4.7.2 nové dekódování chování ve výchozím nastavení zapnutá. Pokud tuto změnu nežádoucí, můžete jej zakázat přidáním následujícího kódu [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepněte <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.2 počínaje verzí je ve výchozím nastavení zakázáno nové dekódování chování. Můžete ji povolit tak, že přidáte následující [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepněte <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

