---
ms.openlocfilehash: dfc1a0d05142861ff1c1b7391126d86e09fa71c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235291"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="7a8ce-101">WebUtility.HtmlDecode už dekóduje neplatné vstupní sekvence</span><span class="sxs-lookup"><span data-stu-id="7a8ce-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7a8ce-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7a8ce-102">Details</span></span>|<span data-ttu-id="7a8ce-103">Ve výchozím nastavení metody dekódování již neprovádějí dekódování neplatné vstupní sekvence do neplatného řetězce UTF-16.</span><span class="sxs-lookup"><span data-stu-id="7a8ce-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="7a8ce-104">Namísto toho vracejí původní vstup.</span><span class="sxs-lookup"><span data-stu-id="7a8ce-104">Instead, they return the original input.</span></span>|
|<span data-ttu-id="7a8ce-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="7a8ce-105">Suggestion</span></span>|<span data-ttu-id="7a8ce-106">Změna dekodéru výstupu by měla mít vliv, pouze pokud do řetězců ukládáte binární data namísto dat UTF-16.</span><span class="sxs-lookup"><span data-stu-id="7a8ce-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="7a8ce-107">Pokud chcete explicitně kontrolovat toto chování, nastavte <code>aspnet:AllowRelaxedUnicodeDecoding</code> atribut [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) elementu <code>true</code> abyste povolili starší chování nebo <code>false</code> k povolili aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="7a8ce-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>|
|<span data-ttu-id="7a8ce-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7a8ce-108">Scope</span></span>|<span data-ttu-id="7a8ce-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="7a8ce-109">Minor</span></span>|
|<span data-ttu-id="7a8ce-110">Version</span><span class="sxs-lookup"><span data-stu-id="7a8ce-110">Version</span></span>|<span data-ttu-id="7a8ce-111">4.5</span><span class="sxs-lookup"><span data-stu-id="7a8ce-111">4.5</span></span>|
|<span data-ttu-id="7a8ce-112">Type</span><span class="sxs-lookup"><span data-stu-id="7a8ce-112">Type</span></span>|<span data-ttu-id="7a8ce-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="7a8ce-113">Runtime</span></span>|
|<span data-ttu-id="7a8ce-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7a8ce-114">Affected APIs</span></span>|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
