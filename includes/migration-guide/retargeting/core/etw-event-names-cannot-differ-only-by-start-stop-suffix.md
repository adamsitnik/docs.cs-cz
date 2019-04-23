---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803687"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="ebe42-101">Názvy událostí trasování událostí pro Windows nelze odlišit pouze podle přípony "Start" nebo "Stop"</span><span class="sxs-lookup"><span data-stu-id="ebe42-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ebe42-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ebe42-102">Details</span></span>|<span data-ttu-id="ebe42-103">V rozhraní .NET Framework 4.6 a 4.6.1, modul runtime vyvolá <xref:System.ArgumentException> při dva názvy událostí trasování událostí pro Windows (ETW) se liší pouze &quot;Start&quot; nebo &quot;Zastavit&quot; příponu (jako když je jedna událost s názvem <code>LogUser</code>a druhou s názvem <code>LogUserStart</code>).</span><span class="sxs-lookup"><span data-stu-id="ebe42-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="ebe42-104">V takovém případě modul runtime nelze vytvořit zdroj události, které nelze generovat žádné protokolování.</span><span class="sxs-lookup"><span data-stu-id="ebe42-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="ebe42-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="ebe42-105">Suggestion</span></span>|<span data-ttu-id="ebe42-106">Aby se zabránilo výjimku, ujistěte se, že žádné názvy dvou událostí se liší pouze &quot;Start&quot; nebo &quot;Zastavit&quot; příponu. Tento požadavek je odebrána od verze rozhraní .NET Framework 4.6.2; modul runtime může rozlišit názvy událostí, které se liší pouze &quot;Start&quot; a &quot;Zastavit&quot; příponu.</span><span class="sxs-lookup"><span data-stu-id="ebe42-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="ebe42-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ebe42-107">Scope</span></span>|<span data-ttu-id="ebe42-108">Edge</span><span class="sxs-lookup"><span data-stu-id="ebe42-108">Edge</span></span>|
|<span data-ttu-id="ebe42-109">Version</span><span class="sxs-lookup"><span data-stu-id="ebe42-109">Version</span></span>|<span data-ttu-id="ebe42-110">4.6</span><span class="sxs-lookup"><span data-stu-id="ebe42-110">4.6</span></span>|
|<span data-ttu-id="ebe42-111">Type</span><span class="sxs-lookup"><span data-stu-id="ebe42-111">Type</span></span>|<span data-ttu-id="ebe42-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="ebe42-112">Retargeting</span></span>|
