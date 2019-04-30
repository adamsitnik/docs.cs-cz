---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774930"
---
# <a name="499---transferemitted"></a><span data-ttu-id="82ad1-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="82ad1-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="82ad1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="82ad1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82ad1-104">ID</span><span class="sxs-lookup"><span data-stu-id="82ad1-104">ID</span></span>|<span data-ttu-id="82ad1-105">499</span><span class="sxs-lookup"><span data-stu-id="82ad1-105">499</span></span>|  
|<span data-ttu-id="82ad1-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="82ad1-106">Keywords</span></span>|<span data-ttu-id="82ad1-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="82ad1-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="82ad1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="82ad1-108">Level</span></span>|<span data-ttu-id="82ad1-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="82ad1-109">LogAlways</span></span>|  
|<span data-ttu-id="82ad1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="82ad1-110">Channel</span></span>|<span data-ttu-id="82ad1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="82ad1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="82ad1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="82ad1-112">Description</span></span>  
 <span data-ttu-id="82ad1-113">Tato událost je vygenerován místo pořízením událost přenosu.</span><span class="sxs-lookup"><span data-stu-id="82ad1-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="82ad1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="82ad1-114">Message</span></span>  
 <span data-ttu-id="82ad1-115">Byla vyvolána událost přenosu.</span><span class="sxs-lookup"><span data-stu-id="82ad1-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="82ad1-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="82ad1-116">Details</span></span>  
  
|<span data-ttu-id="82ad1-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="82ad1-117">Data Item Name</span></span>|<span data-ttu-id="82ad1-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="82ad1-118">Data Item Type</span></span>|<span data-ttu-id="82ad1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="82ad1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="82ad1-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="82ad1-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="82ad1-121">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="82ad1-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="82ad1-122">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="82ad1-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="82ad1-123">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="82ad1-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="82ad1-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="82ad1-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="82ad1-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="82ad1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
