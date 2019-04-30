---
title: Direktivy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797850"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="60a60-102">Direktivy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60a60-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="60a60-103">Témata v této části dokumentu direktivy kompilátoru jazyka Visual Basic zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="60a60-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60a60-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="60a60-104">In This Section</span></span>  
 <span data-ttu-id="60a60-105">[#Const – direktiva](../../../visual-basic/language-reference/directives/const-directive.md) – Definujte konstantu kompilátoru</span><span class="sxs-lookup"><span data-stu-id="60a60-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="60a60-106">[#ExternalSource – direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md) – určete mapování mezi zdrojovými řádky a textem mimo zdroj</span><span class="sxs-lookup"><span data-stu-id="60a60-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="60a60-107">[#If... Pak... #Else direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – zkompilujte vybrané bloky kódu</span><span class="sxs-lookup"><span data-stu-id="60a60-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="60a60-108">[#Region – direktiva](../../../visual-basic/language-reference/directives/region-directive.md) – sbalit a skrýt části kódu v editoru sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="60a60-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="60a60-109">**#Disable, #Enable** – zakažte a povolte určité varování pro oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="60a60-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="60a60-110">Můžete zakázat a povolit příliš čárkou oddělený seznam kódů upozornění.</span><span class="sxs-lookup"><span data-stu-id="60a60-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="60a60-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="60a60-111">Related Sections</span></span>  
 [<span data-ttu-id="60a60-112">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60a60-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="60a60-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60a60-113">Visual Basic</span></span>](../../../visual-basic/index.md)
