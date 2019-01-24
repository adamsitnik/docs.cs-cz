---
title: -addmodule (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: f45afd277818d7e1658751f2aae0b2153c940eee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617509"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="a4819-102">-addmodule (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a4819-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="a4819-103">Tato možnost přidá modul, který byl vytvořen s přepínačem target: module aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="a4819-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4819-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4819-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4819-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a4819-105">Arguments</span></span>  
 <span data-ttu-id="a4819-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="a4819-106">`file`, `file2`</span></span>  
 <span data-ttu-id="a4819-107">Výstupní soubor obsahující metadata.</span><span class="sxs-lookup"><span data-stu-id="a4819-107">An output file that contains metadata.</span></span> <span data-ttu-id="a4819-108">Soubor nesmí obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4819-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="a4819-109">Pokud chcete importovat více než jeden soubor, oddělte názvy souborů čárkami nebo středníkem.</span><span class="sxs-lookup"><span data-stu-id="a4819-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4819-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4819-110">Remarks</span></span>  
 <span data-ttu-id="a4819-111">Všechny moduly přidané pomocí **- addmodule** musí být ve stejném adresáři jako výstupní soubor v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a4819-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="a4819-112">To znamená modul můžete zadat do libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a4819-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="a4819-113">Pokud modul není v adresáři aplikace za běhu, zobrazí se <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="a4819-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="a4819-114">`file` nemůže obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4819-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="a4819-115">Například, pokud je výstupní soubor byl vytvořen s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), jeho metadata, můžete je importovat s **- addmodule**.</span><span class="sxs-lookup"><span data-stu-id="a4819-115">For example, if the output file was created with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="a4819-116">Pokud výstupní soubor byl vytvořen pomocí **– cíl** možností jiných než **-target: module**, její metadata nelze je importovat s **- addmodule** ale můžete je importovat s [– referenční dokumentace](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a4819-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a4819-117">Není k dispozici v sadě Visual Studio; toto – možnost kompilátoru Projekt nemůže odkazovat na modul.</span><span class="sxs-lookup"><span data-stu-id="a4819-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="a4819-118">Tato možnost kompilátoru kromě toho nelze změnit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="a4819-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4819-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4819-119">Example</span></span>  
 <span data-ttu-id="a4819-120">Kompilaci zdrojového `input.cs` a přidá metadata z `metad1.netmodule` a `metad2.netmodule` k vytvoření `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="a4819-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4819-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4819-121">See also</span></span>

- [<span data-ttu-id="a4819-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a4819-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="a4819-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="a4819-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a4819-124">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="a4819-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="a4819-125">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="a4819-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
