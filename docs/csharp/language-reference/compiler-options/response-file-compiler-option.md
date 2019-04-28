---
title: '@ (Možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 32a06c596c44cdf28e5c1bb3422b9cf8262f2c08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662410"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="5eedb-102">@ (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="5eedb-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="5eedb-103">@ – Možnost umožňují určit soubor obsahující možnosti kompilátoru a soubory zdrojového kódu pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="5eedb-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eedb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5eedb-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="5eedb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5eedb-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="5eedb-106">Soubor se seznamem – možnosti kompilátoru nebo souborů se zdrojovým kódem, chcete-li zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="5eedb-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eedb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5eedb-107">Remarks</span></span>  
 <span data-ttu-id="5eedb-108">Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem tak, jako kdyby kdyby byly zadány v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="5eedb-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="5eedb-109">Pokud chcete zadat více než jeden soubor odpovědí do kompilace, zadejte více možnosti soubor odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5eedb-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="5eedb-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5eedb-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="5eedb-111">V odpovědi na soubor, více možností kompilátoru a soubory zdrojového kódu může zobrazit na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="5eedb-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="5eedb-112">Specifikace jediné kompilátoru možnost se musí nacházet na jednom řádku (nemůžou zahrnovat více řádků).</span><span class="sxs-lookup"><span data-stu-id="5eedb-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="5eedb-113">Soubory odpovědí může mít komentáře, které začínají symbolem #.</span><span class="sxs-lookup"><span data-stu-id="5eedb-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="5eedb-114">Určení možností kompilátoru ze souboru odpovědí je stejně jako vydávání těchto příkazů na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="5eedb-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="5eedb-115">Zobrazit [sestavení z příkazového řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="5eedb-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="5eedb-116">Kompilátor zpracovává možnosti příkazu v průběhu jejich výskytu.</span><span class="sxs-lookup"><span data-stu-id="5eedb-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="5eedb-117">Argumenty příkazového řádku můžete přepsat, proto výše uvedených možností v souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="5eedb-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="5eedb-118">Možnosti v souboru odpovědí a naopak, přepíše možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědí.</span><span class="sxs-lookup"><span data-stu-id="5eedb-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="5eedb-119">C# obsahuje soubor csc.rsp, který je umístěn ve stejném adresáři jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="5eedb-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="5eedb-120">Zobrazit [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Další informace o souboru csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="5eedb-120">See [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="5eedb-121">Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio ani ji není možné změnit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="5eedb-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eedb-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5eedb-122">Example</span></span>  
 <span data-ttu-id="5eedb-123">Následují po zadání několika řádků z ukázkového souboru odpovědí:</span><span class="sxs-lookup"><span data-stu-id="5eedb-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eedb-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5eedb-124">See also</span></span>

- [<span data-ttu-id="5eedb-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5eedb-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
