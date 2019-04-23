---
title: -checked (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 814e8f3aa7130c6a64e7e27951854bed7b7cbe6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333935"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="af77b-102">-checked (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="af77b-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="af77b-103">**– Zaškrtnutí** možnost určuje, zda příkaz aritmetické celé číslo, jehož výsledkem hodnotu, která je mimo rozsah datového typu a, který není v oboru [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) nebo [ unchecked](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo, způsobí, že výjimka za běhu.</span><span class="sxs-lookup"><span data-stu-id="af77b-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af77b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af77b-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="af77b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af77b-105">Remarks</span></span>  
 <span data-ttu-id="af77b-106">Celočíselný aritmetické příkaz, který je v oboru `checked` nebo `unchecked` – klíčové slovo není v souladu s vliv **– zaškrtnutí** možnost.</span><span class="sxs-lookup"><span data-stu-id="af77b-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="af77b-107">Pokud celočíselný aritmetické příkaz, který není v oboru `checked` nebo `unchecked` – klíčové slovo výsledkem je hodnota mimo rozsah datového typu, a **-checked +** (nebo **– zaškrtnutí**) se používá v kompilace, že příkaz dojde k výjimce za běhu.</span><span class="sxs-lookup"><span data-stu-id="af77b-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="af77b-108">Pokud **- checked –** se používá při kompilaci, že příkaz nezpůsobí výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="af77b-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="af77b-109">Výchozí hodnota pro tuto možnost je **- checked –**; je zakázaná kontrola přetečení.</span><span class="sxs-lookup"><span data-stu-id="af77b-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="af77b-110">V některých případech automatizované nástroje, které se používají k vytvoření velké aplikace nastavené – kontrola +.</span><span class="sxs-lookup"><span data-stu-id="af77b-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="af77b-111">Jeden scénář pro používání - checked – je globální výchozí nastavení nástroje přepsat zadáním - checked –.</span><span class="sxs-lookup"><span data-stu-id="af77b-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="af77b-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="af77b-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="af77b-113">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="af77b-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="af77b-114">Další informace najdete v tématu [stránku sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="af77b-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="af77b-115">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="af77b-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="af77b-116">Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="af77b-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="af77b-117">Upravit **kontrolovat aritmetické přetečení a podtečení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="af77b-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="af77b-118">Programový přístup k této možnosti kompilátoru, najdete v článku <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="af77b-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af77b-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="af77b-119">Example</span></span>  
 <span data-ttu-id="af77b-120">Následující příkaz kompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="af77b-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="af77b-121">Použití `-checked` v příkazu určuje, že všechny aritmetické příkaz celé číslo v souboru, který není v oboru `checked` nebo `unchecked` – klíčové slovo a jehož výsledkem je hodnota, která je mimo rozsah datového typu, dojde k výjimce za běhu čas.</span><span class="sxs-lookup"><span data-stu-id="af77b-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="af77b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af77b-122">See also</span></span>

- [<span data-ttu-id="af77b-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="af77b-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="af77b-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="af77b-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
