---
title: Trasa podle textu
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: b8a3f7785d7d59d8ad85d6dddde7fd6a04a12d63
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320714"
---
# <a name="route-by-body"></a><span data-ttu-id="d046f-102">Trasa podle textu</span><span class="sxs-lookup"><span data-stu-id="d046f-102">Route by Body</span></span>
<span data-ttu-id="d046f-103">Tento příklad ukazuje, jak implementovat službu, která přijímá zprávy objekty s žádnou akci SOAP.</span><span class="sxs-lookup"><span data-stu-id="d046f-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="d046f-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="d046f-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="d046f-105">Služba implementuje jediného `Calculate` operace, která přijímá <xref:System.ServiceModel.Channels.Message> požadavku parametr a vrátí <xref:System.ServiceModel.Channels.Message> odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d046f-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="d046f-106">V této ukázce klient je konzolová aplikace (.exe) a služba je hostována ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="d046f-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d046f-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d046f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d046f-108">Ukázce odeslání zprávy na základě obsahu těla.</span><span class="sxs-lookup"><span data-stu-id="d046f-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="d046f-109">Integrované zpráva odeslání mechanismus modelu služby Windows Communication Foundation (WCF) je založen na zprávu akce.</span><span class="sxs-lookup"><span data-stu-id="d046f-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="d046f-110">Existují však mnoho existující webové služby, které definují všechny své operace s akcí = "".</span><span class="sxs-lookup"><span data-stu-id="d046f-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="d046f-111">Není možné vytvářet službě založené na souboru WSDL, který udržuje odeslání žádosti o zprávy založené na informace o akci.</span><span class="sxs-lookup"><span data-stu-id="d046f-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="d046f-112">V této ukázce kontraktu služby, který je založen na WSDL (jazyka WSDL je součástí, která je součástí vzorku. Service.wsdl).</span><span class="sxs-lookup"><span data-stu-id="d046f-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="d046f-113">Kontrakt služby je kalkulačky, podobný tomu použitému v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d046f-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="d046f-114">Ale `[OperationContract]` Určuje `Action=""` pro všechny operace.</span><span class="sxs-lookup"><span data-stu-id="d046f-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="d046f-115">Daný kontrakt služby vyžaduje vlastní chování `DispatchByBodyBehavior` aby byly povolené zprávy k odeslání mezi operacemi.</span><span class="sxs-lookup"><span data-stu-id="d046f-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="d046f-116">Toto chování odeslání inicializuje `DispatchByBodyElementOperationSelector` selektor vlastní operace s tabulkou názvy operací s klíči QName obálky odpovídajících prvků.</span><span class="sxs-lookup"><span data-stu-id="d046f-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> `DispatchByBodyElementOperationSelector` <span data-ttu-id="d046f-117">vypadá v počáteční značce prvního podřízeného obsahu a vybere operace pomocí tabulky už jsme zmínili.</span><span class="sxs-lookup"><span data-stu-id="d046f-117">looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="d046f-118">Klient používá automaticky generovaný z WSDL exportovali pomocí služby proxy [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d046f-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="d046f-119">Vzhledem k tomu, že mají akce všechny operace prázdný nemá žádný vliv na kód klienta, s výjimkou parametry akce v proxy serveru automaticky generovány.</span><span class="sxs-lookup"><span data-stu-id="d046f-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="d046f-120">Klientský kód provede několik výpočtů.</span><span class="sxs-lookup"><span data-stu-id="d046f-120">The client code performs several calculations.</span></span> <span data-ttu-id="d046f-121">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="d046f-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d046f-122">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="d046f-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d046f-123">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="d046f-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d046f-124">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d046f-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d046f-125">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d046f-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d046f-126">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d046f-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d046f-127">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="d046f-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d046f-128">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d046f-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d046f-129">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d046f-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d046f-130">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d046f-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
