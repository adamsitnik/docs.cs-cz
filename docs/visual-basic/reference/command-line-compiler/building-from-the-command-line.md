---
title: Sestavení z příkazového řádku (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 798baa90308c83e42b335635fb23a9983f5180fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61839381"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="cf966-102">Sestavení z příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf966-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="cf966-103">Projekt jazyka Visual Basic tvoří jeden nebo více samostatných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="cf966-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="cf966-104">Během procesu označované jako kompilace, tyto soubory jsou svedla dohromady do jednoho balíčku – jeden spustitelný soubor, který může běžet jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf966-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="cf966-105">Visual Basic poskytuje kompilátoru příkazového řádku jako alternativu ke kompilaci programů z v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf966-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="cf966-106">Kompilátoru příkazového řádku je navržené pro situace, ve kterých nechcete, aby úplná sada funkcí v rozhraní IDE – třeba když používáte nebo zápis pro počítače s omezené systémové paměti nebo prostor úložiště.</span><span class="sxs-lookup"><span data-stu-id="cf966-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="cf966-107">Chcete-li zkompilovat zdrojové soubory z integrovaného vývojového prostředí Visual Studio, zvolte **sestavení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="cf966-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="cf966-108">Při sestavování projektu soubory pomocí rozhraní IDE sady Visual Studio můžete zobrazit informace o přidružené **Vbc –** příkazu a jeho přepínače v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="cf966-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="cf966-109">Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **podrobnosti výstupu sestavení projektu nástroje MSBuild** k **normální** nebo vyšší úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="cf966-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="cf966-110">Další informace najdete v tématu [jak: Zobrazování, ukládání a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="cf966-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>  
  
 <span data-ttu-id="cf966-111">Soubory projektu (.vbproj) z příkazového řádku můžete zkompilovat pomocí nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="cf966-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="cf966-112">Další informace najdete v tématu [Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) a [názorný postup: Použití nástroje MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="cf966-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf966-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cf966-113">In This Section</span></span>  
 [<span data-ttu-id="cf966-114">Postupy: Volání kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="cf966-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="cf966-115">Popisuje postup volání kompilátoru příkazového řádku do příkazového řádku nebo z konkrétního podadresáře.</span><span class="sxs-lookup"><span data-stu-id="cf966-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="cf966-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="cf966-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="cf966-117">Obsahuje seznam ukázkové příkazové řádky, které můžete upravit pro vlastní použití.</span><span class="sxs-lookup"><span data-stu-id="cf966-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cf966-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cf966-118">Related Sections</span></span>  
 [<span data-ttu-id="cf966-119">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="cf966-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="cf966-120">Poskytuje seznam – možnosti kompilátoru, uspořádány podle abecedy nebo podle účelu.</span><span class="sxs-lookup"><span data-stu-id="cf966-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="cf966-121">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="cf966-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="cf966-122">Popisuje, jak sestavit konkrétní části kódu.</span><span class="sxs-lookup"><span data-stu-id="cf966-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="cf966-123">Sestavování a čištění projektů a řešení v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf966-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="cf966-124">Popisuje, jak uspořádat co bude součástí jiné sestavení, zvolte Vlastnosti projektu a ujistěte se, že je ve správném pořadí sestavení projektů.</span><span class="sxs-lookup"><span data-stu-id="cf966-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
