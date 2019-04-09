---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: e39458e7e0bac15429ad3d34c4fbba0f55d254f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166988"
---
# <a name="secureconversationbootstrap"></a>\<secureConversationBootstrap>
Určuje výchozí hodnoty pro inicializaci služby zabezpečené konverzace.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<security>  
\<secureConversationBootstrap>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
                             authenticationMode="AuthenticationMode"
                             defaultAlgorithmSuite="SecurityAlgorithmSuite"
                             includeTimestamp="Boolean"
                             requireDerivedKeys="Boolean"
                             keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
                             messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
                             messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
                             requireDerivedKeys="Boolean"
                             requireSecurityContextCancellation="Boolean"
                             requireSignatureConfirmation="Boolean"
                             securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
                             includeTimestamp="Boolean" />
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|Volitelné. Logická hodnota určující, pokud pro odpověď možné použít serializovaný token. Výchozí hodnota je `false`. Při použití duální vazby, výchozí nastavení `true` ignorují se jakékoli nastavení provedli.|  
|`authenticationMode`|Určuje režim ověřování zpráv SOAP mezi iniciátorem a příjemce.<br /><br /> Výchozí nastavení je sspiNegotiated.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Sada algoritmů zabezpečení definuje z různých algoritmy například převodu do kanonického tvaru, Digest, KeyWrap, podpisu, Encryption a keyderivation. Každá sada algoritmů zabezpečení definuje hodnoty pro tyto různé parametry. Zabezpečení na základě zpráv je dosaženo pomocí těchto algoritmů.<br /><br /> Tento atribut se používá při práci s jinou platformu, která požádá o pro sadu algoritmů, které jsou jiné než výchozí. Měli byste vědět silné a slabé stránky relevantní algoritmů při provádění změn pro toto nastavení. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Výchozí hodnota je `Basic256`.|  
|`includeTimestamp`|Logická hodnota určující, zda jsou časová razítka zahrnuta v každé zprávě. Výchozí hodnota je `true`.|  
|`keyEntropyMode`|Určuje způsob, že se vypočítávají klíčů pro zabezpečení zpráv. Klíče může být založen na klienta materiál klíče, jenom na klíče materiál služby pouze nebo kombinaci obojího. Platné hodnoty jsou:<br /><br /> -ClientEntropy: Klíč relace vychází vypnutí klient klíče k dispozici.<br />-ServerEntropy: Klíč relace je založená mimo službu poskytovanou materiál klíče.<br />-CombinedEntropy: Klíč relace založeného na klienta a služby k dispozici šifrovací klíče.<br /><br /> Výchozí hodnota je CombinedEntropy.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Nastaví pořadí, ve zpráv, které jsou použity algoritmy zabezpečení na úrovni zprávy. Platné hodnoty patří:<br /><br /> -SignBeforeEncrypt: Nejprve se přihlaste a pak šifrování.<br />-SignBeforeEncryptAndEncryptSignature: Podepisování, šifrování a šifrování podpis.<br />-EncryptBeforeSign: Šifrování nejprve, pak přihlašování.<br /><br /> SignBeforeEncryptAndEncryptSignature je výchozí hodnota při používání vzájemnými certifikáty s WS-Security 1.1.  SignBeforeEncrypt je výchozí hodnota se 1.0 WS-Security.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Nastaví verzi WS-Security, který se používá. Platné hodnoty patří:<br /><br /> -WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> Výchozí hodnota je WSSecurityXXX2005. Tento atribut je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Logická hodnota určující, zda mohou být klíče odvozeny z původního ověřovacího klíče. Výchozí hodnota je `true`.|  
|`requireSecurityContextCancellation`|Logická hodnota, která určuje, zda by měl kontext zabezpečení zrušen a byla ukončena, když se už nevyžaduje. Výchozí hodnota je `true`.|  
|`requireSignatureConfirmation`|Logická hodnota určující, zda je povoleno potvrzení podpisu WS-Security. Pokud je nastavena na `true`, podpisy zpráv potvrdí straně odpovídajícího. Výchozí hodnota je `false`.<br /><br /> Potvrzení podpisu se používá pro potvrzení, že je služba reagovat v úplné povědomí o požadavek.|  
|`securityHeaderLayout`|Určuje pořadí prvků v záhlaví zabezpečení. Platné hodnoty jsou:<br /><br /> -Strict. Položky jsou přidány do záhlaví zabezpečení podle obecné zásady "deklarovat před použitím".<br />-Lax. Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, která potvrzuje WSS: Zabezpečení zpráv SOAP.<br />-LaxWithTimestampFirst. Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, která potvrzuje WSS: Zabezpečení zpráv SOAP, s tím rozdílem, že první prvek v záhlaví zabezpečení musí být prvek wsse:Timestamp.<br />-LaxWithTimestampLast. Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, která potvrzuje WSS: Zabezpečení zpráv SOAP, s tím rozdílem, že po posledním prvku v záhlaví zabezpečení musí být prvek wsse:Timestamp.<br /><br /> Výchozí hodnota je Strict.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Určuje aktuální vydaný token. Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Určuje nastavení zabezpečení místního klienta pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Určuje nastavení zabezpečení místní služby pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti zabezpečení pro vlastní vazbu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
