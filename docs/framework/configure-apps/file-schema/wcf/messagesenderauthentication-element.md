---
title: <messageSenderAuthentication> – element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 804c280bcdb0fecc87f71121b7d95b5fd0268de9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423126"
---
# <a name="messagesenderauthentication-element"></a>\<messageSenderAuthentication > – element
Určuje možnosti ověřování pro odesílatele zpráv peer-to-peer.  
  
 Další informace o programování peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<clientCredentials>  
\<peer>  
\<messageSenderAuthentication>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Typ a sestavení používané pro ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.|  
|`certificateValidationMode`|Určuje jeden ze tří režimů používaných pro ověření pověření. Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.|  
|`revocationMode`|Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL).|  
|`trustedStoreLocation`|Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá při certifikát služby se vyjedná do klienta. Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType Attribute  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Volitelné. Určuje název typu a sestavení a další data použít k vyhledání typu. Minimálně název oboru názvů a typ jsou požadovány. Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Volitelné. Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. Výchozí hodnota je `ChainTrust`. Výchozí hodnota je `ChainTrust`.<br /><br /> Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`. Výchozí hodnota je `Online`.<br /><br /> Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`. Výchozí hodnota je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`. Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`. Výchozí hodnota je `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Určuje pověření pro ověření klienta ke službě partnera.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element musí být nakonfigurované, pokud je zvoleno ověřování zpráv. Pro výstup kanály, každá zpráva je podepsaná pomocí certifikátu poskytnutého [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Všechny zprávy, předtím, než se doručí do aplikace, jsou porovnávána s přihlašovacími údaji zprávy pomocí validátor určené `customCertificateValidatorType` atribut tohoto elementu. Validátor můžete přijmout nebo odmítnout přihlašovací údaje.  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví režim ověřování zpráv odesílatele `PeerOrChainTrust`.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Ověřování zpráv protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Vlastní ověřování protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
