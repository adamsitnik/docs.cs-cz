---
title: <issuer> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 411fd1addb41822043d72de1edffee9f8733bc08
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256638"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="c73d3-102">\<Issuer > z \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="c73d3-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="c73d3-103">Určuje Token služba zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c73d3-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="c73d3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c73d3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c73d3-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="c73d3-105">\<bindings></span></span>  
<span data-ttu-id="c73d3-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c73d3-106">\<customBinding></span></span>  
<span data-ttu-id="c73d3-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="c73d3-107">\<binding></span></span>  
<span data-ttu-id="c73d3-108">\<security></span><span class="sxs-lookup"><span data-stu-id="c73d3-108">\<security></span></span>  
<span data-ttu-id="c73d3-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="c73d3-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="c73d3-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="c73d3-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c73d3-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c73d3-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c73d3-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c73d3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c73d3-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c73d3-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c73d3-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="c73d3-114">Attributes</span></span>  
  
|<span data-ttu-id="c73d3-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="c73d3-115">Attribute</span></span>|<span data-ttu-id="c73d3-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c73d3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c73d3-117">adresa</span><span class="sxs-lookup"><span data-stu-id="c73d3-117">address</span></span>|<span data-ttu-id="c73d3-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c73d3-118">Required string.</span></span> <span data-ttu-id="c73d3-119">Adresa URL služby STS.</span><span class="sxs-lookup"><span data-stu-id="c73d3-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c73d3-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c73d3-120">Child Elements</span></span>  
  
|<span data-ttu-id="c73d3-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="c73d3-121">Element</span></span>|<span data-ttu-id="c73d3-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c73d3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c73d3-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="c73d3-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="c73d3-124">Kolekce záhlaví adres pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="c73d3-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="c73d3-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="c73d3-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c73d3-126">Při použití vydaný token, určuje nastavení, které povoluje klient k ověření tohoto serveru.</span><span class="sxs-lookup"><span data-stu-id="c73d3-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c73d3-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c73d3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c73d3-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="c73d3-128">Element</span></span>|<span data-ttu-id="c73d3-129">Popis</span><span class="sxs-lookup"><span data-stu-id="c73d3-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c73d3-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="c73d3-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="c73d3-131">Určuje aktuální vydaný token.</span><span class="sxs-lookup"><span data-stu-id="c73d3-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c73d3-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c73d3-132">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c73d3-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="c73d3-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c73d3-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="c73d3-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c73d3-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="c73d3-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c73d3-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="c73d3-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c73d3-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="c73d3-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c73d3-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="c73d3-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c73d3-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c73d3-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c73d3-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c73d3-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="c73d3-141">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c73d3-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c73d3-142">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="c73d3-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
