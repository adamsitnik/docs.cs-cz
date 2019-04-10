---
title: -nowarn (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 13bb50366d9c19751ef3387baf809ab69e27b5dc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324146"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="7e958-102">-nowarn (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="7e958-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="7e958-103">**- Nowarn** možnost umožňuje potlačit zobrazování upozornění na jeden nebo více kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="7e958-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="7e958-104">Více čísel upozornění oddělte čárkou.</span><span class="sxs-lookup"><span data-stu-id="7e958-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e958-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e958-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7e958-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7e958-106">Arguments</span></span>  
 `number1`<span data-ttu-id="7e958-107">, </span><span class="sxs-lookup"><span data-stu-id="7e958-107">,</span></span> `number2`  
 <span data-ttu-id="7e958-108">Čísla upozornění, která má kompilátor potlačit.</span><span class="sxs-lookup"><span data-stu-id="7e958-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e958-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e958-109">Remarks</span></span>  
 <span data-ttu-id="7e958-110">Měli byste zadat pouze číselnou část identifikátoru upozornění.</span><span class="sxs-lookup"><span data-stu-id="7e958-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="7e958-111">Například pokud chcete potlačit CS0028, budete moci zadat `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="7e958-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="7e958-112">Kompilátor bude tiše ignorovat upozornění čísla předaná `-nowarn` , která byla platná v předchozích verzích, ale které byly odebrány z kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7e958-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="7e958-113">Například CS0679 byla platná v kompilátoru v sadě Visual Studio .NET 2002, ale později byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="7e958-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="7e958-114">Nelze potlačit následující upozornění `-nowarn` možnost:</span><span class="sxs-lookup"><span data-stu-id="7e958-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
-   <span data-ttu-id="7e958-115">Kompilátor CS2002 upozornění (úroveň 1)</span><span class="sxs-lookup"><span data-stu-id="7e958-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="7e958-116">Kompilátor CS2023 upozornění (úroveň 1)</span><span class="sxs-lookup"><span data-stu-id="7e958-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="7e958-117">Kompilátor CS2029 upozornění (úroveň 1)</span><span class="sxs-lookup"><span data-stu-id="7e958-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7e958-118">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e958-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7e958-119">Otevřít **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="7e958-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="7e958-120">Podrobnosti najdete v tématu [stránku sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="7e958-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="7e958-121">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="7e958-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="7e958-122">Upravit **potlačit upozornění** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7e958-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="7e958-123">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e958-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e958-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e958-124">See also</span></span>

- [<span data-ttu-id="7e958-125">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="7e958-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="7e958-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="7e958-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="7e958-127">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e958-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
