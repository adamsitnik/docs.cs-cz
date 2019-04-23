---
title: -keyfile (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 3e11cbca004aedd7d4f992abf2f766de4f4f5935
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344647"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="e2d2d-102">-keyfile (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="e2d2d-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="e2d2d-103">Určuje název souboru obsahujícího kryptografický klíč.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2d2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2d2d-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2d2d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2d2d-105">Arguments</span></span>  
  
|<span data-ttu-id="e2d2d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e2d2d-106">Term</span></span>|<span data-ttu-id="e2d2d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e2d2d-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="e2d2d-108">Název souboru obsahujícího klíč se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2d2d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2d2d-109">Remarks</span></span>  
 <span data-ttu-id="e2d2d-110">Pokud tato možnost se používá, kompilátor vloží veřejný klíč ze zadaného souboru do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="e2d2d-111">Chcete-li generovat soubor s klíčem, zadejte sériové číslo -k `file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="e2d2d-112">Pokud kompilujete s **-target: module**, je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení s [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e2d2d-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="e2d2d-113">Můžete také předat údaje o šifrování pro kompilátor [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e2d2d-113">You can also pass your encryption information to the compiler with [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span> <span data-ttu-id="e2d2d-114">Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) potřebujete částečně podepsaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-114">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="e2d2d-115">V případě, že - keyfile a - keycontainer zadávají ve stejné kompilaci (pomocí parametru příkazového řádku nebo pomocí vlastního atributu), kompilátor se nejdřív pokusí použít kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="e2d2d-116">Pokud tato operace úspěšná, sestavení je podepsáno pomocí informací v kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="e2d2d-117">Pokud kompilátor kontejner klíčů nenajde, pokusí se soubor určený parametrem - keyfile.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="e2d2d-118">Pokud se tato operace úspěšná, sestavení je podepsáno informacemi ze souboru klíčů a informace o klíči budou nainstalovány do kontejneru klíčů (podobné sn -i) tak, aby při další kompilaci bude platný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="e2d2d-119">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="e2d2d-120">Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="e2d2d-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e2d2d-121">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e2d2d-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e2d2d-122">Otevřít **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="e2d2d-123">Klikněte na tlačítko **podepisování** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="e2d2d-124">Upravit **vyberte soubor klíče se silným názvem** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="e2d2d-125">Programově přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d2d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2d2d-126">See also</span></span>

- [<span data-ttu-id="e2d2d-127">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2d2d-127">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="e2d2d-128">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e2d2d-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
