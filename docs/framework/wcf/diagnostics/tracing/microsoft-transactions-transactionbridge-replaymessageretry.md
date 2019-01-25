---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: bb7f6fcf95d1ff253fa0e2963610bee2b65ef3c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597109"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="34fd1-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="34fd1-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="34fd1-103">Přehrání opakování zpráva se odeslala na poslána koordinátorovi, který.</span><span class="sxs-lookup"><span data-stu-id="34fd1-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="34fd1-104">Popis</span><span class="sxs-lookup"><span data-stu-id="34fd1-104">Description</span></span>  
 <span data-ttu-id="34fd1-105">Trasovaná v případě potřeby místní správce transakcí se opětovné poslání odpověď na dokonalá koordinátor, protože neobdržela odpověď v daném čase.</span><span class="sxs-lookup"><span data-stu-id="34fd1-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="34fd1-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="34fd1-106">Troubleshooting</span></span>  
 <span data-ttu-id="34fd1-107">Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="34fd1-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="34fd1-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="34fd1-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="34fd1-109">Oba problémy výrazně zkrátí propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="34fd1-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fd1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34fd1-110">See also</span></span>
- [<span data-ttu-id="34fd1-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="34fd1-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="34fd1-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="34fd1-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="34fd1-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="34fd1-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
