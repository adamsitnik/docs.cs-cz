---
title: <clear> – Element pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 97b18f9d6baa618b0f535955b232e2119c758b11
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124888"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<Vymazat > – Element pro \<naslouchacích procesů > pro \<trasování >
Vymaže `Listeners` kolekce pro trasování.  
  
 \<Konfigurace >  
\<system.diagnostics>  
\<trasování >  
\<naslouchací procesy >  
\<clear>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`trace`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.|  
|`listeners`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat zprávy. Posluchači přímý výstup trasování příslušný cíli.|  
  
## <a name="remarks"></a>Poznámky  
 `<clear>` Element odebere všechny moduly pro naslouchání z `Listeners` kolekce pro trasování. Můžete použít `<clear>` prvek před použitím `<add>` element je potřeba mít jistotu, nejsou žádné aktivní naslouchací procesy v kolekci.  
  
 Můžete vymazat `Listeners` kolekce programově zavoláním <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metodu <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnosti (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
> [!NOTE]
>  `<clear>` Odebere element <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce, změna chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody. Volání `Assert` nebo `Fail` metoda je normálně ve výsledku zobrazení okna se zprávou. Však se nezobrazí okno se zprávou, pokud <xref:System.Diagnostics.DefaultTraceListener> se nepoužívá `Listeners` kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<clear>` prvek před použitím `<add>` prvek a přidat naslouchací proces `console` k `Listeners` kolekce pro trasovacího.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
