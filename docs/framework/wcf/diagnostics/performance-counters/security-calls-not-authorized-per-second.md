---
title: Počet neautorizovaných volání zabezpečení za sekundu
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 15890506aece94a07d4b97101519007accf3570a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915912"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="53485-102">Počet neautorizovaných volání zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="53485-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="53485-103">Název čítače: Počet neautorizovaných volání zabezpečení za sekundu.</span><span class="sxs-lookup"><span data-stu-id="53485-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="53485-104">Popis</span><span class="sxs-lookup"><span data-stu-id="53485-104">Description</span></span>  
 <span data-ttu-id="53485-105">Počet volání, která se nezdařila autorizace pro tuto operaci za sekundu.</span><span class="sxs-lookup"><span data-stu-id="53485-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="53485-106">Tento čítač se zvyšuje při <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí metoda `false`.</span><span class="sxs-lookup"><span data-stu-id="53485-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="53485-107">Označuje, že příchozí zprávu od platného uživatele a správně chráněný, ale uživatel nemá oprávnění k provádění konkrétních úkolů.</span><span class="sxs-lookup"><span data-stu-id="53485-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="53485-108">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="53485-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="53485-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="53485-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
