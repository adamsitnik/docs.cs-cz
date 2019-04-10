---
title: Vytváření instancí
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 2cc3c54563b261d49264314f7306193accbe4040
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311432"
---
# <a name="instancing"></a><span data-ttu-id="cbe0e-102">Vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="cbe0e-102">Instancing</span></span>
<span data-ttu-id="cbe0e-103">Instancing ukázce vytvoření instance nastavení chování, které řídí, jak se vytvářejí instance třídy služby v reakci na požadavky klientů.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="cbe0e-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="cbe0e-105">Tato ukázka definuje kontrakt nové `ICalculatorInstance`, který dědí z `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="cbe0e-106">Kontrakt určený `ICalculatorInstance` poskytuje tři další operace, kontroly stavu instance služby.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="cbe0e-107">Změnou nastavení vytvoření instance můžete sledovat změny v chování pomocí klienta.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="cbe0e-108">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="cbe0e-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbe0e-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cbe0e-110">K dispozici jsou následující režimy vytvoření instance:</span><span class="sxs-lookup"><span data-stu-id="cbe0e-110">The following instancing modes are available:</span></span>  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall><span data-ttu-id="cbe0e-111">: Pro každý požadavek klienta je vytvořena nová instance služby.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-111">: A new service instance is created for each client request.</span></span>  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession><span data-ttu-id="cbe0e-112">: Novou instanci je vytvořena pro každou novou relaci klienta a Udržovat dobu trvání relace (vyžaduje vazbu, která podporuje relace).</span><span class="sxs-lookup"><span data-stu-id="cbe0e-112">: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single><span data-ttu-id="cbe0e-113">: Jednu instanci třídy služby zpracuje všechny žádosti klienta po dobu životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-113">: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="cbe0e-114">Určuje chování při vytvoření instance s využitím třídu služby `[ServiceBehavior(InstanceContextMode=<setting>)]` atributu, jak je znázorněno v ukázce kódu, který následuje.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="cbe0e-115">Změnou řádků jsou označené jako komentář, můžete sledovat chování oba režimy instance.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="cbe0e-116">Nezapomeňte znovu sestavit službě po změně vytvoření instance režimu.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="cbe0e-117">Nejsou žádná nastavení týkající se vytváření instancí k určení na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="cbe0e-118">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="cbe0e-119">Zobrazí se režim instancí služby pod kterým je spuštěný.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="cbe0e-120">Po každé operaci se zobrazí počet instancí ID a operace tak, aby odrážely chování vytvoření instance režimu.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="cbe0e-121">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cbe0e-122">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="cbe0e-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cbe0e-123">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbe0e-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cbe0e-124">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbe0e-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cbe0e-125">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbe0e-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbe0e-126">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cbe0e-127">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="cbe0e-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cbe0e-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cbe0e-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
