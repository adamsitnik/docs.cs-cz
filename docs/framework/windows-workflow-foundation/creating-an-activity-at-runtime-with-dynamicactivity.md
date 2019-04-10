---
title: Vytvoření aktivity za běhu pomocí dynamické aktivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: ed133e972caa9a3a62ab2ac1310cb1bd666947ce
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321224"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="2864c-102">Vytvoření aktivity za běhu pomocí dynamické aktivity</span><span class="sxs-lookup"><span data-stu-id="2864c-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<xref:System.Activities.DynamicActivity> <span data-ttu-id="2864c-103">je konkrétní zapečetěná třída s veřejným konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="2864c-103">is a concrete, sealed class with a public constructor.</span></span> <xref:System.Activities.DynamicActivity> <span data-ttu-id="2864c-104">je možné sestavit funkce aktivity za běhu pomocí aktivity modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="2864c-104">can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="2864c-105">Funkce dynamické aktivity</span><span class="sxs-lookup"><span data-stu-id="2864c-105">DynamicActivity Features</span></span>  
 <xref:System.Activities.DynamicActivity> <span data-ttu-id="2864c-106">má přístup k vlastnostem provádění, argumentů a proměnné, ale žádný přístup ke službám za běhu, jako je plánování podřízené aktivity nebo sledování.</span><span class="sxs-lookup"><span data-stu-id="2864c-106">has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="2864c-107">Vlastnosti nejvyšší úrovně můžete nastavit pomocí pracovního postupu <xref:System.Activities.Argument> objekty.</span><span class="sxs-lookup"><span data-stu-id="2864c-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="2864c-108">Tyto argumenty v imperativního kódu jsou vytvořeny pomocí vlastnosti CLR na nový typ.</span><span class="sxs-lookup"><span data-stu-id="2864c-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="2864c-109">V XAML, jsou deklarovány pomocí `x:Class` a `x:Member` značky.</span><span class="sxs-lookup"><span data-stu-id="2864c-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="2864c-110">Aktivity, které jsou vytvářeny pomocí <xref:System.Activities.DynamicActivity> rozhraní s použitím návrháře <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="2864c-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="2864c-111">Aktivity vytvořené v Návrháři můžete načíst dynamicky pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak je ukázáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="2864c-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="2864c-112">Vytvoření aktivity za běhu pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="2864c-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="2864c-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2864c-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="2864c-114">Vyberte **souboru**, **nové**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2864c-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="2864c-115">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="2864c-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2864c-116">Vyberte **Konzolová aplikace sekvenčního pracovního postupu** v **šablony** okna.</span><span class="sxs-lookup"><span data-stu-id="2864c-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="2864c-117">Název nového projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="2864c-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="2864c-118">Klikněte pravým tlačítkem na Workflow1.xaml HelloActivity projektu a vyberte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="2864c-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="2864c-119">Otevřete soubor Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2864c-119">Open Program.cs.</span></span> <span data-ttu-id="2864c-120">Na začátek souboru přidejte následující direktivy.</span><span class="sxs-lookup"><span data-stu-id="2864c-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="2864c-121">Nahraďte obsah `Main` metodu s následujícím kódem, který vytvoří <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje jediný <xref:System.Activities.Statements.WriteLine> aktivity a přiřadí ji k <xref:System.Activities.DynamicActivity.Implementation%2A> vlastnost nové dynamické aktivity.</span><span class="sxs-lookup"><span data-stu-id="2864c-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. <span data-ttu-id="2864c-122">Spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="2864c-122">Execute the application.</span></span> <span data-ttu-id="2864c-123">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="2864c-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="2864c-124">zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2864c-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="2864c-125">Vytvoření aktivity za běhu pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="2864c-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="2864c-126">Open Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2864c-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="2864c-127">Vyberte **souboru**, **nové**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2864c-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="2864c-128">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="2864c-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2864c-129">Vyberte **Konzolová aplikace pracovního postupu** v **šablony** okna.</span><span class="sxs-lookup"><span data-stu-id="2864c-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="2864c-130">Název nového projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="2864c-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="2864c-131">Otevřete v projektu HelloActivity Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="2864c-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="2864c-132">Klikněte na tlačítko **argumenty** možnost v dolní části návrháře.</span><span class="sxs-lookup"><span data-stu-id="2864c-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="2864c-133">Vytvořte nový `In` argument volá `TextToWrite` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="2864c-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="2864c-134">Přetáhněte **WriteLine** aktivita z **primitiv** části panelu nástrojů na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="2864c-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="2864c-135">Přiřaďte hodnotu `TextToWrite` k **Text** vlastnost aktivity.</span><span class="sxs-lookup"><span data-stu-id="2864c-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="2864c-136">Otevřete soubor Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2864c-136">Open Program.cs.</span></span> <span data-ttu-id="2864c-137">Na začátek souboru přidejte následující direktivy.</span><span class="sxs-lookup"><span data-stu-id="2864c-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="2864c-138">Nahraďte obsah `Main` metodu s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="2864c-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="2864c-139">Spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="2864c-139">Execute the application.</span></span> <span data-ttu-id="2864c-140">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="2864c-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="2864c-141">Zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="2864c-141">appears.</span></span>  
  
8. <span data-ttu-id="2864c-142">Klikněte pravým tlačítkem na soubor Workflow1.xaml v **Průzkumníka řešení** a vyberte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="2864c-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="2864c-143">Všimněte si, že třídy activity se vytvoří s `x:Class` a vlastnost se vytvoří s `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="2864c-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2864c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2864c-144">See also</span></span>

- [<span data-ttu-id="2864c-145">Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="2864c-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
