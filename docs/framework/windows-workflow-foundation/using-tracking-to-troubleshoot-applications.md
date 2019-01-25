---
title: Řešení potíží s aplikací pomocí sledování
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 1ed95a26f682fcdb609b410251fdb3f8b647016a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734419"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="c7817-102">Řešení potíží s aplikací pomocí sledování</span><span class="sxs-lookup"><span data-stu-id="c7817-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="c7817-103">Windows Workflow Foundation (WF) umožňuje sledovat související pracovní postup informace, které poskytují podrobnosti do spuštění Windows Workflow Foundation aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="c7817-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="c7817-104">Hostitele Windows Workflow Foundation je možné ji zachytit události pracovního postupu za běhu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7817-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="c7817-105">Pokud váš pracovní postup generuje chyby nebo výjimky, můžete použít sledování podrobnosti pro řešení potíží s jeho zpracování modelu Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="c7817-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="c7817-106">Řešení potíží s WF pomocí sledování WF</span><span class="sxs-lookup"><span data-stu-id="c7817-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="c7817-107">Ke zjištění chyb v rámci zpracování aktivit Windows Workflow Foundation, můžete povolit sledování pomocí sledování profil, který se dotazuje <xref:System.Activities.Tracking.ActivityStateRecord> v chybovém stavu.</span><span class="sxs-lookup"><span data-stu-id="c7817-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="c7817-108">V následujícím kódu je zadán odpovídající dotaz.</span><span class="sxs-lookup"><span data-stu-id="c7817-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="c7817-109">Pokud chybu se rozšíří a zpracovávají v rámci obslužné rutiny chyb (například <xref:System.Activities.Statements.TryCatch> aktivity) to lze zjistit pomocí <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="c7817-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="c7817-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Označuje zdrojová aktivita chyby a název obslužné rutiny chyb.</span><span class="sxs-lookup"><span data-stu-id="c7817-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="c7817-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Obsahuje podrobné informace o chybě v podobě zásobník výjimek pro chybu. Dotaz přihlásit k odběru <xref:System.Activities.Tracking.FaultPropagationRecord> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7817-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="c7817-112">Pokud nezpracovává chybu v rámci pracovního postupu, který je výsledkem neošetřená výjimka v instanci pracovního postupu a instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="c7817-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="c7817-113">Informace o tom podrobnosti neošetřené výjimky, musí profilu sledování dotáže na záznam instance pracovního postupu s `state name="UnhandledException"` jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7817-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="c7817-114">Když instance pracovního postupu dojde neošetřené výjimce <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objektu je vygenerován, pokud bylo povoleno sledování Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="c7817-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="c7817-115">Tento záznam sledování obsahuje podrobné informace o chybě v podobě zásobník výjimek.</span><span class="sxs-lookup"><span data-stu-id="c7817-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="c7817-116">Obsahuje podrobnosti o zdroj chyby (například aktivita), který s chybou a výsledkem neošetřených výjimek. Přihlásit k odběru selhání události z Windows Workflow Foundation, povolte tak, že přidáte sledování účastník sledování.</span><span class="sxs-lookup"><span data-stu-id="c7817-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="c7817-117">Nakonfigurovat tímto účastníkem sledování profil, který se dotazuje na `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, a `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="c7817-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="c7817-118">Pokud je povolené sledování účastník sledování ETW pomocí selhání události se vysílají do relace trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="c7817-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="c7817-119">Události lze zobrazit pomocí prohlížeče událostí v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="c7817-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="c7817-120">To lze nalézt v uzlu **Prohlížeč událostí -> aplikace a služby protokoly -> Microsoft -> Windows -> aplikace Server-** analytického kanálu.</span><span class="sxs-lookup"><span data-stu-id="c7817-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7817-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7817-121">See also</span></span>
- [<span data-ttu-id="c7817-122">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="c7817-122">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="c7817-123">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="c7817-123">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
