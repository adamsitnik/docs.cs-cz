---
title: Použití delegáta AsyncCallback a stavového objektu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb62b191dc3b3246745f9f0ea3737ed74a2bf57b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699003"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="3e7cb-102">Použití delegáta AsyncCallback a stavového objektu</span><span class="sxs-lookup"><span data-stu-id="3e7cb-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="3e7cb-103">Při použití <xref:System.AsyncCallback> delegovat ke zpracování výsledků asynchronních operací v samostatném vlákně, můžete použít stav objektu k předávání informací mezi zpětných dotazů a k načítání konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="3e7cb-104">Toto téma popisuje tento postup tak, že rozbalíte v příkladu v [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="3e7cb-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e7cb-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e7cb-105">Example</span></span>  
 <span data-ttu-id="3e7cb-106">Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třídy se načíst informace o systému DNS (Domain Name) pro počítače zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="3e7cb-107">Tento příklad definuje a používá `HostRequest` třídu pro ukládání informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="3e7cb-108">A `HostRequest` objekt se vytvoří pro každý název počítače zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="3e7cb-109">Tento objekt je předán <xref:System.Net.Dns.BeginGetHostByName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="3e7cb-110">`ProcessDnsInformation` Metoda je volána pokaždé, když se dokončí požadavek.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="3e7cb-111">`HostRequest` Objektu jsou načítány s použitím <xref:System.IAsyncResult.AsyncState%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="3e7cb-112">`ProcessDnsInformation` Metoda používá `HostRequest` objekt pro uložení <xref:System.Net.IPHostEntry> vráceným žádostí nebo <xref:System.Net.Sockets.SocketException> vyvolána v požadavku.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="3e7cb-113">Po dokončení všech žádostí aplikace iteruje `HostRequest` objekty a zobrazí informace o DNS nebo <xref:System.Net.Sockets.SocketException> chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="3e7cb-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3e7cb-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e7cb-114">See also</span></span>

- [<span data-ttu-id="3e7cb-115">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="3e7cb-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="3e7cb-116">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="3e7cb-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="3e7cb-117">Použití delegáta AsyncCallback k ukončení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="3e7cb-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
