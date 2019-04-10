---
title: Uspořádané zpracování zpráv v režimu jedné souběžnosti
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: 785c2953e57eaf967209b0d9e52ab85a3a99c450
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229716"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="a7608-102">Uspořádané zpracování zpráv v režimu jedné souběžnosti</span><span class="sxs-lookup"><span data-stu-id="a7608-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="a7608-103">WCF neposkytuje žádnou záruku o pořadí, ve kterém se zprávy zpracovávají, pokud je základní kanál s relacemi.</span><span class="sxs-lookup"><span data-stu-id="a7608-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="a7608-104">Například službu WCF používající MsmqInputChannel, který není kanál s relacemi, nepůjde zpracovat zprávy v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a7608-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="a7608-105">Existují některé okolnosti, kdy může vývojář má v pořadí zpracování chování ale nebudete chtít použít relace.</span><span class="sxs-lookup"><span data-stu-id="a7608-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="a7608-106">Toto téma popisuje, jak konfigurovat toto chování, pokud služba běží v režimu jedné souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="a7608-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="a7608-107">Zpracování zpráv v pořadí</span><span class="sxs-lookup"><span data-stu-id="a7608-107">In-order Message Processing</span></span>  
 <span data-ttu-id="a7608-108">Volá se nový atribut <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> byl přidán do <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a7608-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="a7608-109">Když <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> je nastavena na hodnotu true a <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavena na <xref:System.ServiceModel.ConcurrencyMode.Single> zprávy odeslané do služby se zpracovávají v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a7608-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="a7608-110">Následující fragment kódu ukazuje, jak nastavit tyto atributy.</span><span class="sxs-lookup"><span data-stu-id="a7608-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="a7608-111">Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavena na jakoukoli jinou hodnotu <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a7608-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7608-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7608-112">See also</span></span>

- [<span data-ttu-id="a7608-113">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="a7608-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="a7608-114">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="a7608-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
