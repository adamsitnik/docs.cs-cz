---
title: <security> of <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125785"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="3aaac-102">\<security> of \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="3aaac-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="3aaac-103">Definuje nastavení zabezpečení přenosu pro kanál integrace služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="3aaac-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="3aaac-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3aaac-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3aaac-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3aaac-105">\<bindings></span></span>  
<span data-ttu-id="3aaac-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="3aaac-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="3aaac-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3aaac-107">\<binding></span></span>  
<span data-ttu-id="3aaac-108">\<security></span><span class="sxs-lookup"><span data-stu-id="3aaac-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aaac-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aaac-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3aaac-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3aaac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3aaac-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3aaac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3aaac-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3aaac-112">Attributes</span></span>  
  
|<span data-ttu-id="3aaac-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3aaac-113">Attribute</span></span>|<span data-ttu-id="3aaac-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3aaac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3aaac-115">režim</span><span class="sxs-lookup"><span data-stu-id="3aaac-115">mode</span></span>|<span data-ttu-id="3aaac-116">Určuje typ zabezpečení této kontroly integrity, šifrování a ověřování s kanálem integrace služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="3aaac-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="3aaac-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="3aaac-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3aaac-118">-Žádný: Zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3aaac-118">-   None: This disables security.</span></span><br /><span data-ttu-id="3aaac-119">-Přenos: Ochrana a ověřování se nabízejí Transport.</span><span class="sxs-lookup"><span data-stu-id="3aaac-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="3aaac-120">To platí pro zabezpečení zpráv mezi správci fronty dvě.</span><span class="sxs-lookup"><span data-stu-id="3aaac-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="3aaac-121">Neexistuje žádné zabezpečení nabízené mezi aplikací a správce fronty.</span><span class="sxs-lookup"><span data-stu-id="3aaac-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="3aaac-122">Existující aplikacím služby Msmq jsou funkčně ekvivalentní s tímto typem režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3aaac-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="3aaac-123">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="3aaac-123">The default value is `Transport`.</span></span> <span data-ttu-id="3aaac-124">Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3aaac-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3aaac-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3aaac-125">Child Elements</span></span>  
  
|<span data-ttu-id="3aaac-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="3aaac-126">Element</span></span>|<span data-ttu-id="3aaac-127">Popis</span><span class="sxs-lookup"><span data-stu-id="3aaac-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aaac-128">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="3aaac-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="3aaac-129">Definuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="3aaac-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="3aaac-130">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3aaac-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3aaac-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3aaac-131">Parent Elements</span></span>  
  
|<span data-ttu-id="3aaac-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="3aaac-132">Element</span></span>|<span data-ttu-id="3aaac-133">Popis</span><span class="sxs-lookup"><span data-stu-id="3aaac-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aaac-134">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3aaac-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3aaac-135">Prvek vazby [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3aaac-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3aaac-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3aaac-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="3aaac-137">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="3aaac-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="3aaac-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3aaac-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3aaac-139">Vazby</span><span class="sxs-lookup"><span data-stu-id="3aaac-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3aaac-140">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3aaac-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3aaac-141">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3aaac-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3aaac-142">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3aaac-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="3aaac-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="3aaac-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
