---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 6f187e9cdcabc358ee69d65e392bc59aa38e52ca
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398168"
---
# <a name="commonparameters"></a>\<commonParameters >
Představuje kolekci parametrů, které jsou používány globálně v rámci více služeb. Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> aktivity typu workflowRuntime**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<commonParameters >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|Přidá dvojici název-hodnota společných parametrů používaných službami do kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 Element definuje všechny parametry, které jsou používány globálně v rámci více služeb, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>. `<commonParameters>`  
  
> [!NOTE]
> Služba sledování SQL tuto `ConnectionString` hodnotu konzistentně nepoužívá, pokud je uvedena `<commonParameters>` v části. Některé jeho operace, jako je například načtení `StateMachineWorkflowInstance.StateHistory` vlastnosti, mohou selhat. Chcete-li tento problém vyřešit `ConnectionString` , zadejte atribut v oddílu konfigurace pro zprostředkovatele sledování, jak je uvedeno v následujícím příkladu.  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 Pro služby, které potvrzují pracovní dávky do úložišť pro uchovávání <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>dat, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a, je můžete povolit, aby znovu opakovaly `EnableRetries` svou transakci pomocí parametru, jak je znázorněno v následujícím příkladu:  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 Všimněte si, `EnableRetries` že parametr lze nastavit buď na globální úrovni (jak je uvedeno v části *CommonParameters* ), nebo pro jednotlivé služby, které `EnableRetries` podporují (jak je uvedeno v části *služby* ).  
  
 Následující vzorový kód ukazuje, jak změnit společné parametry programově.  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Příklad  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<add>](add-of-commonparameters.md)
