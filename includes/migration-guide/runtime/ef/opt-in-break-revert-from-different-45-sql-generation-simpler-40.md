---
ms.openlocfilehash: 64d540278544e74c46d46b77c97bccd26d4116dd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803164"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Konec vyjádřit výslovný souhlas se vrátit z různých 4.5 generování SQL pro jednodušší 4.0 generování SQL

|   |   |
|---|---|
|Podrobnosti|Dotazy, které vytvářejí Příkazy JOIN a obsahovat volání limitující operace, aniž byste nejdřív pomocí OrderBy nyní vytvořit jednodušší SQL. Po upgradu na rozhraní .NET Framework 4.5, vytváří tyto dotazy SQL složitější než předchozí verze.|
|Doporučení|Tato funkce je ve výchozím nastavení zakázaná. Pokud rozhraní Entity Framework generuje dodatečné příkazy JOIN, které způsobují snížení výkonu, můžete tuto funkci povolíte tak, že přidáte následující položky <code>&lt;appSettings&gt;</code> souboru konfigurace (app.config) aplikace:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Scope|Transparentní|
|Version|4.5.2|
|type|Modul runtime|

