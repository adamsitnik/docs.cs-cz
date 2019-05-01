---
title: Zabezpečení zpráv s anonymním klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 613b85e18109faa2a4386090e91aaddcfd8e0b68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038581"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="cdd62-102">Zabezpečení zpráv s anonymním klientem</span><span class="sxs-lookup"><span data-stu-id="cdd62-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="cdd62-103">Následující scénář ukazuje klienta a služby zabezpečuje zabezpečení zpráv Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cdd62-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="cdd62-104">Cílem návrhu je použijte zabezpečení zpráv, nikoli zabezpečení přenosu, tak, aby v budoucnu může podporovat modelu podrobnější nezaložené na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="cdd62-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="cdd62-105">Další informace o použití bohaté deklarací identity pro autorizaci najdete v tématu [správa deklarací identity a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="cdd62-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="cdd62-106">Ukázková aplikace, najdete v části [zprávu zabezpečení anonymní](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="cdd62-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="cdd62-107">![Zabezpečení pomocí anonymního klienta zpráv](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="cdd62-107">![Message security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="cdd62-108">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cdd62-108">Characteristic</span></span>|<span data-ttu-id="cdd62-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cdd62-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="cdd62-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cdd62-110">Security Mode</span></span>|<span data-ttu-id="cdd62-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="cdd62-111">Message</span></span>|
|<span data-ttu-id="cdd62-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="cdd62-112">Interoperability</span></span>|<span data-ttu-id="cdd62-113">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="cdd62-113">WCF only</span></span>|
|<span data-ttu-id="cdd62-114">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="cdd62-114">Authentication (Server)</span></span>|<span data-ttu-id="cdd62-115">Počáteční vyjednávání vyžaduje ověřování serveru, ale ne ověření klienta</span><span class="sxs-lookup"><span data-stu-id="cdd62-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="cdd62-116">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="cdd62-116">Authentication (Client)</span></span>|<span data-ttu-id="cdd62-117">Žádný</span><span class="sxs-lookup"><span data-stu-id="cdd62-117">None</span></span>|
|<span data-ttu-id="cdd62-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="cdd62-118">Integrity</span></span>|<span data-ttu-id="cdd62-119">Ano, pomocí sdíleného bezpečnostní kontext</span><span class="sxs-lookup"><span data-stu-id="cdd62-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="cdd62-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="cdd62-120">Confidentiality</span></span>|<span data-ttu-id="cdd62-121">Ano, pomocí sdíleného bezpečnostní kontext</span><span class="sxs-lookup"><span data-stu-id="cdd62-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="cdd62-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="cdd62-122">Transport</span></span>|<span data-ttu-id="cdd62-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="cdd62-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="cdd62-124">Služba</span><span class="sxs-lookup"><span data-stu-id="cdd62-124">Service</span></span>

<span data-ttu-id="cdd62-125">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="cdd62-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cdd62-126">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="cdd62-126">Do one of the following:</span></span>

- <span data-ttu-id="cdd62-127">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cdd62-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="cdd62-128">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="cdd62-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="cdd62-129">Kód</span><span class="sxs-lookup"><span data-stu-id="cdd62-129">Code</span></span>

<span data-ttu-id="cdd62-130">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="cdd62-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="cdd62-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="cdd62-131">Configuration</span></span>

<span data-ttu-id="cdd62-132">Následující konfigurace je možné použít místo kódu.</span><span class="sxs-lookup"><span data-stu-id="cdd62-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="cdd62-133">Prvek chování služby slouží k určení certifikát, který se používá k ověření služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="cdd62-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="cdd62-134">Service element musí být specifikován pomocí chování `behaviorConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="cdd62-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="cdd62-135">Element vazby Určuje, jestli je typ přihlašovacích údajů klienta `None`, umožňuje anonymní klientům používání služby.</span><span class="sxs-lookup"><span data-stu-id="cdd62-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="cdd62-136">Klient</span><span class="sxs-lookup"><span data-stu-id="cdd62-136">Client</span></span>

<span data-ttu-id="cdd62-137">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="cdd62-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cdd62-138">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="cdd62-138">Do one of the following:</span></span>

- <span data-ttu-id="cdd62-139">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="cdd62-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="cdd62-140">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="cdd62-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="cdd62-141">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cdd62-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="cdd62-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="cdd62-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="cdd62-143">Kód</span><span class="sxs-lookup"><span data-stu-id="cdd62-143">Code</span></span>

<span data-ttu-id="cdd62-144">Následující kód vytvoří instanci klienta.</span><span class="sxs-lookup"><span data-stu-id="cdd62-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="cdd62-145">Vazba používá režim zabezpečení zpráv a typu pověření klienta je nastavena na hodnotu none.</span><span class="sxs-lookup"><span data-stu-id="cdd62-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="cdd62-146">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="cdd62-146">Configuration</span></span>

<span data-ttu-id="cdd62-147">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="cdd62-147">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="cdd62-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdd62-148">See also</span></span>

- [<span data-ttu-id="cdd62-149">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cdd62-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="cdd62-150">Zabezpečení distribuované aplikace</span><span class="sxs-lookup"><span data-stu-id="cdd62-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="cdd62-151">Zabezpečení zpráv s anonymní metodou</span><span class="sxs-lookup"><span data-stu-id="cdd62-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)
- [<span data-ttu-id="cdd62-152">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="cdd62-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="cdd62-153">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="cdd62-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
