---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397538"
---
# <a name="workflowidle"></a>\<workflowIdle >
Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowIdle >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|timeToPersist|Hodnota TimeSpan, která určuje dobu mezi časem, kdy je pracovní postup neaktivní a trvalý. Výchozí hodnota je TimeSpan. MaxValue.<br /><br /> Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti. Tento atribut je užitečný, pokud chcete zachovat instanci pracovního postupu s více agresivními a přitom udržet instanci v paměti tak dlouho, jak je to možné. Tento atribut je platný pouze v případě, že jeho hodnota je menší než atribut **TimeToUnload** . Pokud je větší, je ignorována. Pokud tento atribut uplyne před hodnotou určenou atributem **TimeToUnload** , musí být před uvolněním pracovního postupu dokončena trvalost. To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu. Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby. Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.|  
|timeToUnload|Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna. Výchozí hodnota je 1 minuta.<br /><br /> Uvolňování pracovního postupu znamená, že je také zachována. Pokud je tento atribut nastaven na hodnotu nula, instance pracovního postupu je trvalá a uvolněna ihned po nečinnosti pracovního postupu. Nastavení tohoto atributu na hodnotu TimeSpan. MaxValue efektivně zakáže operaci uvolnění. Instance nečinných pracovních postupů jsou nikdy uvolněna.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování > \<serviceBehaviors >](behavior-of-servicebehaviors-of-workflow.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
