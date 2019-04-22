---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2fe1834c3e92c3eff016ffd7857a0473eb2e8b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816418"
---
# <a name="-recurse"></a><span data-ttu-id="1ed51-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="1ed51-102">-recurse</span></span>
<span data-ttu-id="1ed51-103">Zkompiluje soubory zdrojového kódu ve všech adresářích podřízené zadaný adresář nebo adresář projektu.</span><span class="sxs-lookup"><span data-stu-id="1ed51-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ed51-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ed51-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1ed51-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="1ed51-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1ed51-106">Optional.</span></span> <span data-ttu-id="1ed51-107">Adresář, ve kterém chcete, aby hledání začalo.</span><span class="sxs-lookup"><span data-stu-id="1ed51-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="1ed51-108">Pokud není zadán, hledání začne v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="1ed51-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="1ed51-109">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1ed51-109">Required.</span></span> <span data-ttu-id="1ed51-110">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="1ed51-110">The file(s) to search for.</span></span> <span data-ttu-id="1ed51-111">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="1ed51-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ed51-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ed51-112">Remarks</span></span>  
 <span data-ttu-id="1ed51-113">Zástupné znaky v názvu souboru můžete použít ke kompilaci všech odpovídajících souborů v adresáři projektu bez použití `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="1ed51-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="1ed51-114">Pokud není zadán žádný název výstupního souboru, kompilátor odvodí název výstupního souboru na první zpracování vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="1ed51-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="1ed51-115">Obvykle se jedná v prvním souboru v seznamu soubory zkompilovány při zobrazení podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="1ed51-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="1ed51-116">Z tohoto důvodu je nejvhodnější k určení souboru výstupu pomocí `-out` možnost.</span><span class="sxs-lookup"><span data-stu-id="1ed51-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ed51-117">`-recurse` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1ed51-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ed51-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ed51-118">Example</span></span>  
 <span data-ttu-id="1ed51-119">Následující příkaz zkompiluje všechny soubory jazyka Visual Basic v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="1ed51-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="1ed51-120">Následující příkaz zkompiluje všechny soubory jazyka Visual Basic v `Test\ABC` adresář a všechny adresáře pod něj a poté vygeneruje `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="1ed51-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ed51-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ed51-121">See also</span></span>

- [<span data-ttu-id="1ed51-122">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="1ed51-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1ed51-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ed51-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="1ed51-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="1ed51-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
