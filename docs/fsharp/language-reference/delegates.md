---
title: Delegáty
description: Zjistěte, jak pracovat s Delegáti v F#.
ms.date: 05/16/2016
ms.openlocfilehash: 0596b67530b0399df41dffdf855a07bce2bf4761
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641975"
---
# <a name="delegates"></a><span data-ttu-id="07bab-103">Delegáty</span><span class="sxs-lookup"><span data-stu-id="07bab-103">Delegates</span></span>

<span data-ttu-id="07bab-104">Delegát představuje volání funkce, jako objekt.</span><span class="sxs-lookup"><span data-stu-id="07bab-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="07bab-105">V F#, obvykle používejte funkce hodnoty k reprezentaci funkce jako hodnoty první třídy; ale delegáty se používají v rozhraní .NET Framework a proto jsou potřeba při spolupráci s rozhraní API, která je.</span><span class="sxs-lookup"><span data-stu-id="07bab-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="07bab-106">Může také používají při vytváření knihovny určená pro použití z jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07bab-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="07bab-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07bab-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="07bab-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07bab-108">Remarks</span></span>

<span data-ttu-id="07bab-109">V předchozí syntaxi `type1` reprezentuje typ argumentu nebo typy a `type2` představuje návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="07bab-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="07bab-110">Typy argumentů, které jsou reprezentovány `type1` jsou automaticky curryfikované.</span><span class="sxs-lookup"><span data-stu-id="07bab-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="07bab-111">To naznačuje, který pro tento typ použít formulář řazené kolekce členů, pokud jsou curryfikované argumenty cílová funkce a řazené kolekce členů v závorkách pro argumenty, které jsou již v podobě řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="07bab-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="07bab-112">Automatické curryfikace odebere závorka, byste museli opustit argumentem řazené kolekce členů, která odpovídá cílové metody.</span><span class="sxs-lookup"><span data-stu-id="07bab-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="07bab-113">Naleznete v příkladu kódu pro syntaxi, kterou byste měli použít ve všech případech.</span><span class="sxs-lookup"><span data-stu-id="07bab-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="07bab-114">Delegáty lze připojit k F# hodnoty a statické funkce nebo instanci metody.</span><span class="sxs-lookup"><span data-stu-id="07bab-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="07bab-115">F#Funkce hodnot je možné předat přímo jako argumenty pro delegování konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="07bab-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="07bab-116">Pro statické metody vytvoříte pomocí názvu třídy a metody delegáta.</span><span class="sxs-lookup"><span data-stu-id="07bab-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="07bab-117">Pro metodu instance zadejte instanci objektu a metoda v jeden argument.</span><span class="sxs-lookup"><span data-stu-id="07bab-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="07bab-118">V obou případech se člen přístup – operátor (`.`) se používá.</span><span class="sxs-lookup"><span data-stu-id="07bab-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="07bab-119">`Invoke` Metodu na typ delegáta volá funkci zapouzdřený objekt.</span><span class="sxs-lookup"><span data-stu-id="07bab-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="07bab-120">Také delegáty lze předat jako hodnoty funkcí odkazem název metody Invoke bez závorek.</span><span class="sxs-lookup"><span data-stu-id="07bab-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="07bab-121">Následující kód ukazuje syntaxi pro vytvoření delegáty, které představují různé metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="07bab-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="07bab-122">V závislosti na tom, jestli je metoda statickou metodu nebo metodu instance a určuje, zda má argumenty v podobě řazené kolekce členů nebo curryfikované formuláře syntaxi pro deklaraci a přiřazení delegáta se mírně liší.</span><span class="sxs-lookup"><span data-stu-id="07bab-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="07bab-123">Následující kód ukazuje některé z různými způsoby, kterými můžete pracovat s delegátů.</span><span class="sxs-lookup"><span data-stu-id="07bab-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="07bab-124">Výstup z předchozího příkladu kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="07bab-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="07bab-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07bab-125">See also</span></span>

- [<span data-ttu-id="07bab-126">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="07bab-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="07bab-127">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="07bab-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="07bab-128">Události</span><span class="sxs-lookup"><span data-stu-id="07bab-128">Events</span></span>](members/events.md)
