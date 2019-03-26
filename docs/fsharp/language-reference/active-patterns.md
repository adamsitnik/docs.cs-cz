---
title: Aktivní vzorky
description: Zjistěte, jak můžete definovat pojmenované oddíly, které rozdělit vstupní data v aktivní vzory F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: 0f1f57de425836738201d2d8f84ab67a0df142ee
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412081"
---
# <a name="active-patterns"></a><span data-ttu-id="8cff8-103">Aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="8cff8-103">Active Patterns</span></span>

<span data-ttu-id="8cff8-104">*Aktivní vzory* vám umožňují definovat pojmenované oddíly, které rozdělit vstupní data tak, aby tyto názvy můžete používat ve vzorku s odpovídajícím výrazem, stejně jako byste to udělali pro diskriminované sjednocení.</span><span class="sxs-lookup"><span data-stu-id="8cff8-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="8cff8-105">Aktivní vzory můžete použít k rozložení dat v podobě přizpůsobené pro každý oddíl.</span><span class="sxs-lookup"><span data-stu-id="8cff8-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="8cff8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cff8-106">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="8cff8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8cff8-107">Remarks</span></span>

<span data-ttu-id="8cff8-108">V předchozí syntaxi identifikátory jsou názvy pro oddíly vstupních dat, která je reprezentována *argumenty*, nebo jinými slovy, názvy pro dílčí sadu všechny hodnoty argumentů.</span><span class="sxs-lookup"><span data-stu-id="8cff8-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="8cff8-109">V definici – aktivní vzor může být až sedm oddíly.</span><span class="sxs-lookup"><span data-stu-id="8cff8-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="8cff8-110">*Výraz* popisuje formulář, do kterého chcete rozložit data.</span><span class="sxs-lookup"><span data-stu-id="8cff8-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="8cff8-111">Můžete definovat pravidla pro zjišťování, který pojmenovaných oddílů hodnot uvedených jako argumenty patří do definici – aktivní vzor.</span><span class="sxs-lookup"><span data-stu-id="8cff8-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="8cff8-112">(| A |) symboly jsou označovány jako *banánů klipy* a je volána funkce vytvořené pomocí tohoto typu umožňují vazby *aktivní rozlišovač*.</span><span class="sxs-lookup"><span data-stu-id="8cff8-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="8cff8-113">Jako příklad zvažte následující active vzor s argumentem.</span><span class="sxs-lookup"><span data-stu-id="8cff8-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="8cff8-114">Aktivní vzor můžete použít ve vzoru porovnávání výrazů jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8cff8-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="8cff8-115">Výstup tohoto programu je následující:</span><span class="sxs-lookup"><span data-stu-id="8cff8-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="8cff8-116">Jiné aktivní vzory používá k rozložení datových typů v několika způsoby, například pokud má stejná podkladová data různé možné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="8cff8-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="8cff8-117">Například `Color` objekt může lze rozložit na reprezentaci RGB nebo reprezentaci HSB.</span><span class="sxs-lookup"><span data-stu-id="8cff8-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="8cff8-118">Výstup programu výše je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8cff8-118">The output of the above program is as follows:</span></span>

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="8cff8-119">V kombinaci tyto dva způsoby použití aktivní vzorky umožňují oddílu a jak rozložit data na příslušný formulář a provádí výpočty odpovídající příslušná data ve formuláři pro výpočet nejvíce usnadnil.</span><span class="sxs-lookup"><span data-stu-id="8cff8-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="8cff8-120">Výsledné výrazy odpovídající vzor povolit data mají být zapsána do pohodlný způsob, který je velmi čitelný, jehož cílem je výrazně zjednodušit potenciálně velmi složitý větvení a datové analýzy kódu.</span><span class="sxs-lookup"><span data-stu-id="8cff8-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="8cff8-121">Částečné aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="8cff8-121">Partial Active Patterns</span></span>

<span data-ttu-id="8cff8-122">V některých případech je potřeba rozdělit pouze část prostoru vstupní.</span><span class="sxs-lookup"><span data-stu-id="8cff8-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="8cff8-123">V takovém případě můžete zapsat sadu částečné vzorů z nich odpovídá některými vstupy ale selhání tak, aby odpovídaly ostatní vstupy.</span><span class="sxs-lookup"><span data-stu-id="8cff8-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="8cff8-124">Aktivní vzory, které nevytváří vždy hodnotu, se nazývají *částečné aktivní vzory*; má návratovou hodnotu, je typ možnosti.</span><span class="sxs-lookup"><span data-stu-id="8cff8-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="8cff8-125">K definování částečné active vzor, můžete použít zástupný znak (\_) na konci seznamu vzorků uvnitř banánů klipy.</span><span class="sxs-lookup"><span data-stu-id="8cff8-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="8cff8-126">Následující kód ukazuje použití částečné aktivní vzor.</span><span class="sxs-lookup"><span data-stu-id="8cff8-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="8cff8-127">Výstup z předchozího příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8cff8-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="8cff8-128">Při použití částečné aktivní vzory, někdy jednotlivé volby lze nesouvislé, nebo vylučují, ale nemusí být.</span><span class="sxs-lookup"><span data-stu-id="8cff8-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="8cff8-129">V následujícím příkladu model datové krychle a druhou mocninu vzoru nejsou nesouvislý, protože některá čísla jsou pole a datové krychle, jako je například 64.</span><span class="sxs-lookup"><span data-stu-id="8cff8-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="8cff8-130">Následující program používá vzor a zkombinovat vzory hranaté a datové krychle.</span><span class="sxs-lookup"><span data-stu-id="8cff8-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="8cff8-131">Vytiskne všechny celých čísel až 1000, které jsou jak čtverce a datové krychle, tak i ty, které jsou pouze datové krychle.</span><span class="sxs-lookup"><span data-stu-id="8cff8-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span> 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="8cff8-132">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="8cff8-132">The output is as follows:</span></span>

```
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="8cff8-133">Parametrizované aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="8cff8-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="8cff8-134">Aktivní vzory vždy provést aspoň jeden argument pro položku je nalezena shoda, může ale trvat další argumenty, v takovém případě název *parametrizované – aktivní vzor* platí.</span><span class="sxs-lookup"><span data-stu-id="8cff8-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="8cff8-135">Další argumenty povolit obecný vzor specificky určené.</span><span class="sxs-lookup"><span data-stu-id="8cff8-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="8cff8-136">Například obsahovat aktivní vzory, které často Analýza řetězců pomocí regulárních výrazů regulární výraz jako další parametr, stejně jako v následujícím kódem, který také používá částečné active vzor `Integer` definované v předcházejícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8cff8-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="8cff8-137">V tomto příkladu jsou uvedeny řetězce, které používá regulární výrazy pro různé formáty kalendářního data k přizpůsobení obecné ParseRegex active vzor.</span><span class="sxs-lookup"><span data-stu-id="8cff8-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="8cff8-138">Aktivní vzor celé číslo se používá k převod odpovídající řetězců na celá čísla, která může být předán konstruktoru data a času.</span><span class="sxs-lookup"><span data-stu-id="8cff8-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="8cff8-139">Výstup předchozího kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8cff8-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="8cff8-140">Aktivní vzory nejsou omezeny pouze na vzor odpovídající výrazy, můžete také použít na vazby let.</span><span class="sxs-lookup"><span data-stu-id="8cff8-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="8cff8-141">Výstup předchozího kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8cff8-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="8cff8-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cff8-142">See also</span></span>

- [<span data-ttu-id="8cff8-143">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="8cff8-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8cff8-144">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="8cff8-144">Match Expressions</span></span>](match-expressions.md)
