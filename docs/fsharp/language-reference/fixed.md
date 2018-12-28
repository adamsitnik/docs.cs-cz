---
title: Klíčové slovo fixed
description: Přečtěte si, jak připnout místní do zásobníku, aby se zabránilo kolekce s F# – klíčové slovo ' fixed'.
ms.date: 04/24/2017
ms.openlocfilehash: 7fdf66560f3e2ab7584b00c7e4584d7f6c161858
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614331"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="71f8f-103">Klíčové slovo fixed</span><span class="sxs-lookup"><span data-stu-id="71f8f-103">The fixed keyword</span></span>

<span data-ttu-id="71f8f-104">F#4.1 zavádí `fixed` – klíčové slovo, které umožňuje "připnout" místní do zásobníku, aby se zabránilo jejímu shromážděných nebo přesunuty během uvolňování.</span><span class="sxs-lookup"><span data-stu-id="71f8f-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="71f8f-105">Používá se pro programovacích scénářů pro nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="71f8f-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="71f8f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71f8f-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="71f8f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71f8f-107">Remarks</span></span>

<span data-ttu-id="71f8f-108">Tato zásada rozšiřuje syntaxe výrazy umožňují extrahování ukazatel a vytvoříte jejich vazbu na název, který je zabráněno shromážděných nebo přesunuty během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="71f8f-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="71f8f-109">Ukazatel z výrazu je pevně prostřednictvím `fixed` – klíčové slovo je vázán na identifikátor rozhraní prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="71f8f-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="71f8f-110">Sémantika této je podobný správu prostředků prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="71f8f-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="71f8f-111">Ukazatel vyřešen, zatímco se nachází v oboru, a jakmile je mimo rozsah, už je pevná.</span><span class="sxs-lookup"><span data-stu-id="71f8f-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="71f8f-112">`fixed` nelze použít mimo kontext `use` vazby.</span><span class="sxs-lookup"><span data-stu-id="71f8f-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="71f8f-113">Je třeba svázat ukazatel myši na název s `use`.</span><span class="sxs-lookup"><span data-stu-id="71f8f-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="71f8f-114">Použití `fixed` musí nastat do během výraz ve funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="71f8f-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="71f8f-115">Nelze ji použít v oboru skriptu úrovni nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="71f8f-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="71f8f-116">Stejně jako všechny ukazatele kód to je nebezpečné funkce a vygeneruje upozornění při použití.</span><span class="sxs-lookup"><span data-stu-id="71f8f-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="71f8f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="71f8f-117">Example</span></span>

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="71f8f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71f8f-118">See also</span></span>

- [<span data-ttu-id="71f8f-119">Nativeptr – modul</span><span class="sxs-lookup"><span data-stu-id="71f8f-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
