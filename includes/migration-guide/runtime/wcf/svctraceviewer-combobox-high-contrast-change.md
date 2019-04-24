---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982163"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="9e0ea-101">Změna vysoký kontrast – pole se seznamem svcTraceViewer</span><span class="sxs-lookup"><span data-stu-id="9e0ea-101">svcTraceViewer ComboBox high contrast change</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9e0ea-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9e0ea-102">Details</span></span>|<span data-ttu-id="9e0ea-103">V [nástroje prohlížeče trasování služeb Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox – ovládací prvky se zobrazí v správná barva v určitých vysokokontrastních motivech.</span><span class="sxs-lookup"><span data-stu-id="9e0ea-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="9e0ea-104">Problém byl vyřešen v rozhraní .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="9e0ea-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="9e0ea-105">Ale z důvodu zpětné kompatibility požadavky rozhraní .NET Framework SDK, opravy nebyla pro zákazníky ve výchozím nastavení viditelné.</span><span class="sxs-lookup"><span data-stu-id="9e0ea-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="9e0ea-106">.NET 4.8 poskytuje informace o této změně přidáním následujícího kódu [konfigurace přepínačů AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) svcTraceViewer.exe.config souboru:</span><span class="sxs-lookup"><span data-stu-id="9e0ea-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="9e0ea-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9e0ea-107">Suggestion</span></span>|<ul><li><span data-ttu-id="9e0ea-108">Jak se pokud chcete odhlásit změny, pokud už nechcete mít vysoký kontrast chování změnit, můžete jej zakázat tak, že odeberete ze souboru svcTraceViewer.exe.config v následující části:</span><span class="sxs-lookup"><span data-stu-id="9e0ea-108">How to opt out of the change If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span></li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="9e0ea-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9e0ea-109">Scope</span></span>|<span data-ttu-id="9e0ea-110">Edge</span><span class="sxs-lookup"><span data-stu-id="9e0ea-110">Edge</span></span>|
|<span data-ttu-id="9e0ea-111">Version</span><span class="sxs-lookup"><span data-stu-id="9e0ea-111">Version</span></span>|<span data-ttu-id="9e0ea-112">4.8</span><span class="sxs-lookup"><span data-stu-id="9e0ea-112">4.8</span></span>|
|<span data-ttu-id="9e0ea-113">Type</span><span class="sxs-lookup"><span data-stu-id="9e0ea-113">Type</span></span>|<span data-ttu-id="9e0ea-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="9e0ea-114">Runtime</span></span>|