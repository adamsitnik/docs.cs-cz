---
ms.openlocfilehash: 2413e1997b6e729b9d5889677e25254aaa24afea
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859350"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Nesprávná implementace MemberDescriptor.Equals

|   |   |
|---|---|
|Podrobnosti|Původní implementaci <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metoda porovná dvě vlastnosti rozdílnými řetězcovými z objektů, který se porovnává: název kategorie a řetězce popisu. Je k porovnání <xref:System.ComponentModel.MemberDescriptor.Category> první objektu, který se <xref:System.ComponentModel.MemberDescriptor.Category> druhý z nich a <xref:System.ComponentModel.MemberDescriptor.Description> prvního k <xref:System.ComponentModel.MemberDescriptor.Description> druhého.|
|Doporučení|Pokud je aplikace závislá na <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> někdy vrací <code>false</code> při popisovače jsou ekvivalentní a se zaměřujete na rozhraní .NET Framework 4.6.2 nebo novější, máte několik možností:<ol><li>Provádět změny kódu k porovnání <xref:System.ComponentModel.MemberDescriptor.Category> a <xref:System.ComponentModel.MemberDescriptor.Description> pole ručně kromě volání <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody.</li><li>Vyjádřit výslovný nesouhlas této změny do souboru app.config přidejte následující hodnotu:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pokud vaše aplikace cílí na .NET Framework 4.6.1 nebo starší a běží na rozhraní .NET Framework 4.6.2 nebo novější a chcete, aby tato změna povolené, přepínač kompatibility lze nastavit na <code>false</code> do souboru app.config přidejte následující hodnotu:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.6.2|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

