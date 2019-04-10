---
ms.openlocfilehash: 347b6ccb3e986d820514159179c824c28907fc62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236408"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Vylepšení přístupnosti technologie ASP.NET v rozhraní .NET Framework 4.7.1

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, technologie ASP.NET je vylepšené fungování webové ovládací prvky technologie ASP.NET s technologiemi přístupnosti v sadě Visual Studio lepší podporu technologie ASP.NET zákazníkům.  Patří mezi ně následující změny:<ul><li>Změny pro implementaci chybějící vzory usnadnění přístupu uživatelského rozhraní v ovládacích prvcích, jako dialogové okno Přidat pole v zobrazení podrobností o průvodce nebo dialogové okno Konfigurace ListView Průvodce ListView.</li><li>Editor pole stránkování dat, jako jsou změny ke zlepšení zobrazení v režimu vysokého kontrastu.</li><li>Změny pro zlepšení navigace klávesnice, prostředí pro ovládací prvky, jako je dialogové okno pole v Průvodci úpravy polí stránkování ovládací prvek DataPager, dialogové okno Konfigurovat ObjectContext nebo dialogové okno Konfigurovat výběr dat v Průvodci nakonfigurujte zdroj dat.</li></ul>|
|Doporučení|<strong>Jak aktivování nebo zrušení těchto změn</strong>mohl Návrhář Visual Studio, abyste využili výhod tyto změny, musíte spustit na rozhraní .NET Framework 4.7.1 nebo novější. Webová aplikace využívat tyto změny v některém z následujících způsobů:<ul><li>Nainstalovat Visual Studio 2017 15.3 nebo novější, který podporuje nové funkce pro usnadnění přístupu s následující přepínač AppContext ve výchozím nastavení.</li><li>Odhlásit ze starší verze usnadnění chování tak, že přidáte <code>Switch.UseLegacyAccessibilityFeatures</code> přepínač AppContext k <code>&lt;runtime&gt;</code> oddílu v souboru devenv.exe.config a nastavíte ho na <code>false</code>, jak ukazuje následující příklad.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikací určených pro rozhraní .NET Framework 4.7.1 nebo novější a chcete zachovat starší chování usnadnění můžete přejít k používání funkce starší verze usnadnění explicitním nastavením na tento přepínač AppContext <code>true</code>.|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Type|Změna cílení|
