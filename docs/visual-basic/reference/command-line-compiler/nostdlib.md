---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 32a5b0531851e9f8b4280e8d2908bfe2d011bf90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547720"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="65fbe-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65fbe-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="65fbe-103">Způsobí, že kompilátor, aby automaticky odkazovat na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="65fbe-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65fbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65fbe-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="65fbe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65fbe-105">Remarks</span></span>  
 <span data-ttu-id="65fbe-106">`-nostdlib` Možnost odebere automatické odkaz na sestavení System.dll a zabrání čtení soubor Vbc.rsp kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="65fbe-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="65fbe-107">Odkazuje na soubor Vbc.rsp, který je umístěn ve stejném adresáři jako soubor Vbc.exe, běžně používaném [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importuje `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="65fbe-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65fbe-108">Vždy je odkazováno na sestavení Mscorlib.dll a Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="65fbe-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65fbe-109">`-nostdlib` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="65fbe-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65fbe-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="65fbe-110">Example</span></span>  
 <span data-ttu-id="65fbe-111">Následující kód zkompiluje `T2.vb` bez odkazování na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="65fbe-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="65fbe-112">Je nutné nastavit `_MYTYPE` – Konstanta podmíněné kompilace na řetězec "Prázdný" odeberte `My` objektu.</span><span class="sxs-lookup"><span data-stu-id="65fbe-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="65fbe-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65fbe-113">See also</span></span>
- [<span data-ttu-id="65fbe-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="65fbe-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="65fbe-115">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="65fbe-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="65fbe-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="65fbe-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="65fbe-117">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="65fbe-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
