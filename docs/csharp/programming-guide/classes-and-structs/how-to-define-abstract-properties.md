---
title: 'Postupy: Definování abstraktních a vlastností - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 98a535f68efc50c2ff7409d8eadf52f9e7549566
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201947"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="895b3-102">Postupy: Definování abstraktních a vlastností (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="895b3-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="895b3-103">Následující příklad ukazuje, jak definovat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="895b3-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="895b3-104">Deklarace abstraktní vlastnost neposkytuje implementaci pro přistupující objekty vlastnosti – deklaruje, že podporuje vlastnosti třídy, ale ponechá implementace přistupujícího objektu odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="895b3-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="895b3-105">Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="895b3-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="895b3-106">Tento příklad se skládá ze tří souborů, z nichž každý je kompilován samostatně a jeho výsledné sestavení se odkazuje na další kompilace:</span><span class="sxs-lookup"><span data-stu-id="895b3-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="895b3-107">abstractshape.cs: `Shape` třídy obsahující abstraktní `Area` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="895b3-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="895b3-108">Shapes.cs: Podtřídy třídy `Shape` třídy.</span><span class="sxs-lookup"><span data-stu-id="895b3-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="895b3-109">shapetest.cs: Testovací program do zobrazované oblasti některých `Shape`-odvozené objekty.</span><span class="sxs-lookup"><span data-stu-id="895b3-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="895b3-110">Chcete-li příklad zkompilovat, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="895b3-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="895b3-111">Tím se vytvoří shapetest.exe spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="895b3-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="895b3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="895b3-112">Example</span></span>  
 <span data-ttu-id="895b3-113">Deklaruje tento soubor `Shape` třídu, která obsahuje `Area` vlastnost typu `double`.</span><span class="sxs-lookup"><span data-stu-id="895b3-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
-   <span data-ttu-id="895b3-114">Modifikátory pro vlastnost jsou umístěny v deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="895b3-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="895b3-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="895b3-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="895b3-116">Při deklarování abstraktní vlastnosti (například `Area` v tomto příkladu), můžete jednoduše označit, jaký přistupující objekty vlastnosti jsou k dispozici, ale neimplementují je.</span><span class="sxs-lookup"><span data-stu-id="895b3-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="895b3-117">V tomto příkladu, pouze [získat](../../../csharp/language-reference/keywords/get.md) přístupový objekt není k dispozici, tak vlastnost je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="895b3-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="895b3-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="895b3-118">Example</span></span>  
 <span data-ttu-id="895b3-119">Následující kód ukazuje tři podtřídy třídy `Shape` a jak mohou přepsat `Area` vlastnost poskytli vlastní implementaci.</span><span class="sxs-lookup"><span data-stu-id="895b3-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="895b3-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="895b3-120">Example</span></span>  
 <span data-ttu-id="895b3-121">Následující kód ukazuje testovací program, který vytváří celou řadou `Shape`-odvozené objekty a vytiskne jejich oblasti.</span><span class="sxs-lookup"><span data-stu-id="895b3-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="895b3-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="895b3-122">See also</span></span>

- [<span data-ttu-id="895b3-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="895b3-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="895b3-124">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="895b3-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="895b3-125">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="895b3-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="895b3-126">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="895b3-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="895b3-127">Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="895b3-127">How to: Create and Use Assemblies Using the Command Line</span></span>](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
