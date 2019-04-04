---
title: Interpolace řetězců v jazyce C#
description: Zjistěte, jak mají být zahrnuty výsledky výrazu formátovaný výsledný řetězec v jazyce C# pomocí interpolace řetězců.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 5a66ba9215579a459b543a24ece338ffbbfd9aea
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920711"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="988a9-103">Interpolace řetězců v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="988a9-103">String interpolation in C\#</span></span>

<span data-ttu-id="988a9-104">V tomto kurzu se dozvíte, jak používat [interpolace](../language-reference/tokens/interpolated.md) formátování a zahrňte výsledky výrazu do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="988a9-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="988a9-105">V příkladech se předpokládá, že máte zkušenosti s základní koncepty jazyka C# a .NET typ formátování.</span><span class="sxs-lookup"><span data-stu-id="988a9-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="988a9-106">Pokud jste ještě interpolace řetězců nebo formátování typu .NET, podívejte se [kurzu interpolace řetězce interaktivní](exploration/interpolated-strings.yml) první.</span><span class="sxs-lookup"><span data-stu-id="988a9-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="988a9-107">Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="988a9-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="988a9-108">Úvod</span><span class="sxs-lookup"><span data-stu-id="988a9-108">Introduction</span></span>

<span data-ttu-id="988a9-109">[Interpolace](../language-reference/tokens/interpolated.md) funkce je založená na horní [složené formátování](../../standard/base-types/composite-formatting.md) běží na procesorech a poskytuje čitelné a pohodlné syntaxe zahrnout výsledky výrazu formátovaný výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="988a9-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="988a9-110">K identifikaci řetězcového literálu jako interpolovaném řetězci, předřaďte ji `$` symbol.</span><span class="sxs-lookup"><span data-stu-id="988a9-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="988a9-111">Můžete vložit libovolný platný C# výraz, který vrací hodnotu v interpolovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="988a9-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="988a9-112">V následujícím příkladu při vyhodnocování výrazu výsledek je převedena na řetězec a součástí výsledného řetězce:</span><span class="sxs-lookup"><span data-stu-id="988a9-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="988a9-113">Jak ukazuje příklad, patří uzavřením závorek výrazu v interpolovaném řetězci:</span><span class="sxs-lookup"><span data-stu-id="988a9-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="988a9-114">V době kompilace, interpolovaném řetězci se obvykle transformuje na <xref:System.String.Format%2A?displayProperty=nameWithType> volání metody.</span><span class="sxs-lookup"><span data-stu-id="988a9-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="988a9-115">Díky tomu se všechny funkce [řetězec složené formátování](../../standard/base-types/composite-formatting.md) funkce je k dispozici pro použití s interpolovanými řetězci najdete také.</span><span class="sxs-lookup"><span data-stu-id="988a9-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

