---
title: Strom položek programovacího modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: fe2076740331df861d1861b0cecef43cf96039b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694149"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="b5fa4-102">Strom položek programovacího modelu</span><span class="sxs-lookup"><span data-stu-id="b5fa4-102">Programming Model Item Tree</span></span>
<span data-ttu-id="b5fa4-103">Tato ukázka předvádí, jak přejít <xref:System.Activities.Presentation.Model.ModelItem> stromové struktury pomocí deklarativní datové vazby ve stromovém zobrazení Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="b5fa4-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="b5fa4-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b5fa4-104">Sample Details</span></span>
 <span data-ttu-id="b5fa4-105"><xref:System.Activities.Presentation.Model.ModelItem> Stromu je úrovní abstrakce, jakou používají [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktury ke zveřejňování dat o základní instance, který právě upravujete.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="b5fa4-106">Na následujícím obrázku je znázornění různé vrstvy v rámci infrastruktury [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5fa4-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 <span data-ttu-id="b5fa4-107">![Architektura Návrháře pracovního postupu](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span><span class="sxs-lookup"><span data-stu-id="b5fa4-107">![Workflow Designer Architecture](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span></span>

 <span data-ttu-id="b5fa4-108">A <xref:System.Activities.Presentation.Model.ModelItem> se skládá z ukazatele na základní hodnotu, stejně jako kolekce <xref:System.Activities.Presentation.Model.ModelProperty> objekty.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="b5fa4-109">A <xref:System.Activities.Presentation.Model.ModelProperty> objekt zase obsahuje data, jako jsou název a typ vlastnosti a pak ukazatel na hodnotu, která je dále jiného <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="b5fa4-110">Převaděč hodnoty se používá k manipulaci s některé <xref:System.Activities.Presentation.Model.ModelItem>s vrácená <xref:System.Activities.Presentation.Model.ModelProperty> tak, aby byly správně zobrazí ve stromovém zobrazení.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="b5fa4-111">Ukázka pak ukazuje, jak toho programovat proti <xref:System.Activities.Presentation.Model.ModelItem> stromu pomocí imperativní syntaxe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="b5fa4-112">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="b5fa4-112">To use this sample</span></span>

1.  <span data-ttu-id="b5fa4-113">Otevřete ProgrammingModelItemTree.sln řešení v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2.  <span data-ttu-id="b5fa4-114">Sestavte řešení tak, že vyberete **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3.  <span data-ttu-id="b5fa4-115">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-115">Press F5 to run the application.</span></span> <span data-ttu-id="b5fa4-116">[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Se pak zobrazí formulář.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-116">The [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] form is then displayed.</span></span>

4.  <span data-ttu-id="b5fa4-117">Klikněte na tlačítko **načíst WF** tlačítko načtete <xref:System.Activities.Presentation.Model.ModelItem> a jeho vazbu na stromové zobrazení.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5.  <span data-ttu-id="b5fa4-118">Kliknutím **změnit Model položka stromu** tlačítko spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="b5fa4-119">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b5fa4-120">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b5fa4-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5fa4-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5fa4-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b5fa4-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="b5fa4-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5fa4-123">See also</span></span>
- <xref:System.Windows.Data.IValueConverter>
