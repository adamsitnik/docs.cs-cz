---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 1711909ada4756dd2723f62160eef0ad12c03174
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333220"
---
# <a name="local-channel"></a><span data-ttu-id="00a25-102">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="00a25-102">Local Channel</span></span>
<span data-ttu-id="00a25-103">Místní kanál je přenosový kanál Windows Communication Foundation (WCF), který se používá ke komunikaci v rámci stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="00a25-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="00a25-104">To je užitečné pro scénáře, kdy klient a služba běží ve stejné doméně aplikace a musí se jim vyhnout nároky na typické kanál zásobníku WCF (serializaci a deserializaci zpráv).</span><span class="sxs-lookup"><span data-stu-id="00a25-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="00a25-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="00a25-105">Demonstrates</span></span>  
 <span data-ttu-id="00a25-106">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="00a25-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="00a25-107">Diskuse</span><span class="sxs-lookup"><span data-stu-id="00a25-107">Discussion</span></span>  
 <span data-ttu-id="00a25-108">Ukázkový soubor obsahuje dva soubory projektu:</span><span class="sxs-lookup"><span data-stu-id="00a25-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="00a25-109">**LocalChannel**: Programové reprezentace místního kanálu v rámci aktuální domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="00a25-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="00a25-110">V tomto projektu odesílání komponenty umístí zprávu do fronty v paměti a přijímající součást zrušení fronty zprávy ji přijmout.</span><span class="sxs-lookup"><span data-stu-id="00a25-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="00a25-111">**ClientAndService**: Tento projekt hostuje službu v konzolové aplikaci a pak spustí klienta k volání služby z v rámci stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="00a25-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="00a25-112">Místní kanál návrhu přeskočí zásobníku kanálu a zvýšit rychlost procesu serializace.</span><span class="sxs-lookup"><span data-stu-id="00a25-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="00a25-113">Místní přenosový kanál se implementuje pomocí fronty k přenosu volání služby z klienta do služby a k vrácení hodnoty zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="00a25-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="00a25-114">Místo serializaci parametrů a vrácených hodnot, ukázka zkopíruje objekty.</span><span class="sxs-lookup"><span data-stu-id="00a25-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00a25-115">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="00a25-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="00a25-116">Sestavte a spusťte LocalChannel řešení.</span><span class="sxs-lookup"><span data-stu-id="00a25-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="00a25-117">Hostitel služby je spuštěn a klient zavolá službu pomocí místního kanálu.</span><span class="sxs-lookup"><span data-stu-id="00a25-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="00a25-118">Chcete-li zobrazit výsledky volání služby, zobrazí se okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="00a25-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00a25-119">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="00a25-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00a25-120">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="00a25-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="00a25-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="00a25-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00a25-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="00a25-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
