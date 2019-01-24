---
title: '&lt;defaultFtpCachePolicy&gt; Element (Network Settings)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: f237831befab627ec603a9000a7cef6184e0ae65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546106"
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a>&lt;defaultFtpCachePolicy&gt; Element (Network Settings)
Popisuje, zda ukládání do mezipaměti serveru FTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.  
  
 \<Konfigurace >  
\<system.net>  
\<requestCaching>  
\<defaultFtpCachePolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`policyLevel`|Určuje FTP zásady ukládání do mezipaměti. Výchozí hodnota je `Default`.|  
  
## <a name="policylevel-attribute"></a>PolicyLevel, který atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`Default`|Vrátí uložený v mezipaměti prostředků, pokud je prostředek čerstvé, délka obsahu je správná, a vypršení platnosti, úpravu a délka obsahu atributy jsou k dispozici.|  
|`BypassCache`|Vrátí prostředek ze serveru.|  
|`CacheOnly`|Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikosti položky.|  
|`CacheIfAvailable`|Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikost položky; v opačném případě zdroj se stáhne ze serveru a je vrátit zpět volajícímu.|  
|`Revalidate`|Vrátí uložený v mezipaměti prostředků, pokud časové razítko v mezipaměti prostředku je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj staženy ze serveru, uložená v mezipaměti a vrátit zpět volajícímu.|  
|`Reload`|Soubory ke stažení prostředku ze serveru, ukládá do mezipaměti a vrátí řízení volajícímu prostředku.|  
|`NoCacheNoStore`|Pokud existuje prostředek v mezipaměti, je odstranit. Zdroj se stáhne ze serveru a je vrátit zpět volajícímu.|  
|`Revalidate`|Splňuje požadavek s použitím uložené v mezipaměti kopie prostředku časové razítko je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj staženy ze serveru, zobrazí volajícímu a uložená v mezipaměti.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit zásady ukládání do mezipaměti FTP `NoCacheNoStore`.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
