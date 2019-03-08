---
title: 'Postupy: Přístup ke službám pomocí duplexního kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 366fd9d6aa220bcbec1ee8fb2a04d1b84755800a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678680"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="ad424-102">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="ad424-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="ad424-103">Jednu funkci Windows Communication Foundation (WCF) je schopnost vytvářet služby, která používá vzor duplexní zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ad424-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="ad424-104">Tento model umožňuje služba ke komunikaci s klientem prostřednictvím zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="ad424-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="ad424-105">Toto téma popisuje kroky k vytvoření klienta WCF v třídě klienta, který implementuje rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ad424-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="ad424-106">Duální vazby poskytuje IP adresu klienta do služby.</span><span class="sxs-lookup"><span data-stu-id="ad424-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="ad424-107">Klient musí použít zabezpečení zajistit, že se připojí jenom ke službám ji vztahy důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ad424-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="ad424-108">Kurz týkající se vytvoření klienta a basic služby WCF, najdete v tématu [kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="ad424-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="ad424-109">Pro přístup k duplexní služby</span><span class="sxs-lookup"><span data-stu-id="ad424-109">To access a duplex service</span></span>

1. <span data-ttu-id="ad424-110">Vytvoření služby, která obsahuje dvě rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ad424-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="ad424-111">První rozhraní je pro službu, druhý zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ad424-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="ad424-112">Další informace o vytvoření duplexní služby najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="ad424-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="ad424-113">Spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="ad424-113">Run the service.</span></span>

3. <span data-ttu-id="ad424-114">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat kontrakty (rozhraní) pro klienta.</span><span class="sxs-lookup"><span data-stu-id="ad424-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="ad424-115">Informace o tom, jak to provést, najdete v tématu [jak: Vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="ad424-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="ad424-116">Implementujte rozhraní zpětného volání ve třídě klienta, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ad424-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="ad424-117">Vytvořit instanci <xref:System.ServiceModel.InstanceContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="ad424-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="ad424-118">Konstruktor vyžaduje instanci třídy klienta.</span><span class="sxs-lookup"><span data-stu-id="ad424-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="ad424-119">Vytvořte instanci klienta WCF pomocí konstruktoru, který se vyžaduje <xref:System.ServiceModel.InstanceContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="ad424-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="ad424-120">Druhý parametr konstruktoru je název koncového bodu v konfiguračním souboru nalezeno.</span><span class="sxs-lookup"><span data-stu-id="ad424-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="ad424-121">Volání metody WCF klienta podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="ad424-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="ad424-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad424-122">Example</span></span>

<span data-ttu-id="ad424-123">Následující příklad kódu ukazuje, jak vytvořit třídu klienta, který přistupuje k duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ad424-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="ad424-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad424-124">See also</span></span>

- [<span data-ttu-id="ad424-125">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="ad424-125">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="ad424-126">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="ad424-126">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="ad424-127">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ad424-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="ad424-128">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="ad424-128">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="ad424-129">Postupy: Používání ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="ad424-129">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
