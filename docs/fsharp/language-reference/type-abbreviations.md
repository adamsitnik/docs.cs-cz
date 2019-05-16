---
title: Zkratky typů
description: Další informace o F# typ – zkratky poskytnout smysluplnějšího názvu typu Pokud chcete, aby byl kód lépe čitelný.
ms.date: 05/16/2016
ms.openlocfilehash: 2930db1dcaa66741900bc91937aa1fd2f006c5f8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641684"
---
# <a name="type-abbreviations"></a><span data-ttu-id="2544f-103">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="2544f-103">Type Abbreviations</span></span>

<span data-ttu-id="2544f-104">A *– zkratka typu* je alias nebo alternativní název typu.</span><span class="sxs-lookup"><span data-stu-id="2544f-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="2544f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2544f-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="2544f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2544f-106">Remarks</span></span>

<span data-ttu-id="2544f-107">Zkratky typů můžete poskytnout typu výstižnější název, pokud chcete, aby byl kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="2544f-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="2544f-108">Můžete také využít k vytvoření snadné použití názvu pro typ, který je jinak náročné vypsat. Kromě toho vám pomůže zkratky typů usnadňují změna základního typu bez úpravy veškerý kód, který používá typ.</span><span class="sxs-lookup"><span data-stu-id="2544f-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="2544f-109">Toto je zkratka jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="2544f-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="2544f-110">Výchozí hodnota dostupnost zkratek typů `public`.</span><span class="sxs-lookup"><span data-stu-id="2544f-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="2544f-111">Zkratky typů můžete zahrnout obecné parametry, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="2544f-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="2544f-112">V předchozím kódu `Transform` je – zkratka typu, který představuje funkci, která přijímá jeden argument typu a, který vrací jedinou hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="2544f-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="2544f-113">Zkratky typů není zachováno v kódu rozhraní .NET Framework MSIL.</span><span class="sxs-lookup"><span data-stu-id="2544f-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="2544f-114">Proto při použití F# sestavení z jiného jazyka rozhraní .NET Framework, musíte použít název základního typu pro – zkratka typu.</span><span class="sxs-lookup"><span data-stu-id="2544f-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="2544f-115">Zkratky typů lze použít také na měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="2544f-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="2544f-116">Další informace najdete v tématu [měrné jednotky](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="2544f-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2544f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2544f-117">See also</span></span>

- [<span data-ttu-id="2544f-118">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2544f-118">F# Language Reference</span></span>](index.md)
