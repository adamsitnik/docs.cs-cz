---
title: '&lt;security&gt; – &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 9e6a0e864dcb83a529a5ac457e2fcffe0435376f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701167"
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="08488-102">&lt;security&gt; – &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="08488-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="08488-103">Definuje možnosti zabezpečení [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="08488-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="08488-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="08488-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="08488-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="08488-105">\<bindings></span></span>  
<span data-ttu-id="08488-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="08488-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="08488-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="08488-107">\<binding></span></span>  
<span data-ttu-id="08488-108">\<security></span><span class="sxs-lookup"><span data-stu-id="08488-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08488-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08488-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08488-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="08488-110">Attributes and Elements</span></span>  
 <span data-ttu-id="08488-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08488-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08488-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="08488-112">Attributes</span></span>  
  
|<span data-ttu-id="08488-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="08488-113">Attribute</span></span>|<span data-ttu-id="08488-114">Popis</span><span class="sxs-lookup"><span data-stu-id="08488-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08488-115">režim</span><span class="sxs-lookup"><span data-stu-id="08488-115">mode</span></span>|<span data-ttu-id="08488-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="08488-116">Optional.</span></span> <span data-ttu-id="08488-117">Určuje typ zabezpečení, který se používá.</span><span class="sxs-lookup"><span data-stu-id="08488-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="08488-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="08488-118">The default is `None`.</span></span> <span data-ttu-id="08488-119">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="08488-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="08488-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="08488-120">mode Attribute</span></span>  
  
|<span data-ttu-id="08488-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="08488-121">Value</span></span>|<span data-ttu-id="08488-122">Popis</span><span class="sxs-lookup"><span data-stu-id="08488-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08488-123">Žádná</span><span class="sxs-lookup"><span data-stu-id="08488-123">None</span></span>|<span data-ttu-id="08488-124">-Zprávy nejsou zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="08488-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="08488-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="08488-125">Transport</span></span>|<span data-ttu-id="08488-126">Zabezpečení je prováděno pomocí přenos protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="08488-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="08488-127">Zprávy protokolu SOAP jsou zabezpečené pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="08488-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="08488-128">Služba je ověřen u klienta pomocí certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="08488-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="08488-129">Klient je ověřený pomocí nebyl typ ClientCredentialType zadán.</span><span class="sxs-lookup"><span data-stu-id="08488-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="08488-130">Zobrazit [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="08488-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="08488-131">Zpráva</span><span class="sxs-lookup"><span data-stu-id="08488-131">Message</span></span>|<span data-ttu-id="08488-132">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="08488-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="08488-133">Ve výchozím nastavení je tělo zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="08488-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="08488-134">Pro tuto vazbu systému vyžaduje, aby certifikát serveru poskytnuta klientovi mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="08488-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="08488-135">Jediné platné `ClientCredentialType` pro tuto vazbu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="08488-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="08488-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="08488-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="08488-137">Zabezpečení přenosu zajišťují integritu a důvěrnost serveru ověřování.</span><span class="sxs-lookup"><span data-stu-id="08488-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="08488-138">Ověření klienta je k dispozici prostřednictvím zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="08488-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="08488-139">Tento režim je důležité, když se uživatel ověřuje pomocí uživatelského jména a hesla a nějaké existující nasazení HTTP pro přenos zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="08488-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="08488-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="08488-140">TransportCredentialOnly</span></span>|<span data-ttu-id="08488-141">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="08488-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="08488-142">Poskytuje ověření klienta založené na protokolu http.</span><span class="sxs-lookup"><span data-stu-id="08488-142">It provides http-based client authentication.</span></span> <span data-ttu-id="08488-143">Tento režim je třeba používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="08488-143">This mode should be used with caution.</span></span> <span data-ttu-id="08488-144">Byste měli použít ve prostředích, kde zabezpečení přenosu se neposkytujeme jiným způsobem (jako je protokol IPSec) a infrastruktura WCF se poskytuje pouze ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="08488-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08488-145">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="08488-145">Child Elements</span></span>  
  
|<span data-ttu-id="08488-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="08488-146">Element</span></span>|<span data-ttu-id="08488-147">Popis</span><span class="sxs-lookup"><span data-stu-id="08488-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08488-148">\<transport></span><span class="sxs-lookup"><span data-stu-id="08488-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="08488-149">Definuje nastavení zabezpečení přenosu pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="08488-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="08488-150">Tento element odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="08488-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="08488-151">\<message></span><span class="sxs-lookup"><span data-stu-id="08488-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="08488-152">Definuje nastavení zabezpečení zpráv pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="08488-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="08488-153">Tento element odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="08488-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08488-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08488-154">Parent Elements</span></span>  
  
|<span data-ttu-id="08488-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="08488-155">Element</span></span>|<span data-ttu-id="08488-156">Popis</span><span class="sxs-lookup"><span data-stu-id="08488-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08488-157">vazba</span><span class="sxs-lookup"><span data-stu-id="08488-157">binding</span></span>|<span data-ttu-id="08488-158">Prvek vazby [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="08488-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08488-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08488-159">Remarks</span></span>  
 <span data-ttu-id="08488-160">Ve výchozím nastavení není zabezpečen zprávu protokolu SOAP a klient není ověřený.</span><span class="sxs-lookup"><span data-stu-id="08488-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="08488-161">Tento prvek umožňuje konfigurovat nastavení dalšího ověření zabezpečení pro `basicHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="08488-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08488-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08488-162">See also</span></span>
- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="08488-163">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="08488-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="08488-164">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="08488-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="08488-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="08488-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="08488-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="08488-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="08488-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="08488-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="08488-168">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="08488-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
