---
title: -keycontainer (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: cf51bccc98f04c38149ec821b7064a4844d7e804
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662813"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="56d88-102">-keycontainer (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="56d88-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="56d88-103">Určuje název kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="56d88-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56d88-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="56d88-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="56d88-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="56d88-106">Název kontejner klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="56d88-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56d88-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56d88-107">Remarks</span></span>  
 <span data-ttu-id="56d88-108">Když **- keycontainer** není použita možnost, kompilátor vytvoří komponentu sdílet.</span><span class="sxs-lookup"><span data-stu-id="56d88-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="56d88-109">Kompilátor vloží veřejný klíč do manifestu sestavení ze zadaného kontejneru a podepíše konečné sestavení soukromým klíčem.</span><span class="sxs-lookup"><span data-stu-id="56d88-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="56d88-110">Chcete-li generovat soubor s klíčem, zadejte `sn -k file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="56d88-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="56d88-111">`sn -i` nainstaluje pár klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="56d88-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="56d88-112">Tato možnost není podporována při spuštění kompilátoru u CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="56d88-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="56d88-113">Chcete-li při sestavování u CoreCLR podepsání sestavení, použijte [- keyfile](keyfile-compiler-option.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="56d88-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="56d88-114">Pokud kompilujete s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), název souboru s klíčem je uložené v modulu a součástí sestavení při kompilaci tento modul do sestavení pomocí [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="56d88-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="56d88-115">Tuto možnost lze také nastavit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) ve zdrojovém kódu pro jakýkoli modul Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="56d88-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="56d88-116">Můžete také předat údaje o šifrování pro kompilátor [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="56d88-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="56d88-117">Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Pokud má veřejný klíč do manifestu sestavení, ale chcete zpoždění podepsání sestavení, dokud byl testován.</span><span class="sxs-lookup"><span data-stu-id="56d88-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="56d88-118">Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="56d88-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="56d88-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="56d88-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="56d88-120">Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="56d88-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="56d88-121">Programově přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="56d88-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d88-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56d88-122">See also</span></span>

- [<span data-ttu-id="56d88-123">-Keyfile – možnost kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="56d88-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="56d88-124">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="56d88-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="56d88-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="56d88-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