<span data-ttu-id="988a9-116">Kompilátor může nahradit <xref:System.String.Format%2A?displayProperty=nameWithType> pro <xref:System.String.Concat%2A?displayProperty=nameWithType> Pokud analyzovat chování by ekvivalentní zřetězení.</span><span class="sxs-lookup"><span data-stu-id="988a9-116">The compiler may substitute a <xref:System.String.Format%2A?displayProperty=nameWithType> for <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="988a9-117">Jak určit řetězec formátu pro interpolovaný výraz</span><span class="sxs-lookup"><span data-stu-id="988a9-117">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="988a9-118">Zadejte řetězec formátu, který je podporována typem výsledku výrazu podle interpolovaný výraz s čárkou (":") a nakonec formátovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="988a9-118">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="988a9-119">Následující příklad ukazuje, jak určit standardních a vlastních formátovacích řetězců pro výrazy, které produkují data a času nebo číselné výsledky:</span><span class="sxs-lookup"><span data-stu-id="988a9-119">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="988a9-120">Další informace najdete v tématu [součást řetězec formátu](../../standard/base-types/composite-formatting.md#format-string-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="988a9-120">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="988a9-121">Tento oddíl poskytuje odkazy na témata, které popisují standardní a vlastní formátovací řetězce podporuje základní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="988a9-121">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="988a9-122">Jak řídit šířku pole a zarovnání formátovaného interpolovaný výraz</span><span class="sxs-lookup"><span data-stu-id="988a9-122">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="988a9-123">Zadejte šířku minimální pole a zarovnání formátovaného výraz výsledku podle interpolovaný výraz s čárkou (",") a konstantní výraz:</span><span class="sxs-lookup"><span data-stu-id="988a9-123">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="988a9-124">Pokud *zarovnání* hodnota je pozitivní, výraz formátovaný výsledek je zarovnaný doprava; záporná, je zarovnaná doleva.</span><span class="sxs-lookup"><span data-stu-id="988a9-124">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="988a9-125">Pokud je třeba zadat zarovnání a řetězec formátu, začněte s komponentou zarovnání:</span><span class="sxs-lookup"><span data-stu-id="988a9-125">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="988a9-126">Následující příklad ukazuje, jak určit zarovnání a používá kanálem znaky ("|") pro vymezení textová pole:</span><span class="sxs-lookup"><span data-stu-id="988a9-126">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="988a9-127">Jako příklad ukazuje výstup, pokud výraz formátovaný výsledek délka je větší než zadaná šířka pole *zarovnání* hodnota se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="988a9-127">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="988a9-128">Další informace najdete v tématu [součást zarovnání](../../standard/base-types/composite-formatting.md#alignment-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="988a9-128">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="988a9-129">Použití řídicích sekvencí v interpolovaném řetězci</span><span class="sxs-lookup"><span data-stu-id="988a9-129">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="988a9-130">Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v běžném řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="988a9-130">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="988a9-131">Další informace najdete v tématu [řetězec řídící sekvence](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="988a9-131">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="988a9-132">Interpretace doslova řídicí sekvence, použijte [verbatim](../language-reference/tokens/verbatim.md) řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="988a9-132">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="988a9-133">Doslovný interpolovaný řetězec začíná `$` znak následovaný `@` znak.</span><span class="sxs-lookup"><span data-stu-id="988a9-133">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="988a9-134">Zahrnout závorek "{" nebo "}", do výsledného řetězce, použijte dva složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="988a9-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="988a9-135">Další informace najdete v tématu [uvozovací znaky složených závorek](../../standard/base-types/composite-formatting.md#escaping-braces) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="988a9-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="988a9-136">Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a sestavit verbatim interpolovaný řetězec:</span><span class="sxs-lookup"><span data-stu-id="988a9-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="988a9-137">Jak používat Ternární podmiňovací operátor `?:` v interpolovaným výrazem</span><span class="sxs-lookup"><span data-stu-id="988a9-137">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="988a9-138">Jako dvojtečka (":") má zvláštní význam v položce s interpolovaným výrazem, aby bylo možné používat [podmiňovací operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete ho do závorek, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="988a9-138">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="988a9-139">Jak vytvořit specifické pro jazykovou verzi výsledný řetězec pomocí interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="988a9-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="988a9-140">Ve výchozím nastavení používá interpolovaném řetězci aktuální jazykové verze, které jsou definované <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> vlastnosti pro všechny operace formátování.</span><span class="sxs-lookup"><span data-stu-id="988a9-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="988a9-141">Použít implicitní převod interpolované řetězce, který se <xref:System.FormattableString?displayProperty=nameWithType> instance a volání jeho <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu pro vytvoření specifické pro jazykovou verzi výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="988a9-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="988a9-142">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="988a9-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="988a9-143">Jak ukazuje příklad, můžete použít jednu <xref:System.FormattableString> instance ke generování více výsledný řetězec pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="988a9-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="988a9-144">Postup vytvoření výsledného řetězce pomocí neutrální jazykové verze</span><span class="sxs-lookup"><span data-stu-id="988a9-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="988a9-145">Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodu, můžete použít statické <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metoda přeložit interpolovaném řetězci na výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="988a9-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="988a9-146">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="988a9-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="988a9-147">Závěr</span><span class="sxs-lookup"><span data-stu-id="988a9-147">Conclusion</span></span>

<span data-ttu-id="988a9-148">Tento kurz popisuje běžné scénáře použití interpolace řetězců.</span><span class="sxs-lookup"><span data-stu-id="988a9-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="988a9-149">Další informace o interpolace řetězců, najdete v článku [interpolace](../language-reference/tokens/interpolated.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="988a9-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="988a9-150">Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) a [složené formátování](../../standard/base-types/composite-formatting.md) témata.</span><span class="sxs-lookup"><span data-stu-id="988a9-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="988a9-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="988a9-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="988a9-152">Řetězce</span><span class="sxs-lookup"><span data-stu-id="988a9-152">Strings</span></span>](../programming-guide/strings/index.md)
