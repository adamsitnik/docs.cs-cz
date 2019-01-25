---
title: -refout (možnosti kompilátoru C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 51029c071b3c5bdefe5af798f01238086b8e6d4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589789"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="a41a2-102">-refout (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a41a2-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="a41a2-103">**- Refout** možnost určuje, kde referenční sestavení by mělo být výstupní cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="a41a2-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="a41a2-104">To se přeloží na `metadataPeStream` v rozhraní API pro generování.</span><span class="sxs-lookup"><span data-stu-id="a41a2-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="a41a2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a41a2-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="a41a2-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="a41a2-106">Arguments</span></span>

 <span data-ttu-id="a41a2-107">`filepath` Cesta k souboru pro referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="a41a2-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="a41a2-108">Obecně to by měla odpovídat hodnotě primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="a41a2-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="a41a2-109">Doporučené konvence (používány nástrojem MSBuild), je umístit odkaz na sestavení v "ref /" podsložku vzhledem k primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="a41a2-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="a41a2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a41a2-110">Remarks</span></span>

<span data-ttu-id="a41a2-111">Obsahující jenom metadata sestavení mají jejich těl metod nahradit pomocí jediného `throw null` textu, ale zahrnout všichni členové s výjimkou anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="a41a2-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="a41a2-112">Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).</span><span class="sxs-lookup"><span data-stu-id="a41a2-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="a41a2-113">Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut.</span><span class="sxs-lookup"><span data-stu-id="a41a2-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="a41a2-114">Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho).</span><span class="sxs-lookup"><span data-stu-id="a41a2-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="a41a2-115">Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načten v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="a41a2-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="a41a2-116">Nástroje, které odpovídají na sestavení je potřeba zajistit, že se načítají referenční sestavení jako pouze pro reflexi, jinak se mu nepřidají chyby z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a41a2-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="a41a2-117">Další referenční sestavení odebrání metadat (soukromé členy) obsahující jenom metadata sestavení:</span><span class="sxs-lookup"><span data-stu-id="a41a2-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="a41a2-118">Referenční sestavení má jenom odkazy na to, co potřebuje na povrchu API.</span><span class="sxs-lookup"><span data-stu-id="a41a2-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="a41a2-119">Skutečné sestavení může mít další odkazy týkající se konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="a41a2-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="a41a2-120">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na všechny typy vyžadované pro `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a41a2-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="a41a2-121">V případech, kdy jejich odebrání nebude mít vliv na viditelně kompilace se odeberou soukromé funkce členy (metody, vlastnosti a události).</span><span class="sxs-lookup"><span data-stu-id="a41a2-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="a41a2-122">Pokud neexistují žádné `InternalsVisibleTo` atributy, provést totéž pro interní členy funkce.</span><span class="sxs-lookup"><span data-stu-id="a41a2-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="a41a2-123">Ale všechny typy (včetně privátního nebo vnořené typy) jsou uloženy v referenčních sestavení.</span><span class="sxs-lookup"><span data-stu-id="a41a2-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="a41a2-124">Všechny atributy jsou udržovány (pravidla i interní).</span><span class="sxs-lookup"><span data-stu-id="a41a2-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="a41a2-125">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="a41a2-125">All virtual methods are kept.</span></span> <span data-ttu-id="a41a2-126">Explicitní implementace rozhraní zůstanou.</span><span class="sxs-lookup"><span data-stu-id="a41a2-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="a41a2-127">Explicitně implementovaný vlastnosti a události se neodstraní jejich přístupových objektů jsou virtuální (a tedy uchovávají).</span><span class="sxs-lookup"><span data-stu-id="a41a2-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="a41a2-128">Všechna pole struktury jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="a41a2-128">All fields of a struct are kept.</span></span> <span data-ttu-id="a41a2-129">(Toto je Release candidate pro metodu post-C# – vylepšení 7.1)</span><span class="sxs-lookup"><span data-stu-id="a41a2-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="a41a2-130">`-refout` a [ `-refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="a41a2-130">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="a41a2-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a41a2-131">See also</span></span>

- [<span data-ttu-id="a41a2-132">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a41a2-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="a41a2-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="a41a2-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
