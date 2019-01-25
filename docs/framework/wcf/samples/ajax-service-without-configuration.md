---
title: Služba AJAX bez konfigurace
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: f722eac27fadbd772b85a638c3c9171c2783a8b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582183"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="9e00c-102">Služba AJAX bez konfigurace</span><span class="sxs-lookup"><span data-stu-id="9e00c-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="9e00c-103">Tento příklad ukazuje, jak pomocí Windows Communication Foundation (WCF) bez použití jakékoli konfigurace základní technologie ASP.NET asynchronní JavaScript a XML (AJAX) službu (služba, obsahujících pomocí kódu jazyka JavaScript z webového prohlížeče klienta) nastavení.</span><span class="sxs-lookup"><span data-stu-id="9e00c-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="9e00c-104">Služba používá speciální syntaxe v souboru SVC automaticky povolení koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="9e00c-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="9e00c-105">Podpora pro AJAX ve službě WCF je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9e00c-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="9e00c-106">Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [Ajax ukázky](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="9e00c-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e00c-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9e00c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9e00c-108">Tato ukázka staví na AJAX služba využívající HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="9e00c-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="9e00c-109">Jak je popsáno v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázce <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> slouží jako hostitel služby.</span><span class="sxs-lookup"><span data-stu-id="9e00c-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="9e00c-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> ke službě.</span><span class="sxs-lookup"><span data-stu-id="9e00c-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="9e00c-111">Pokud má být provedeno do koncového bodu, je nutné žádné změny konfigurace `<system.ServiceModel>` části je úplně odebrat ze souboru Web.config pro službu.</span><span class="sxs-lookup"><span data-stu-id="9e00c-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="9e00c-112">Soubor Web.config obsahuje některá nastavení technologie ASP.NET, které jsou používány ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="9e00c-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="9e00c-113">V případě, které nebyly tento případ, může odebrat celý soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="9e00c-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e00c-114">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9e00c-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9e00c-115">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9e00c-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9e00c-116">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9e00c-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9e00c-117">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9e00c-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9e00c-118">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9e00c-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9e00c-119">Zajistěte, aby pokyny k instalaci v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9e00c-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9e00c-120">Sestavte řešení ConfigFreeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9e00c-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9e00c-121">Přejděte na `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (neotevírejte ConfigFreeClientPage.aspx v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="9e00c-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e00c-122">Při spuštění této ukázky, ujistěte se, že anonymní ověřování a ověřování Windows nejsou současně povoleno ServiceModelSamples složky ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="9e00c-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="9e00c-123">Pokud je to tento případ, zakažte ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="9e00c-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="9e00c-124">Po spuštění ukázky, povolit ověřování Windows a spusťte "příkaz iisreset".</span><span class="sxs-lookup"><span data-stu-id="9e00c-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e00c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e00c-125">See also</span></span>
- [<span data-ttu-id="9e00c-126">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="9e00c-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
