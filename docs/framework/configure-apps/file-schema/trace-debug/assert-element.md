---
title: <assert> Prvek
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 2f3823265e358976f970cdfa36772d2251894280
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197604"
---
# <a name="assert-element"></a>\<Assert – > – Element
Určuje, jestli se má zobrazit okno se zprávou, když zavoláte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zpráv do.  
  
 \<Konfigurace >  
\<system.diagnostics>  
\<assert>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`assertuienabled`|Nepovinný atribut.<br /><br /> Určuje, zda chcete-li zobrazit zprávu pole při **Debug.Assert –** vyhodnotí jako metoda **false**.|  
|`logfilename`|Nepovinný atribut.<br /><br /> Určuje název souboru pro zápis zprávy, když **Debug.Assert –** vyhodnotí jako **false**.|  
  
## <a name="assertuienabled-attribute"></a>assertuienabled atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|`true`|Zobrazí okno se zprávou. Toto nastavení je výchozí.|  
|`false`|Nezobrazuje okno se zprávou.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Oba atributy v  **\<vyhodnocení >** elementu jsou volitelné. Zakážete okna se zprávou bez zadání soubor pro zápis zprávy, které mají, nebo můžete určit soubor k zapsání zprávy při opuštění zprávy pole povolená.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat zobrazování okna se zprávou, když voláte **Debug.Assert –** a zápis zpráv do `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Debug>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
