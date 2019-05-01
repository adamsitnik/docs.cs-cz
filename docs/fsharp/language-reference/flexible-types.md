---
title: Flexibilní typy
description: Další informace o použití F# anotaci typu flexibilní, což znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu.
ms.date: 05/16/2016
ms.openlocfilehash: 32857cc317bc6b4b7baf53b623b551e8e0733e41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981380"
---
# <a name="flexible-types"></a><span data-ttu-id="a1b5d-103">Flexibilní typy</span><span class="sxs-lookup"><span data-stu-id="a1b5d-103">Flexible Types</span></span>

<span data-ttu-id="a1b5d-104">A *anotace typu flexibilní* znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu, kde kompatibility se určuje podle umístění v hierarchii objektově orientované třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="a1b5d-105">Flexibilní typy jsou užitečné zejména pokud nedojde k automatické převod na typy výše v hierarchii typu, ale přesto chtějí povolit vaší funkce pro práci s jakýkoli typ v hierarchii nebo libovolný typ, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1b5d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b5d-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="a1b5d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1b5d-107">Remarks</span></span>

<span data-ttu-id="a1b5d-108">V předchozí syntaxi *typ* představuje základní typ nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="a1b5d-109">Flexibilní typ je ekvivalentní pro obecný typ, který má omezení, která omezuje povolených typů na typy, které jsou kompatibilní s typem základní typ nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="a1b5d-110">To znamená jsou následující dva řádky kódu ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="a1b5d-111">Flexibilní typy jsou užitečné v několika typy situací označuje termín.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="a1b5d-112">Například pokud máte vyšší pořadí funkci (funkce, která přebírá jako argument funkce), často je užitečné mít návratový typ flexibilní funkce.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="a1b5d-113">V následujícím příkladu, použití flexibilní typu s argumentem pořadí v `iterate2` umožňuje vyšší pořadí funkce pro práci s funkcí, které generují pořadí, pole, seznamy a jakýkoli jiný typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="a1b5d-114">Vezměte v úvahu následující dvě funkce, jednu, která vrátí sekvenci Druhý operand, který vrátí typ flexibilní.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="a1b5d-115">Další příklad, vezměte v úvahu [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkce knihovny:</span><span class="sxs-lookup"><span data-stu-id="a1b5d-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="a1b5d-116">Pro tuto funkci můžete projít žádnou z následující vyčíslitelné pořadí:</span><span class="sxs-lookup"><span data-stu-id="a1b5d-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="a1b5d-117">Seznam seznamů</span><span class="sxs-lookup"><span data-stu-id="a1b5d-117">A list of lists</span></span>
- <span data-ttu-id="a1b5d-118">Seznam polí</span><span class="sxs-lookup"><span data-stu-id="a1b5d-118">A list of arrays</span></span>
- <span data-ttu-id="a1b5d-119">Pole seznamů</span><span class="sxs-lookup"><span data-stu-id="a1b5d-119">An array of lists</span></span>
- <span data-ttu-id="a1b5d-120">Pole sekvence</span><span class="sxs-lookup"><span data-stu-id="a1b5d-120">An array of sequences</span></span>
- <span data-ttu-id="a1b5d-121">Libovolnou kombinaci vyčíslitelné pořadí</span><span class="sxs-lookup"><span data-stu-id="a1b5d-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="a1b5d-122">Následující kód používá `Seq.concat` k předvedení scénáře, které můžete podporovat pomocí flexibilní typy.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="a1b5d-123">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="a1b5d-124">V F#, stejně jako v jiných jazycích objektově orientované existují kontextech, ve kterém odvozené typy nebo typy, které implementují rozhraní se automaticky převedou na základní typ nebo typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="a1b5d-125">Tyto automatické převody nastanou argumenty s přímým přístupem, ale ne v případě, že typ je v podřízené pozice, jako součást více komplexní typ, jako je například návratovým typem funkce typ, nebo jako argument typu.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="a1b5d-126">Proto flexibilní typu notation je to užitečné hlavně Pokud aplikujete na požadovaný typ je součástí více komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="a1b5d-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1b5d-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1b5d-127">See also</span></span>

- [<span data-ttu-id="a1b5d-128">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="a1b5d-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a1b5d-129">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="a1b5d-129">Generics</span></span>](generics/index.md)