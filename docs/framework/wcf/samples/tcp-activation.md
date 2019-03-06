---
title: Aktivace protokolem TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 065c4706d0a52414c4abed85044ce06ad3efe35c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374918"
---
# <a name="tcp-activation"></a><span data-ttu-id="f16aa-102">Aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="f16aa-102">TCP Activation</span></span>

<span data-ttu-id="f16aa-103">Tato ukázka předvádí, který je hostitelem služby, které používá služby aktivační procesů Windows (WAS) k aktivaci služby, která komunikuje přes protokol net.tcp.</span><span class="sxs-lookup"><span data-stu-id="f16aa-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="f16aa-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f16aa-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f16aa-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f16aa-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f16aa-106">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f16aa-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f16aa-107">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f16aa-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f16aa-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f16aa-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f16aa-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f16aa-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="f16aa-110">Ukázka se skládá z programu konzoly klienta (.exe) a služby knihovny (.dll) hostované v pracovním procesu aktivoval WAS.</span><span class="sxs-lookup"><span data-stu-id="f16aa-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="f16aa-111">Činnost klienta je vidět v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="f16aa-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="f16aa-112">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="f16aa-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="f16aa-113">Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (přidat, odečítání, násobení a rozdělit), jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="f16aa-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="f16aa-114">Implementace služby vypočítá a vrátí odpovídající výsledek:</span><span class="sxs-lookup"><span data-stu-id="f16aa-114">The service implementation calculates and returns the appropriate result:</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="f16aa-115">Ukázka používá variantu net.tcp vazby s povoleno sdílení portu TCP a zabezpečení vypnuto.</span><span class="sxs-lookup"><span data-stu-id="f16aa-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="f16aa-116">Pokud chcete použít zabezpečený TCP vazby, změňte režim zabezpečení serveru na požadované nastavení a znovu spusťte Svcutil.exe na straně klienta se vygenerovat soubor aktualizace klienta konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f16aa-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="f16aa-117">Následující příklad ukazuje konfiguraci pro službu:</span><span class="sxs-lookup"><span data-stu-id="f16aa-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="f16aa-118">Jak je znázorněno v následujícím ukázkovém kódu, je nakonfigurovaný koncový bod klienta:</span><span class="sxs-lookup"><span data-stu-id="f16aa-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="f16aa-119">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="f16aa-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f16aa-120">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="f16aa-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f16aa-121">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="f16aa-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f16aa-122">Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="f16aa-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)] <span data-ttu-id="f16aa-123">je vyžadován pro aktivaci WAS.</span><span class="sxs-lookup"><span data-stu-id="f16aa-123">is required for WAS activation.</span></span>

2. <span data-ttu-id="f16aa-124">Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f16aa-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="f16aa-125">Kromě toho je třeba nainstalovat jiným protokolem než HTTP aktivačních komponent WCF:</span><span class="sxs-lookup"><span data-stu-id="f16aa-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="f16aa-126">Z **Start** nabídce zvolte **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="f16aa-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="f16aa-127">Vyberte **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="f16aa-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="f16aa-128">Klikněte na tlačítko **součásti Windows zapnout nebo vypnout**.</span><span class="sxs-lookup"><span data-stu-id="f16aa-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="f16aa-129">Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontrolu **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.</span><span class="sxs-lookup"><span data-stu-id="f16aa-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="f16aa-130">Konfigurace WAS pro podporu Aktivace protokolem TCP.</span><span class="sxs-lookup"><span data-stu-id="f16aa-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="f16aa-131">V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá AddNetTcpSiteBinding.cmd nachází v adresáři ukázkové.</span><span class="sxs-lookup"><span data-stu-id="f16aa-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="f16aa-132">Kvůli podpoře aktivace net.tcp, musíte ji nejdřív svázat výchozí webový server k portu net.tcp.</span><span class="sxs-lookup"><span data-stu-id="f16aa-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="f16aa-133">To lze provést pomocí Appcmd.exe, která se instaluje s sada nástrojů pro správu Internetové informační služby 7.0 (IIS).</span><span class="sxs-lookup"><span data-stu-id="f16aa-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="f16aa-134">Z příkazového řádku na úrovni správce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f16aa-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="f16aa-135">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="f16aa-135">This command is a single line of text.</span></span> <span data-ttu-id="f16aa-136">Tento příkaz přidá vazbu webu net.tcp výchozí webový server naslouchá na portu TCP 808 s libovolný název hostitele.</span><span class="sxs-lookup"><span data-stu-id="f16aa-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="f16aa-137">Přestože všechny aplikace v rámci lokality sdílejí společné vazby net.tcp, každá aplikace můžete povolit podporu net.tcp jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="f16aa-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="f16aa-138">Pokud chcete povolit net.tcp /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku na úrovni správce:</span><span class="sxs-lookup"><span data-stu-id="f16aa-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="f16aa-139">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="f16aa-139">This command is a single line of text.</span></span> <span data-ttu-id="f16aa-140">Tento příkaz umožňuje aplikaci /servicemodelsamples přistupovat pomocí obou `http://localhost/servicemodelsamples` a `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="f16aa-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="f16aa-141">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f16aa-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="f16aa-142">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f16aa-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    <span data-ttu-id="f16aa-143">Odeberte net.tcp vazby webu, kterou jste přidali pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="f16aa-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="f16aa-144">V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá RemoveNetTcpSiteBinding.cmd nachází v adresáři ukázkové.</span><span class="sxs-lookup"><span data-stu-id="f16aa-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="f16aa-145">Odebrání net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku na úrovni správce:</span><span class="sxs-lookup"><span data-stu-id="f16aa-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="f16aa-146">Tento příkaz musí být zadán jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="f16aa-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="f16aa-147">Odeberte vazbu webu net.tcp spuštěním následujícího příkazu z příkazového řádku na úrovni správce:</span><span class="sxs-lookup"><span data-stu-id="f16aa-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="f16aa-148">Tento příkaz musí být zadán v jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="f16aa-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="f16aa-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f16aa-149">See also</span></span>

- [<span data-ttu-id="f16aa-150">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="f16aa-150">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
