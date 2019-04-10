---
title: 'Postupy: Výměna zpráv ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: aad4eae870e3ba603c56a28a620fe8bc0e31ceb6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342983"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="00ff9-102">Postupy: Výměna zpráv ve spolehlivých relacích</span><span class="sxs-lookup"><span data-stu-id="00ff9-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="00ff9-103">Toto téma popisuje kroky potřebné k povolení stabilní relace pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="00ff9-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="00ff9-104">Povolit stabilní relace imperativně pomocí kódu nebo deklarativně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="00ff9-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="00ff9-105">Tento postup používá konfiguračních souborů klienta a služby, pokud chcete povolit ve stabilní relaci a stanovit, že zprávy dorazí ve stejném pořadí, ve kterém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="00ff9-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="00ff9-106">Klíčovou součástí tohoto postupu je, že obsahují element konfigurace koncového bodu `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="00ff9-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="00ff9-107">[  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) element konfigurace odkazuje na tento název a povolit tak, že nastavíte spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="00ff9-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="00ff9-108">Zadejte záruky doručení pro spolehlivé relace tak, že nastavíte `ordered` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="00ff9-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="00ff9-109">Pro zdrojovou kopii tohoto příkladu, naleznete v tématu [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="00ff9-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="00ff9-110">Nakonfigurovat službu pomocí WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="00ff9-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="00ff9-111">Definování kontraktu služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="00ff9-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="00ff9-112">Implementace kontraktu služby ve třídě služby.</span><span class="sxs-lookup"><span data-stu-id="00ff9-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="00ff9-113">Všimněte si, že informace o adresu nebo vazby není zadán uvnitř implementace služby.</span><span class="sxs-lookup"><span data-stu-id="00ff9-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="00ff9-114">Nejste nutné napsat kód pro načtení informací adresu nebo vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="00ff9-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="00ff9-115">Vytvoření *Web.config* souboru nakonfigurujte koncový bod `CalculatorService` , která používá <xref:System.ServiceModel.WSHttpBinding> s stabilní relace povolen a seřazené doručování zpráv vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="00ff9-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="00ff9-116">Vytvoření *Service.svc* soubor, který obsahuje řádek:</span><span class="sxs-lookup"><span data-stu-id="00ff9-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="00ff9-117">Místo *Service.svc* souboru ve virtuální adresář Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="00ff9-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="00ff9-118">Konfigurace klienta s WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="00ff9-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="00ff9-119">Použití [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby:</span><span class="sxs-lookup"><span data-stu-id="00ff9-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="00ff9-120">Obsahuje generovaného klienta `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="00ff9-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="00ff9-121">Generovaný klientskou aplikací také obsahuje implementaci `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="00ff9-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="00ff9-122">Všimněte si, že informace o adrese a vazby není zadán kdekoli uvnitř implementace služby.</span><span class="sxs-lookup"><span data-stu-id="00ff9-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="00ff9-123">Nejste nutné napsat kód pro načtení informací adresu nebo vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="00ff9-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="00ff9-124">*Svcutil.exe* také generuje konfiguraci pro klienta, který se používá <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="00ff9-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="00ff9-125">Název konfiguračního souboru *App.config* při používání sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="00ff9-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="00ff9-126">Vytvoření instance `ClientCalculator` v aplikaci a volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="00ff9-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="00ff9-127">Kompilace a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="00ff9-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="00ff9-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="00ff9-128">Example</span></span>

<span data-ttu-id="00ff9-129">Spolehlivé relace několik vazeb poskytovaných systémem podpory ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="00ff9-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="00ff9-130">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="00ff9-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="00ff9-131">Příklad toho, jak vytvořit vlastní vazby, který podporuje spolehlivé relace, naleznete v tématu [jak: Vytvoření vazby vlastního stabilní relaci s HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="00ff9-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00ff9-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00ff9-132">See also</span></span>

- [<span data-ttu-id="00ff9-133">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="00ff9-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
