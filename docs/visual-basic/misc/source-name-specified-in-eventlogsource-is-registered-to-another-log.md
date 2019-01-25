---
title: Zadaný v EventLogSource název zdroje je zaregistrovaný do protokolu, než je zadaná v EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 4de98bef87b871036c3c5730ff09cf94c1df2918
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584568"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="8cfc6-102">Zadaný v EventLogSource název zdroje je zaregistrovaný do protokolu, než je zadaná v EventLogName</span><span class="sxs-lookup"><span data-stu-id="8cfc6-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="8cfc6-103">`EventLog` Se pokouší odkazovat na zdroj, který je registrovaný pro jiný protokol.</span><span class="sxs-lookup"><span data-stu-id="8cfc6-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="8cfc6-104">Pokud vytváříte položky do protokolu událostí, je nutné zadat <xref:System.Diagnostics.EventLog.Source%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8cfc6-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="8cfc6-105"><xref:System.Diagnostics.EventLog.Source%2A> Vlastnost zaregistruje vaše komponenta se do protokolu událostí jako platný zdroj položky.</span><span class="sxs-lookup"><span data-stu-id="8cfc6-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="8cfc6-106">Jeden zdroj může být spojen s (a proto zapisovat položky do) jenom jeden protokol událostí současně.</span><span class="sxs-lookup"><span data-stu-id="8cfc6-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="8cfc6-107">Ve výchozím nastavení, pokud se pokusíte pro zápis záznamu, aniž nejprve registraci komponenty jako platný zdroj, systém automaticky registruje zdroj protokolu událostí, použití hodnoty <xref:System.Diagnostics.EventLog.Source%2A> vlastnost jako zdrojový řetězec.</span><span class="sxs-lookup"><span data-stu-id="8cfc6-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8cfc6-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8cfc6-108">To correct this error</span></span>  
  
-   <span data-ttu-id="8cfc6-109">Zajistěte, aby že zdroj je registrován do správné protokolu.</span><span class="sxs-lookup"><span data-stu-id="8cfc6-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="8cfc6-110">Chcete-li to provést, použijte <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody nebo jeden z jejich přetížení zadat řetězec, který jednoznačně identifikuje vaše komponenta do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="8cfc6-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfc6-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cfc6-111">See also</span></span>
- [<span data-ttu-id="8cfc6-112">Správa protokolů událostí</span><span class="sxs-lookup"><span data-stu-id="8cfc6-112">Administering Event Logs</span></span>](https://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)
- [<span data-ttu-id="8cfc6-113">Odkazy protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="8cfc6-113">Event Log References</span></span>](https://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)
- [<span data-ttu-id="8cfc6-114">Postupy: Přidejte svoji aplikaci jako zdroj položky protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="8cfc6-114">How to: Add Your Application as a Source of Event Log Entries</span></span>](https://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)
- [<span data-ttu-id="8cfc6-115">Postupy: Odebrat zdroje událostí</span><span class="sxs-lookup"><span data-stu-id="8cfc6-115">How to: Remove an Event Source</span></span>](https://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
