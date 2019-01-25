---
title: '&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 11ce6dcd2f075606cf808992edb99328daec3fba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696411"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="1e628-102">&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="1e628-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="1e628-103">Určuje nastavení pro služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="1e628-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="1e628-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1e628-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e628-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1e628-105">\<behaviors></span></span>  
<span data-ttu-id="1e628-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e628-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1e628-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1e628-107">\<behavior></span></span>  
<span data-ttu-id="1e628-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1e628-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1e628-109">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="1e628-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e628-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e628-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e628-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1e628-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1e628-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1e628-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e628-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1e628-113">Attributes</span></span>  
  
|<span data-ttu-id="1e628-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1e628-114">Attribute</span></span>|<span data-ttu-id="1e628-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1e628-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="1e628-116">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> má být použit.</span><span class="sxs-lookup"><span data-stu-id="1e628-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e628-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1e628-117">Child Elements</span></span>  
 <span data-ttu-id="1e628-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="1e628-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e628-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1e628-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1e628-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1e628-120">Element</span></span>|<span data-ttu-id="1e628-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1e628-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e628-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1e628-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="1e628-123">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="1e628-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e628-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e628-124">Remarks</span></span>  
 <span data-ttu-id="1e628-125">Použijte tento prvek konfigurace pro zadání seznamu známé deklarace typů pro serializaci soubory cookie zabezpečení kontextu Token (SCT), stejně jako kodéru pro kódování a zabezpečit informace soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="1e628-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="1e628-126">Další informace o SCT najdete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="1e628-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e628-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e628-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
