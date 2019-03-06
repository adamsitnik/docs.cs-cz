---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 9728f3caee4dba367e4fc4a3e68213b1055cc3d1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362952"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.  
  
 \<system.identityModel.services>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádná  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> z modulů HTTP (SAM).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
 Žádná  
  
## <a name="remarks"></a>Poznámky  
 Přidat `<system.identityModel.services>` části do konfiguračního souboru aplikace k poskytování nastavení SAM a WSFAM.  
  
> [!IMPORTANT]
>  Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity ve vašem kódu, deklarace identity Správce autorizací (<xref:System.Security.Claims.ClaimsAuthorizationManager>) a zásad, který se používá pro autorizační rozhodnutí, které jsou konfigurovány pomocí `<identityConfiguration>` element, který je implicitně nebo explicitně odkazovat z `<federationConfiguration>` elementu v této části. Další informace najdete v tématu **poznámky** pod [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.  
  
 `<system.identityModel.services>` Části je reprezentována <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> třídy. Kolekce podřízených `<federationConfiguration>` prvky nakonfigurovali v sekci je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> třídy.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak přidat `<system.identityModel.services>` části ke konfiguračnímu souboru. Musíte je napřed přidat části deklarace pro obě `<system.identityModel.services>` oddílu a `<system.identityModel>` oddíly. (Po přidání `<system.identityModel.services>` oddílu, měli byste také přidat deklaraci `<system.identityModel>` části a ujistěte se, že výchozí `<identityConfiguration>` část lze vytvořit modul runtime, v případě potřeby.) Po přidání deklarace části můžete nakonfigurovat v nastavení federovaného ověřování `<system.identityModel.services>` elementu.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"   
        issuer="http://localhost:15839/wsFederationSTS/Issue"   
        realm="http://localhost:50969/" reply="http://localhost:50969/"   
        requireHttps="false"   
        signOutReply="http://localhost:50969/SignedOutPage.html"   
        signOutQueryString="Param1=value2&Param2=value2"   
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
