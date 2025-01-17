---
title: Element <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: 99eef6b8c264e21df7f4ecf9fc79dc607d484a0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115423"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<element > ThrowUnobservedTaskExceptions
Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda mají být neošetřené výjimky úloh ukončeny spuštěným procesem.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Neukončí běžící proces pro neošetřenou výjimku úlohy. Toto nastavení je výchozí.|  
|`true`|Ukončí běžící proces pro neošetřenou výjimku úlohy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
|||  
  
## <a name="remarks"></a>Poznámky  
 Pokud nebyla pozorována výjimka, která je přidružena k <xref:System.Threading.Tasks.Task>, není k dispozici žádná <xref:System.Threading.Tasks.Task.Wait%2A> operace, nadřazený objekt není připojen a vlastnost <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> nebyla přečtena. výjimka úlohy je považována za nepozorovanou.  
  
 V .NET Framework 4 ve výchozím nastavení, pokud je <xref:System.Threading.Tasks.Task> s nepozorovanou výjimkou uvolňování paměti, finalizační metoda vyvolá výjimku a ukončí proces. Ukončení procesu je určeno časováním uvolňování paměti a dokončením.  
  
 Aby vývojáři usnadnili psaní asynchronního kódu založeného na úlohách, .NET Framework 4,5 mění toto výchozí chování pro nepozorované výjimky. Nepozorované výjimky stále způsobují vyvolání události <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>, ale ve výchozím nastavení se proces neukončí. Místo toho je výjimka po vyvolání události ignorována bez ohledu na to, zda obslužná rutina události tuto výjimku dobere.  
  
 V .NET Framework 4,5 lze pomocí [elementu\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace povolit .NET Framework 4 chování při vyvolání výjimky.  
  
 Chování výjimky můžete určit také jedním z následujících způsobů:  
  
- Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
- Nastavením hodnoty DWORD registru ThrowUnobservedTaskExceptions = 1 v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit vyvolávání výjimek v úlohách pomocí konfiguračního souboru aplikace.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak je vyvolána nepozorovaná výjimka z úlohy. Kód musí být spuštěn jako vydaný program pro správné fungování.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
