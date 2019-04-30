---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: d56bbf145c85902d8e5f1fd21f760633121da6da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939215"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="e637a-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="e637a-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="e637a-103">Nelze přesunout nebo odstraňovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="e637a-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e637a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e637a-104">Description</span></span>  
 <span data-ttu-id="e637a-105">Trasování označuje, že došlo k chybě při pokusu o přesunutí, odstraňte nebo odmítnout zprávu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e637a-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="e637a-106">Zprávy služby MSMQ se použijí ve Windows Communication Foundation (WCF) (při použití s NetMsmqBinding nebo třídu MsmqIntegrationBinding). Trasování souvisí s zvolená hodnota `ReceiveErrorHandling` vlastnosti NetMsmqBinding nebo vazbu MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="e637a-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="e637a-107">Trasování není indikátorem celkového selhání systému.</span><span class="sxs-lookup"><span data-stu-id="e637a-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="e637a-108">Ale znamená, že zvolený zacházení s nezpracovatelnými zpráva dispozice pro zprávy se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e637a-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="e637a-109">Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.</span><span class="sxs-lookup"><span data-stu-id="e637a-109">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e637a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e637a-110">See also</span></span>

- [<span data-ttu-id="e637a-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="e637a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e637a-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e637a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e637a-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e637a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
