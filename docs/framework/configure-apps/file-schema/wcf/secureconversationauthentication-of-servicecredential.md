---
title: '&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 2c8479c4d8a321c822d49bdc24f359ffad5500e9
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147184"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a>&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;
Určuje nastavení pro služby zabezpečené konverzace.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceCredentials >  
\<secureConversationAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`securityStateEncoderType`|Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> má být použit.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Použijte tento prvek konfigurace pro zadání seznamu známé deklarace typů pro serializaci soubory cookie zabezpečení kontextu Token (SCT), stejně jako kodéru pro kódování a zabezpečit informace soubory cookie. Další informace o SCT najdete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
