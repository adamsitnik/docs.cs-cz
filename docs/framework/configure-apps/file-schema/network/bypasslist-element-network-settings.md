---
title: <bypasslist> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 1dda43be8c0e0c94bdf7b57b67aa4d403b547f97
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699545"
---
# <a name="bypasslist-element-network-settings"></a>@no__t – element > 0bypasslist (nastavení sítě)
Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<bypasslist >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[add](add-element-for-bypasslist-network-settings.md)|Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.|  
|[jejich](clear-element-for-bypasslist-network-settings.md)|Vymaže seznam obcházení.|  
|[remove](remove-element-for-bypasslist-network-settings.md)|Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="remarks"></a>Poznámky  
 Seznam pro obejití obsahuje regulární výrazy, které popisují identifikátory URI, které <xref:System.Net.WebRequest> instancí přímo, nikoli prostřednictvím proxy server.  
  
 Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění. Regulární výraz "[a-z] + @no__t -0.contoso\\.com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com. Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] + @no__t -0.contoso\\.com $".  
  
 Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá dvě adresy do seznamu pro obejití. První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresy začínají na 192,168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
