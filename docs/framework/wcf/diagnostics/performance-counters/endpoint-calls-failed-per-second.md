---
title: 'Koncový bod: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 03fbdd83246fa811424f445823f705a3bef5697a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608034"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="cb377-102">Koncový bod: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="cb377-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="cb377-103">Název čítače: Počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="cb377-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cb377-104">Popis</span><span class="sxs-lookup"><span data-stu-id="cb377-104">Description</span></span>  
 <span data-ttu-id="cb377-105">Počet volání, které mají neošetřené výjimky a tento koncový bod přijatých za sekundu.</span><span class="sxs-lookup"><span data-stu-id="cb377-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="cb377-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="cb377-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cb377-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cb377-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="cb377-108">Tento čítač se zvyšuje vždy, když dojde k neošetřené výjimce v tomto koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="cb377-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb377-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb377-109">See also</span></span>
- [<span data-ttu-id="cb377-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="cb377-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
