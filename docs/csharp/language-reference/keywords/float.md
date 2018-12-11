---
title: float – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: 4ca256bf7204cdaad7d49ed19c662ab81bb01bf9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242448"
---
# <a name="float-c-reference"></a><span data-ttu-id="d4c3e-102">float (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d4c3e-102">float (C# Reference)</span></span>

<span data-ttu-id="d4c3e-103">`float` – Klíčové slovo znamená jednoduchý typ, který ukládá 32bitové hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="d4c3e-104">V následující tabulce jsou uvedeny přesnosti a rozsahu pro `float` typu.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-104">The following table shows the precision and approximate range for the `float` type.</span></span>

|<span data-ttu-id="d4c3e-105">Typ</span><span class="sxs-lookup"><span data-stu-id="d4c3e-105">Type</span></span>|<span data-ttu-id="d4c3e-106">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="d4c3e-106">Approximate range</span></span>|<span data-ttu-id="d4c3e-107">Přesnost</span><span class="sxs-lookup"><span data-stu-id="d4c3e-107">Precision</span></span>|<span data-ttu-id="d4c3e-108">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="d4c3e-108">.NET type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="d4c3e-109">±1.5 x 10<sup>−45</sup> k ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="d4c3e-109">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="d4c3e-110">~ 6. až 9 číslic</span><span class="sxs-lookup"><span data-stu-id="d4c3e-110">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a><span data-ttu-id="d4c3e-111">Literály</span><span class="sxs-lookup"><span data-stu-id="d4c3e-111">Literals</span></span>

<span data-ttu-id="d4c3e-112">Ve výchozím nastavení, skutečné číselný literál na pravé straně operátoru přiřazení je považován za [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="d4c3e-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="d4c3e-113">Proto se inicializovat proměnnou s plovoucí desetinnou čárkou, použijte příponu `f` nebo `F`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d4c3e-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>

```csharp
float x = 3.5F;
```

<span data-ttu-id="d4c3e-114">Pokud je předchozí deklarace nepoužívají příponu, obdržíte chybu kompilace, protože se pokoušíte ukládat [double](double.md) hodnoty do `float` proměnné.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>

## <a name="conversions"></a><span data-ttu-id="d4c3e-115">Převody</span><span class="sxs-lookup"><span data-stu-id="d4c3e-115">Conversions</span></span>

<span data-ttu-id="d4c3e-116">Integrální číselné typy a typy s plovoucí desetinnou čárkou ve výrazu můžete kombinovat.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="d4c3e-117">V takovém případě integrální typy jsou převedeny na typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="d4c3e-118">Vyhodnocení výrazu se provádí dle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="d4c3e-118">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="d4c3e-119">Pokud jeden z typů s plovoucí desetinnou čárkou je [double](double.md), je výraz vyhodnocen [double](double.md), nebo [bool](bool.md) v relační porovnání nebo porovnání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md), or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

- <span data-ttu-id="d4c3e-120">Pokud neexistuje žádné [double](double.md) zadejte výraz, výraz je vyhodnocen jako `float`, nebo [bool](bool.md) v relační porovnání nebo porovnání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="d4c3e-121">Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:</span><span class="sxs-lookup"><span data-stu-id="d4c3e-121">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="d4c3e-122">Kladnou a zápornou nulou</span><span class="sxs-lookup"><span data-stu-id="d4c3e-122">Positive and negative zero</span></span>

- <span data-ttu-id="d4c3e-123">Kladné a záporné nekonečno.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-123">Positive and negative infinity</span></span>

- <span data-ttu-id="d4c3e-124">Hodnota not-a-Number (NaN)</span><span class="sxs-lookup"><span data-stu-id="d4c3e-124">Not-a-Number value (NaN)</span></span>

- <span data-ttu-id="d4c3e-125">Konečná sada nenulové hodnoty</span><span class="sxs-lookup"><span data-stu-id="d4c3e-125">The finite set of nonzero values</span></span>

<span data-ttu-id="d4c3e-126">Další informace o těchto hodnotách naleznete v části Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](https://www.ieee.org) webu.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

## <a name="example"></a><span data-ttu-id="d4c3e-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4c3e-127">Example</span></span>

<span data-ttu-id="d4c3e-128">V následujícím příkladu [int](int.md), [krátký](short.md)a `float` jsou zahrnuty v matematickém výrazu dává `float` výsledek.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="d4c3e-129">(Nezapomeňte, že `float` je alias pro <xref:System.Single?displayProperty=nameWithType> typu.) Všimněte si, že neexistuje žádná [double](double.md) ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="d4c3e-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d4c3e-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d4c3e-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4c3e-131">See also</span></span>

- <xref:System.Single>  
- [<span data-ttu-id="d4c3e-132">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d4c3e-132">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="d4c3e-133">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d4c3e-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="d4c3e-134">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="d4c3e-134">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="d4c3e-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d4c3e-135">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="d4c3e-136">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="d4c3e-136">Integral Types Table</span></span>](integral-types-table.md)  
- [<span data-ttu-id="d4c3e-137">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="d4c3e-137">Built-In Types Table</span></span>](built-in-types-table.md)  
- [<span data-ttu-id="d4c3e-138">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="d4c3e-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="d4c3e-139">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="d4c3e-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)  