---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760423"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="43b21-101">Aktualizace zásobníku tisk WPF</span><span class="sxs-lookup"><span data-stu-id="43b21-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="43b21-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="43b21-102">Details</span></span>|<span data-ttu-id="43b21-103">Pomocí rozhraní API pro tisk na WPF <xref:System.Printing.PrintQueue?displayProperty=name> nyní volat okna Tisk dokumentu balíčku API ve prospěch teď zastaralé rozhraní API tisk XPS.</span><span class="sxs-lookup"><span data-stu-id="43b21-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="43b21-104">Změny s použitelnost v úvahu; uživatelé ani vývojáři měli vidět všechny změny v chování nebo použití rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="43b21-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="43b21-105">Nový zásobník tisk je standardně povolená, když běží v systému Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="43b21-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="43b21-106">Staré zásobníku tisku bude nadále fungovat stejně jako v minulosti ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="43b21-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="43b21-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="43b21-107">Suggestion</span></span>|<span data-ttu-id="43b21-108">Chcete-li použít staré zásobníku ve Windows 10 Creators Update, nastavte <code>UseXpsOMPrinting</code> hodnota REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klíč registru, který <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="43b21-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="43b21-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="43b21-109">Scope</span></span>|<span data-ttu-id="43b21-110">Edge</span><span class="sxs-lookup"><span data-stu-id="43b21-110">Edge</span></span>|
|<span data-ttu-id="43b21-111">Version</span><span class="sxs-lookup"><span data-stu-id="43b21-111">Version</span></span>|<span data-ttu-id="43b21-112">4.7</span><span class="sxs-lookup"><span data-stu-id="43b21-112">4.7</span></span>|
|<span data-ttu-id="43b21-113">Type</span><span class="sxs-lookup"><span data-stu-id="43b21-113">Type</span></span>|<span data-ttu-id="43b21-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="43b21-114">Runtime</span></span>|

