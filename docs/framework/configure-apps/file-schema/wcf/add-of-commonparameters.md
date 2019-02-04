---
title: <add> z <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: e0ca00911577f9f210def9326df261f772f9c26d
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674422"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="96453-102">\<Přidat > z \<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="96453-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="96453-103">Určuje dvojice název hodnota parametrů, které jsou používány globálně u více služeb.</span><span class="sxs-lookup"><span data-stu-id="96453-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="96453-104">Obvykle tento parametr obsahuje připojovací řetězec databáze, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="96453-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="96453-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="96453-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="96453-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="96453-106">\<behaviors></span></span>  
<span data-ttu-id="96453-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="96453-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="96453-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="96453-108">\<behavior></span></span>  
<span data-ttu-id="96453-109">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="96453-109">\<workflowRuntime></span></span>  
<span data-ttu-id="96453-110">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="96453-110">\<commonParameters></span></span>  
<span data-ttu-id="96453-111">\<add></span><span class="sxs-lookup"><span data-stu-id="96453-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96453-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96453-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96453-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96453-113">Attributes and Elements</span></span>  
 <span data-ttu-id="96453-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96453-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96453-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="96453-115">Attributes</span></span>  
  
|<span data-ttu-id="96453-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="96453-116">Attribute</span></span>|<span data-ttu-id="96453-117">Popis</span><span class="sxs-lookup"><span data-stu-id="96453-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96453-118">name</span><span class="sxs-lookup"><span data-stu-id="96453-118">name</span></span>|<span data-ttu-id="96453-119">Název parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="96453-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="96453-120">value</span><span class="sxs-lookup"><span data-stu-id="96453-120">value</span></span>|<span data-ttu-id="96453-121">Hodnota parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="96453-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96453-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96453-122">Child Elements</span></span>  
 <span data-ttu-id="96453-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="96453-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96453-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96453-124">Parent Elements</span></span>  
  
|<span data-ttu-id="96453-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="96453-125">Element</span></span>|<span data-ttu-id="96453-126">Popis</span><span class="sxs-lookup"><span data-stu-id="96453-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96453-127">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="96453-127">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="96453-128">Kolekce společných parametrů, které jsou používané službami.</span><span class="sxs-lookup"><span data-stu-id="96453-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="96453-129">Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="96453-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96453-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96453-130">Remarks</span></span>  
 <span data-ttu-id="96453-131">`<commonParameters>` Všechny parametry, které jsou používány globálně u více služeb, například definuje element `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="96453-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="96453-132">Pro služby, které potvrdí práci dávek trvalého úložiště, jako například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, umožníte jim to chcete zkusit znovu jejich transakce pomocí `EnableRetries` parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="96453-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="96453-133">Všimněte si, že `EnableRetries` parametr lze nastavit buď na globální úrovni (jak je znázorněno *CommonParameters* části) nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je znázorněno v *služby*části).</span><span class="sxs-lookup"><span data-stu-id="96453-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="96453-134">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="96453-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96453-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="96453-135">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="96453-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96453-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="96453-137">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="96453-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="96453-138">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="96453-138">\<commonParameters></span></span>](commonparameters.md)
