---
title: '&lt;webproxyscript –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 580fcb17c16c4f5de137b8aa298db68c44867c52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536266"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a>&lt;webproxyscript –&gt; – Element (nastavení sítě)
Konfiguruje vlastnosti souboru, který používá ke zjišťování webové proxy servery.  
  
 \<Konfigurace >  
\<system.net>  
\<settings>  
\<webProxyScript>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`downloadTimeout`|Určuje maximální dobu se stáhnout skript do hodiny, minuty a sekundy. Výchozí hodnota je jedna minuta.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
