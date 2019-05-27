---
title: <security> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 788d49239b8b9161a35705295705e6d42eff7837
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052155"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="56693-102">\<security> of \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="56693-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="56693-103">Určuje koncový bod nakonfigurovaný s požadavky na zabezpečení [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="56693-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md).</span></span>  
  
 <span data-ttu-id="56693-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56693-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="56693-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="56693-105">\<bindings></span></span>  
<span data-ttu-id="56693-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="56693-106">\<webHttpBinding></span></span>  
<span data-ttu-id="56693-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="56693-107">\<binding></span></span>  
<span data-ttu-id="56693-108">\<security></span><span class="sxs-lookup"><span data-stu-id="56693-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56693-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56693-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56693-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="56693-110">Attributes and Elements</span></span>  
 <span data-ttu-id="56693-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="56693-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56693-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="56693-112">Attributes</span></span>  
  
|<span data-ttu-id="56693-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="56693-113">Attribute</span></span>|<span data-ttu-id="56693-114">Popis</span><span class="sxs-lookup"><span data-stu-id="56693-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56693-115">režim</span><span class="sxs-lookup"><span data-stu-id="56693-115">mode</span></span>|<span data-ttu-id="56693-116">Určuje, zda zabezpečení transportní vrstvy nebo žádné zabezpečení používá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="56693-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="56693-117">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="56693-117">The default is `None`.</span></span> <span data-ttu-id="56693-118">Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="56693-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="56693-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="56693-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="56693-120">Value</span><span class="sxs-lookup"><span data-stu-id="56693-120">Value</span></span>|<span data-ttu-id="56693-121">Popis</span><span class="sxs-lookup"><span data-stu-id="56693-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56693-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="56693-122">None</span></span>|<span data-ttu-id="56693-123">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="56693-123">Security is disabled.</span></span>|  
|<span data-ttu-id="56693-124">Přenos</span><span class="sxs-lookup"><span data-stu-id="56693-124">Transport</span></span>|<span data-ttu-id="56693-125">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="56693-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="56693-126">Služba je potřeba nakonfigurovat s využitím certifikátů SSL.</span><span class="sxs-lookup"><span data-stu-id="56693-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="56693-127">Zprávu je zcela zabezpečené pomocí protokolu HTTPS a služba je ověřený pomocí klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="56693-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="56693-128">Ověření klienta je řízen pomocí `ClientCredentialType` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="56693-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="56693-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="56693-129">TransportCredentialOnly</span></span>|<span data-ttu-id="56693-130">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="56693-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="56693-131">Poskytuje ověření klienta založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="56693-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="56693-132">Tento režim je třeba používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="56693-132">This mode should be used with caution.</span></span> <span data-ttu-id="56693-133">Byste měli použít ve prostředích, kde zabezpečení přenosu se neposkytujeme jiným způsobem (jako je protokol IPSec) a infrastruktura WCF se poskytuje pouze ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="56693-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56693-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="56693-134">Child Elements</span></span>  
  
|<span data-ttu-id="56693-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="56693-135">Element</span></span>|<span data-ttu-id="56693-136">Popis</span><span class="sxs-lookup"><span data-stu-id="56693-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56693-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="56693-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="56693-138">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="56693-138">Defines the transport security settings.</span></span> <span data-ttu-id="56693-139">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="56693-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56693-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="56693-140">Parent Elements</span></span>  
  
|<span data-ttu-id="56693-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="56693-141">Element</span></span>|<span data-ttu-id="56693-142">Popis</span><span class="sxs-lookup"><span data-stu-id="56693-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56693-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="56693-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="56693-144">Prvek vazby, který se používá ke konfiguraci koncových bodů pro Windows Communication Foundation (WCF) Web services tuto odpověď na požadavky HTTP namísto zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="56693-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56693-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56693-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="56693-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="56693-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="56693-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="56693-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="56693-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="56693-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="56693-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="56693-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="56693-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="56693-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="56693-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="56693-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="56693-152">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="56693-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
