---
ms.openlocfilehash: 62ba525a28960d96c5458aa1481e1f319d5bc875
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859237"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current můžou vrátit hodnotu null při volání do pomocí klauzule

|   |   |
|---|---|
|Podrobnosti|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> může vrátit <code>null</code> a <xref:System.NullReferenceException> může dojít, pokud jsou splněny všechny následující podmínky:<ul><li>Načtení hodnoty <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> vlastnost v metodě, která vrátí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</li><li>Můžete vytvořit instanci <xref:System.ServiceModel.OperationContextScope> objekt <code>using</code> klauzuli.</li><li>Načtení hodnoty <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> vlastnosti v rámci <code>using statement</code>. Příklad:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Doporučení|A tento problém vyřešit, můžete provést následující:<ul><li>Upravit kód pro vytvoření instance nového jinou hodnotu než<code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A> objektu:</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Nainstalujte nejnovější aktualizaci rozhraní .NET Framework 4.6.2, nebo upgradujte na novější verzi rozhraní .NET Framework. Zakáže tok <xref:System.Threading.ExecutionContext> v <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> a obnoví chování aplikací služby WCF v rozhraní .NET Framework 4.6.1 a dřívějších verzích. Toto chování je možné konfigurovat; je ekvivalentní k přidání nastavení aplikace, které následující konfigurační soubor:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Pokud tuto změnu nežádoucí, vaše aplikace závisí na kontextu spuštění mezi kontexty operace můžete povolit tok následujícím způsobem:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.6.2|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|

