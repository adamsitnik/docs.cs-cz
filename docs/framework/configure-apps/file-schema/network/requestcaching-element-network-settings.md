---
title: <requestCaching> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: af290e4b9258a08425a15e297ff538502edea916
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164850"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching – > – Element (nastavení sítě)
Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.  
  
 \<Konfigurace >  
\<system.net>  
\<requestCaching>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`isPrivateCache`|Určuje, zda mezipaměti zajišťuje izolaci mezi informace o různé uživatele. Výchozí hodnota je `true`. Tato hodnota by měla být `false` pro aplikace střední vrstvy.|  
|`disableAllCaching`|Určuje, že ukládání do mezipaměti je zakázaná pro všechny odpovědi na webu a nedají se přepsat prostřednictvím kódu programu.|  
|`defaultPolicyLevel`|Jedna z hodnot v <xref:System.Net.Cache.RequestCacheLevel> výčtu. Výchozí hodnota je `BypassCache`.|  
|`unspecifiedMaximumAge`|Určuje výchozí dobu, po jejímž uplynutí obsah označena jako neplatná.|  
  
## <a name="policylevel-attribute"></a>PolicyLevel, který atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|`Default`|Vrátí uložený v mezipaměti prostředků, pokud je prostředek čerstvé, délka obsahu je správná, a vypršení platnosti, úpravu a délka obsahu atributy jsou k dispozici.|  
|`BypassCache`|Vrátí prostředek ze serveru.|  
|`CacheOnly`|Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikosti položky.|  
|`CacheIfAvailable`|Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikost položky; v opačném případě zdroj se stáhne ze serveru a je vrátit zpět volajícímu.|  
|`Revalidate`|Vrátí uložený v mezipaměti prostředků, pokud časové razítko v mezipaměti prostředku je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj se stáhne ze serveru, uloží se do mezipaměti a je vrátit zpět volajícímu.|  
|`Reload`|Soubory ke stažení prostředku ze serveru, ukládá do mezipaměti a vrátí řízení volajícímu prostředku.|  
|`NoCacheNoStore`|Pokud existuje prostředek v mezipaměti, je odstranit. Zdroj se stáhne ze serveru a je vrátit zpět volajícímu.|  
|`Revalidate`|Splňuje požadavek s použitím uložené v mezipaměti kopie prostředku časové razítko je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj se stáhne ze serveru, zobrazí volajícímu a je uložen v mezipaměti,|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|Volitelný element.<br /><br /> Popisuje, zda HTTP, ukládání do mezipaměti je aktivní a popisuje výchozí zásady ukládání do mezipaměti.|  
|[\<defaultFtpCachePolicy> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|Volitelný element.<br /><br /> Popisuje, zda ukládání do mezipaměti serveru FTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat ukládání do mezipaměti.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
