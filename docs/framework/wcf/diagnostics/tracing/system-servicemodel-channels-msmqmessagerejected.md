---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 4feeb1b57d79c7445d51f5d688b0a9f55e761542
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143387"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="79ed7-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="79ed7-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="79ed7-103">MSMQ odmítl zprávu.</span><span class="sxs-lookup"><span data-stu-id="79ed7-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="79ed7-104">Popis</span><span class="sxs-lookup"><span data-stu-id="79ed7-104">Description</span></span>  
 <span data-ttu-id="79ed7-105">Trasování označuje, že zprávy MSMQ byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="79ed7-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="79ed7-106">Když (používá se NetMsmqBinding nebo vazbu MsmqIntegrationBinding) Windows Communication Foundation (WCF) není schopen se jejich zpracování může být odmítnutá zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="79ed7-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="79ed7-107">Tyto zprávy jsou označovány jako počet nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="79ed7-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="79ed7-108">Nezpracovatelná zpráva zamítá při `ReceiveErrorHandling` NetMsmqBinding nebo vazbu MsmqIntegrationBinding je nastavena na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="79ed7-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="79ed7-109">Odmítnuté zprávy se doručí zpět do odesílatele [fronty nedoručených zpráv](https://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="79ed7-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="79ed7-110">Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.</span><span class="sxs-lookup"><span data-stu-id="79ed7-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="79ed7-111">Zobrazit [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) pro další podrobnosti o tom, co znamená odmítnuté zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="79ed7-111">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ed7-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79ed7-112">See also</span></span>

- [<span data-ttu-id="79ed7-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="79ed7-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="79ed7-114">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="79ed7-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="79ed7-115">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="79ed7-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="79ed7-116">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="79ed7-116">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
- [<span data-ttu-id="79ed7-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="79ed7-117">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkID=99548)
