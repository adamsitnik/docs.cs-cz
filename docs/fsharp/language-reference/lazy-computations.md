---
title: Opožděné výpočty
description: Zjistěte, jak F# opožděné výpočty může zlepšit výkon aplikací a knihoven.
ms.date: 05/16/2016
ms.openlocfilehash: 35f4a3f7a88ef1650497e0c943234b3574d13b38
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610070"
---
# <a name="lazy-computations"></a><span data-ttu-id="2c02a-103">Opožděné výpočty</span><span class="sxs-lookup"><span data-stu-id="2c02a-103">Lazy Computations</span></span>

<span data-ttu-id="2c02a-104">*Opožděné výpočty* jsou výpočty, které není u nich vyhodnoceno okamžitě, ale místo toho se vyhodnocují v případě potřeby výsledek.</span><span class="sxs-lookup"><span data-stu-id="2c02a-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="2c02a-105">To může pomoct zlepšit výkon kódu.</span><span class="sxs-lookup"><span data-stu-id="2c02a-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c02a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c02a-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="2c02a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c02a-107">Remarks</span></span>

<span data-ttu-id="2c02a-108">V předchozí syntaxi *výraz* je kód, který je vyhodnocen pouze v případě, že výsledek je nutné použít, a *identifikátor* je hodnota, která ukládá výsledek.</span><span class="sxs-lookup"><span data-stu-id="2c02a-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="2c02a-109">Hodnota je typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečný typ, který se používá pro `'T` se určí na základě výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="2c02a-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="2c02a-110">Opožděné výpočty umožňují zvýšit výkon tím, že omezují spuštění výpočtu na pouze situace, ve kterých je potřeba výsledku.</span><span class="sxs-lookup"><span data-stu-id="2c02a-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="2c02a-111">K vynucení výpočtu, která se má provést, zavolejte metodu `Force`.</span><span class="sxs-lookup"><span data-stu-id="2c02a-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="2c02a-112">`Force` způsobí, že spuštění provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="2c02a-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="2c02a-113">Následující volání `Force` vrátit stejný výsledek, ale neprovádět je jakýkoli kód.</span><span class="sxs-lookup"><span data-stu-id="2c02a-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="2c02a-114">Následující kód ukazuje použití opožděné výpočty a použití `Force`.</span><span class="sxs-lookup"><span data-stu-id="2c02a-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="2c02a-115">V tomto kódu typu `result` je `Lazy<int>`a `Force` vrátí metoda `int`.</span><span class="sxs-lookup"><span data-stu-id="2c02a-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="2c02a-116">Opožděné vyhodnocení, ale ne `Lazy` zadejte, se také používá pro pořadí.</span><span class="sxs-lookup"><span data-stu-id="2c02a-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="2c02a-117">Další informace najdete v tématu [pořadí](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="2c02a-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c02a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c02a-118">See also</span></span>

- [<span data-ttu-id="2c02a-119">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2c02a-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2c02a-120">Lazyextensions – modul</span><span class="sxs-lookup"><span data-stu-id="2c02a-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)