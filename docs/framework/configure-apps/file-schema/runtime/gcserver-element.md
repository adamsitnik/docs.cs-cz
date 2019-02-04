---
title: Element <gcServer>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9125ee35b081a1723f379bd3fbdec808d085c675
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674448"
---
# <a name="gcserver-element"></a>\<gcServer> Element
Určuje, zda modul common language runtime spustí uvolnění paměti serveru.  
  
 \<Konfigurace >  
\<modul runtime >  
\<gcServer>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime spustí uvolnění paměti serveru.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nejde spustit uvolňování paměti serveru. Toto nastavení je výchozí.|  
|`true`|Spustí uvolnění paměti serveru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (CLR) podporuje dva typy uvolňování paměti: uvolnění paměti pracovní stanice, která je dostupná na všech systémech, a uvolňování paměti serveru, který je k dispozici v systémech s více procesory. Můžete použít `<gcServer>` elementu k řízení typu CLR uvolňování paměti provede. Použití <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> a určí, zda je povoleno uvolnění paměti serveru.  
  
 Jednoprocesorových počítačích výchozí kolekce uvolnění paměti pracovní stanice by měl být nejrychlejší možnost. Pracovní stanice nebo serveru lze použít pro počítače se dvěma procesory. Uvolnění paměti serveru by měl být nejrychlejší možnost pro více než dva procesory.  
  
 Tento element lze použít pouze v konfiguračním souboru aplikace; je ignorován, pokud je v konfiguračním souboru počítače.  
  
> [!NOTE]
>  V rozhraní .NET Framework 4 a dřívějších verzích souběžné uvolňování paměti není k dispozici při uvolnění paměti serveru je povolená. Počínaje [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], je souběžné uvolňování paměti serveru. Chcete-li použít nesouběžné uvolňování, nastavte `<gcServer>` elementu `true` a [ \<gcConcurrent > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) k `false`.  
  
## <a name="example"></a>Příklad  
 Následující příklad umožňuje uvolňování paměti serveru.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Chcete-li zakázat souběžné uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
