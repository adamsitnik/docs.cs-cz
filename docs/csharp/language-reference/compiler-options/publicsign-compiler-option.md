---
title: -publicsign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738063"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="e873f-102">-publicsign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="e873f-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="e873f-103">Tato možnost způsobí, že kompilátor použít veřejný klíč, ale není ve skutečnosti podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="e873f-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="e873f-104">**- Publicsign** možnost nastaví bit v sestavení, že modul runtime, že soubor je ve skutečnosti podepsán.</span><span class="sxs-lookup"><span data-stu-id="e873f-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="e873f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e873f-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="e873f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e873f-106">Arguments</span></span>

<span data-ttu-id="e873f-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="e873f-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="e873f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e873f-108">Remarks</span></span>

<span data-ttu-id="e873f-109">**- Publicsign** možnost vyžaduje použití [- keyfile](keyfile-compiler-option.md) nebo [- keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e873f-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="e873f-110">**Keyfile** nebo **keycontainer** možnosti zadat veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="e873f-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="e873f-111">**- Publicsign** a **- delaysign** možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="e873f-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="e873f-112">Někdy označuje jako "falešnou přihlášení" nebo "OSS znak", veřejné podepisování obsahuje veřejný klíč v sestavení výstupu a nastaví příznak "podepsaný", ale není ve skutečnosti podepsat sestavení s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="e873f-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="e873f-113">To je užitečné pro open source projekty, pokud chtějí uživatelé vytvářet sestavení, které jsou kompatibilní s vydaných sestavení "plně podepsané", ale nemají přístup k privátnímu klíči použitý k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="e873f-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="e873f-114">Protože téměř žádné příjemce ve skutečnosti je potřeba zkontrolovat, pokud je plně podepsané sestavení, předdefinované veřejně sestavení jsou použitelných téměř každý scénář, ve kterém se použije plně podepsané jeden.</span><span class="sxs-lookup"><span data-stu-id="e873f-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e873f-115">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e873f-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="e873f-116">Otevřít **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e873f-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="e873f-117">Upravit **zpoždění podepsání** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e873f-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="e873f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e873f-118">See also</span></span>

- [<span data-ttu-id="e873f-119">-Delaysign – možnost kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e873f-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="e873f-120">-Keyfile – možnost kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e873f-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="e873f-121">-Keycontainer – možnost kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e873f-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="e873f-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e873f-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="e873f-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e873f-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
