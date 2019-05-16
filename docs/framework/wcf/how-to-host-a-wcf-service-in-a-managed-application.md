---
title: 'Postupy: Hostování služby WCF ve spravované aplikaci'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: b6d1c9c38e2cc5f1b1b7b5538af0339987563de6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637583"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="a5f7a-102">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="a5f7a-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="a5f7a-103">Hostování služby do spravované aplikace, kód služby do spravované aplikace kódu pro vložení, definovat koncový bod pro službu buď imperativně v kódu, deklarativně pomocí konfigurace nebo pomocí výchozí koncové body a pak vytvořte instance <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="a5f7a-104">Chcete-li začít přijímat zprávy, zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a5f7a-105">Tím se vytvoří a otevře naslouchacího procesu pro službu.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="a5f7a-106">Hostitelská služba tímto způsobem se často označuje jako "hostování na vlastním" protože spravované aplikace pracuje hostování samotný.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="a5f7a-107">Službu zavřete volání <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="a5f7a-108">Služba je rovněž možné hostovat ve spravované službě Windows, v Internetové informační služby (IIS) nebo ve Windows WAS Process Activation Service ().</span><span class="sxs-lookup"><span data-stu-id="a5f7a-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="a5f7a-109">Další informace o možnosti pro služby hostování najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5f7a-109">For more information about hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

<span data-ttu-id="a5f7a-110">Hostování ve spravované aplikaci služby je nejflexibilnější možností, protože vyžaduje minimálně infrastrukturu pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="a5f7a-111">Další informace o hostování služeb ve spravovaných aplikacích najdete v tématu [hostování ve spravované aplikaci](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="a5f7a-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="a5f7a-112">Následující postup ukazuje, jak implementovat v místním prostředí službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="a5f7a-113">Vytvoření služby v místním prostředí</span><span class="sxs-lookup"><span data-stu-id="a5f7a-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="a5f7a-114">Vytvořte novou konzolovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="a5f7a-114">Create a new console application:</span></span>

   1. <span data-ttu-id="a5f7a-115">Otevřít Visual Studio a vyberte **nový** > **projektu** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="a5f7a-116">V **nainstalované šablony** seznamu vyberte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="a5f7a-117">Vyberte **konzolovou aplikaci** šablony.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-117">Select the **Console App** template.</span></span> <span data-ttu-id="a5f7a-118">Typ `SelfHost` v **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="a5f7a-119">Klikněte pravým tlačítkem na **SelfHost** v **Průzkumníka řešení** a vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="a5f7a-120">Vyberte **System.ServiceModel** z **.NET** kartě a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a5f7a-121">Pokud **Průzkumníka řešení** okno není viditelný, vyberte **Průzkumníka řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="a5f7a-122">Dvakrát klikněte na panel **Program.cs** nebo **Module1.vb** v **Průzkumníka řešení** a otevře se v okně kódu, pokud ještě není otevřený.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="a5f7a-123">Na začátek souboru přidejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="a5f7a-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="a5f7a-124">Definování a implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-124">Define and implement a service contract.</span></span> <span data-ttu-id="a5f7a-125">Tento příklad definuje `HelloWorldService` , který vrací zprávy na základě zadání ke službě.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="a5f7a-126">Další informace o tom, jak definovat a implementovat rozhraní služby najdete v tématu [jak: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) a [jak: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a5f7a-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="a5f7a-127">V horní části `Main` metody vytvoření instance <xref:System.Uri> třída s atributem základní adresu pro službu.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="a5f7a-128">Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy, prochází <xref:System.Type> , které představuje typ služby a základní adresu identifikátoru URI (Uniform Resource) k <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="a5f7a-129">Povolit publikování metadat a následně zavolat <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost> k inicializaci služby a připravit ji pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="a5f7a-130">Tento příklad používá výchozí koncové body a konfigurační soubor je požadovaná pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="a5f7a-131">Pokud jsou nakonfigurované žádné koncové body, modul runtime vytvoří jeden koncový bod pro každou základní adresu pro každou smlouvu službou implementována.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="a5f7a-132">Další informace o výchozí koncové body, naleznete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5f7a-132">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="a5f7a-133">Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení řešení.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="a5f7a-134">Testování služby</span><span class="sxs-lookup"><span data-stu-id="a5f7a-134">Test the service</span></span>

1. <span data-ttu-id="a5f7a-135">Stisknutím klávesy **Ctrl**+**F5** ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="a5f7a-136">Otevřít **testovací klient WCF**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a5f7a-137">Chcete-li otevřít **testovací klient WCF**, otevřete příkazový řádek pro vývojáře pro sadu Visual Studio a spusťte **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="a5f7a-138">Vyberte **přidat službu** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="a5f7a-139">Typ `http://localhost:8080/hello` do pole adresy a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a5f7a-140">Ujistěte se, že je služba spuštěná, jinak se tento krok nezdaří.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="a5f7a-141">Pokud jste změnili základní adresa v kódu, použijte upravené základní adresy v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="a5f7a-142">Dvakrát klikněte na panel **SayHello** pod **Moje projekty služeb** uzlu.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="a5f7a-143">Zadejte svoje jméno do **hodnotu** sloupec **požádat o** seznamu a klikněte na tlačítko **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="a5f7a-144">Zobrazí se zpráva s odpovědí v **odpovědi** seznamu.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="a5f7a-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5f7a-145">Example</span></span>

<span data-ttu-id="a5f7a-146">Následující příklad vytvoří <xref:System.ServiceModel.ServiceHost> objekt hostitele služby typu `HelloWorldService`a pak zavolá <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a5f7a-147">Základní adresa jsou uvedené v kódu, je povoleno publikování metadat a používají výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="a5f7a-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a5f7a-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5f7a-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="a5f7a-149">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="a5f7a-149">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="a5f7a-150">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="a5f7a-150">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="a5f7a-151">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="a5f7a-151">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="a5f7a-152">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="a5f7a-152">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="a5f7a-153">Postupy: Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="a5f7a-153">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="a5f7a-154">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="a5f7a-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="a5f7a-155">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a5f7a-155">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a5f7a-156">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="a5f7a-156">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
