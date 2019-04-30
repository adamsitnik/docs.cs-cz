---
title: 'Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: cd3729019b5371b5313bba3814758c723c0d448a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857555"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="ec347-102">Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="ec347-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="ec347-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Je chování, které vám umožní zadat akce má být provedena, pokud dojde k neošetřené výjimce v pracovním postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ec347-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="ec347-104">Toto téma ukazuje, jak konfigurovat toto chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ec347-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="ec347-105">Ke konfiguraci WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="ec347-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="ec347-106">Přidat <`workflowUnhandledException`> element v <`behavior`> element v rámci <`serviceBehaviors`> element, pomocí `action` atribut k určení akce má být provedena, když dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec347-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ec347-107">Zjednodušená konfigurace používá předchozí ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ec347-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="ec347-108">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ec347-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="ec347-109">Toto chování lze nastavit v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec347-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="ec347-110">`action` Atribut <`workflowUnhandledException`> element můžete nastavit na jedno z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="ec347-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="ec347-111">**abandon**</span><span class="sxs-lookup"><span data-stu-id="ec347-111">**abandon**</span></span>  
     <span data-ttu-id="ec347-112">Zruší instance v paměti bez zásahu do stavu trvalé instanci (který se vrátit k poslední bod trvalého).</span><span class="sxs-lookup"><span data-stu-id="ec347-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="ec347-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="ec347-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="ec347-114">Zruší instance v paměti a aktualizuje trvalou instanci bude pozastavena.</span><span class="sxs-lookup"><span data-stu-id="ec347-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="ec347-115">**Zrušit**</span><span class="sxs-lookup"><span data-stu-id="ec347-115">**cancel**</span></span>  
     <span data-ttu-id="ec347-116">Obslužné rutiny zrušení volání pro instanci a pak dokončí instance v paměti, což může také odebrat z úložiště instancí</span><span class="sxs-lookup"><span data-stu-id="ec347-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="ec347-117">**ukončit**</span><span class="sxs-lookup"><span data-stu-id="ec347-117">**terminate**</span></span>  
     <span data-ttu-id="ec347-118">Dokončení instance v paměti a odstraní ji z úložiště instancí.</span><span class="sxs-lookup"><span data-stu-id="ec347-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="ec347-119">Další informace o <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, naleznete v tématu [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="ec347-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec347-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec347-120">See also</span></span>

- [<span data-ttu-id="ec347-121">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="ec347-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="ec347-122">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ec347-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
