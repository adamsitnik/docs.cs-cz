---
title: Co je nového v C# 8.0 – C# Průvodce
description: Získejte přehled o nových funkcí dostupných v C# 8.0. V tomto článku je aktuální verze Preview 2.
ms.date: 02/12/2019
ms.openlocfilehash: a1d41418b2f546c62f1d6a51b19337ee2d303ccc
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665258"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="95637-104">Co je nového v C# 8.0</span><span class="sxs-lookup"><span data-stu-id="95637-104">What's new in C# 8.0</span></span>

<span data-ttu-id="95637-105">Existuje mnoho vylepšení C# jazyk, který můžete vyzkoušet již s verzí preview 2.</span><span class="sxs-lookup"><span data-stu-id="95637-105">There are many enhancements to the C# language that you can try out already with preview 2.</span></span> <span data-ttu-id="95637-106">Nové funkce přidané ve verzi preview 2 jsou:</span><span class="sxs-lookup"><span data-stu-id="95637-106">The new features added in preview 2 are:</span></span>

- <span data-ttu-id="95637-107">[Porovnávání vzorů vylepšení](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="95637-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * [<span data-ttu-id="95637-108">Přepnout výrazy</span><span class="sxs-lookup"><span data-stu-id="95637-108">Switch expressions</span></span>](#switch-expressions)
  * [<span data-ttu-id="95637-109">Vlastnost vzory</span><span class="sxs-lookup"><span data-stu-id="95637-109">Property patterns</span></span>](#property-patterns)
  * [<span data-ttu-id="95637-110">Vzory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="95637-110">Tuple patterns</span></span>](#tuple-patterns)
  * [<span data-ttu-id="95637-111">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="95637-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="95637-112">Pomocí deklarace</span><span class="sxs-lookup"><span data-stu-id="95637-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="95637-113">Statická lokální funkce</span><span class="sxs-lookup"><span data-stu-id="95637-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="95637-114">Struktury ref uvolnitelné</span><span class="sxs-lookup"><span data-stu-id="95637-114">Disposable ref structs</span></span>](#disposable-ref-structs)

<span data-ttu-id="95637-115">Následující funkce jazyka poprvé objevil v C# 8.0 ve verzi preview 1:</span><span class="sxs-lookup"><span data-stu-id="95637-115">The following language features first appeared in C# 8.0 preview 1:</span></span>

- [<span data-ttu-id="95637-116">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="95637-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="95637-117">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="95637-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="95637-118">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="95637-118">Indices and ranges</span></span>](#indices-and-ranges)

> [!NOTE]
> <span data-ttu-id="95637-119">Tento článek byl naposledy aktualizován pro C# 8.0 ve verzi preview 2.</span><span class="sxs-lookup"><span data-stu-id="95637-119">This article was last updated for C# 8.0 preview 2.</span></span>

<span data-ttu-id="95637-120">Zbývající část tohoto článku stručně popisuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="95637-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="95637-121">Pokud podrobné články jsou k dispozici, jsou k dispozici odkazy na tyto kurzy a přehledy.</span><span class="sxs-lookup"><span data-stu-id="95637-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="95637-122">Další vzory na více místech</span><span class="sxs-lookup"><span data-stu-id="95637-122">More patterns in more places</span></span>

<span data-ttu-id="95637-123">**Porovnávání vzorů** poskytuje nástroje k zajištění funkce závislé na tvar v souvisejících, ale různé druhy dat.</span><span class="sxs-lookup"><span data-stu-id="95637-123">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="95637-124">C#7.0 vytvořit pomocí syntaxe pro typ vzory a konstantní vzory [ `is` ](../language-reference/keywords/is.md) výraz a [ `switch` ](../language-reference/keywords/switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="95637-124">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="95637-125">Tyto funkce jsou reprezentovány první nezávazně postup směrem k podpoře programovací modely, kde data a funkce live od sebe.</span><span class="sxs-lookup"><span data-stu-id="95637-125">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="95637-126">Jak se v oboru blíží další mikroslužby a další cloudové architektury, jsou potřeba další nástroje jazyka.</span><span class="sxs-lookup"><span data-stu-id="95637-126">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="95637-127">C#8.0 rozšiřuje tento slovník tak další vzorek výrazy můžete použít na více místech ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="95637-127">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="95637-128">Pokud vaše data a funkce jsou oddělené vezměte v úvahu tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="95637-128">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="95637-129">Vezměte v úvahu porovnávání vzorů při algoritmy závisí na skutečnost než objekt typu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="95637-129">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="95637-130">Tyto postupy zadejte jiný způsob, jak vyjádřit návrhy.</span><span class="sxs-lookup"><span data-stu-id="95637-130">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="95637-131">Kromě nové vzory v nových místech C# 8.0 přidá **rekurzivní vzory**.</span><span class="sxs-lookup"><span data-stu-id="95637-131">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="95637-132">Výsledek výrazu jakékoli vzor je výraz.</span><span class="sxs-lookup"><span data-stu-id="95637-132">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="95637-133">Rekurzivní vzor je jednoduše vzor výraz použitý pro výstup jiný výraz vzoru.</span><span class="sxs-lookup"><span data-stu-id="95637-133">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="95637-134">Přepnout výrazy</span><span class="sxs-lookup"><span data-stu-id="95637-134">switch expressions</span></span>

<span data-ttu-id="95637-135">Často [ `switch` ](../language-reference/keywords/switch.md) příkaz vytvoří hodnotu ve všech jeho `case` bloky.</span><span class="sxs-lookup"><span data-stu-id="95637-135">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="95637-136">**Přepnout výrazy** vám umožní používat stručnější syntaxi výrazu.</span><span class="sxs-lookup"><span data-stu-id="95637-136">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="95637-137">Existují méně opakované `case` a `break` klíčová slova a méně složených závorek.</span><span class="sxs-lookup"><span data-stu-id="95637-137">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="95637-138">Jako příklad vezměte v úvahu následující výčtového typu, který obsahuje seznam barvy rainbow:</span><span class="sxs-lookup"><span data-stu-id="95637-138">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="95637-139">Můžete převést `Rainbow` hodnotu na jeho hodnoty RGB pomocí následující metody, který obsahuje výraz přepínače:</span><span class="sxs-lookup"><span data-stu-id="95637-139">You could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="95637-140">Existuje několik vylepšení syntaxe tady:</span><span class="sxs-lookup"><span data-stu-id="95637-140">There are several syntax improvements here:</span></span>

- <span data-ttu-id="95637-141">Proměnná byla zaslána před `switch` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="95637-141">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="95637-142">Jiné pořadí vizuálně usnadňuje rozlišit výraz přepínače z příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="95637-142">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="95637-143">`case` a `:` prvky jsou nahrazeny `=>`.</span><span class="sxs-lookup"><span data-stu-id="95637-143">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="95637-144">Je stručnějším a intuitivní.</span><span class="sxs-lookup"><span data-stu-id="95637-144">It's more concise and intuitive.</span></span>
- <span data-ttu-id="95637-145">`default` Případ je nahrazen `_` zahodit.</span><span class="sxs-lookup"><span data-stu-id="95637-145">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="95637-146">Subjekty jsou výrazy, nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="95637-146">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="95637-147">Oproti, který odpovídá kódu pomocí klasického `switch` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="95637-147">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor fromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a><span data-ttu-id="95637-148">Vlastnost vzory</span><span class="sxs-lookup"><span data-stu-id="95637-148">Property patterns</span></span>

<span data-ttu-id="95637-149">**Vlastnost vzor** umožňuje tak, aby odpovídala na vlastnosti objektu prověřit.</span><span class="sxs-lookup"><span data-stu-id="95637-149">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="95637-150">Vezměte v úvahu elektronického obchodování webu, který musí vypočítat na základě adresy odběratele DPH.</span><span class="sxs-lookup"><span data-stu-id="95637-150">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="95637-151">Výpočet není základní působnosti `Address` třídy.</span><span class="sxs-lookup"><span data-stu-id="95637-151">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="95637-152">Se změní v čase, pravděpodobně častěji než změny formátu adresy.</span><span class="sxs-lookup"><span data-stu-id="95637-152">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="95637-153">Množství DPH závisí `State` vlastnost adresy.</span><span class="sxs-lookup"><span data-stu-id="95637-153">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="95637-154">Následující metoda používá vzor pro vlastnost pro výpočet DPH z adresy a cena:</span><span class="sxs-lookup"><span data-stu-id="95637-154">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
    ```

Pattern matching creates a concise syntax for expressing this algorithm.

### Tuple patterns

Some algorithms depend on multiple inputs. **Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).  The following code shows a switch expression for the game *rock, paper, scissors*:

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
    ```

The messages indicate the winner. The discard case represents the three combinations for ties, or other text inputs.

### Positional patterns

Some types include a `Deconstruct` method that deconstructs its properties into discrete variables. When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.  Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="95637-155">Používá následující metodu **poziční vzor** k extrakci hodnot z `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="95637-155">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="95637-156">Potom použije `when` klauzule určit do kvadrantu bodu:</span><span class="sxs-lookup"><span data-stu-id="95637-156">Then, it uses a `when` clause to determine the quadrant of the point:</span></span>

```csharp
static string Quadrant(Point p) => p switch
{
    (0, 0) => "origin",
    (var x, var y) when x > 0 && y > 0 => "Quadrant 1",
    (var x, var y) when x < 0 && y > 0 => "Quadrant 2",
    (var x, var y) when x < 0 && y < 0 => "Quadrant 3",
    (var x, var y) when x > 0 && y < 0 => "Quadrant 4",
    (var x, var y) => "on a border",
    _ => "unknown"
};
```

<span data-ttu-id="95637-157">Vzor zrušení v předchozím přepínače odpovídá při buď `x` nebo `y`, ale ne obojí je 0.</span><span class="sxs-lookup"><span data-stu-id="95637-157">The discard pattern in the preceding switch matches when either `x` or `y`, but not both, is 0.</span></span> <span data-ttu-id="95637-158">Výraz přepínače musíte vytvořit hodnotu nebo vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="95637-158">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="95637-159">Výraz přepínače vyvolá výjimku, pokud neodpovídá žádná případů.</span><span class="sxs-lookup"><span data-stu-id="95637-159">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="95637-160">Kompilátor vygeneruje upozornění za vás, pokud jste ve výrazu přepínače nepokrývají všechny možné případy.</span><span class="sxs-lookup"><span data-stu-id="95637-160">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

## <a name="using-declarations"></a><span data-ttu-id="95637-161">pomocí deklarace</span><span class="sxs-lookup"><span data-stu-id="95637-161">using declarations</span></span>

<span data-ttu-id="95637-162">A **using – deklarace** deklaraci proměnné předchází `using` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="95637-162">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="95637-163">To sděluje kompilátoru, že by mělo být uvolněno deklarované proměnné na konci nadřazeném oboru.</span><span class="sxs-lookup"><span data-stu-id="95637-163">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="95637-164">Zvažte například následující kód, který zapisuje do textového souboru:</span><span class="sxs-lookup"><span data-stu-id="95637-164">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="95637-165">V předchozím příkladu je soubor odstraněn po dosažení pravou složenou závorku v případě metody.</span><span class="sxs-lookup"><span data-stu-id="95637-165">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="95637-166">Který je koncem objektu oboru, ve kterém `file` je deklarována.</span><span class="sxs-lookup"><span data-stu-id="95637-166">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="95637-167">Předchozí kód je ekvivalentní následujícímu kódu pomocí klasického [příkazy using](../language-reference/keywords/using-statement.md) – příkaz:</span><span class="sxs-lookup"><span data-stu-id="95637-167">The preceding code is equivalent to the following code using the classic [using statements](../language-reference/keywords/using-statement.md) statement:</span></span>


```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="95637-168">V předchozím příkladu je soubor uvolněno při přidružené pravou složenou závorku `using` je dosažen příkaz.</span><span class="sxs-lookup"><span data-stu-id="95637-168">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="95637-169">V obou případech platí, kompilátor vygeneruje volání `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="95637-169">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="95637-170">Kompilátor vygeneruje chybu, pokud výraz v pomocí příkazu není na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="95637-170">The compiler generates an error if the expression in the using statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="95637-171">Statická lokální funkce</span><span class="sxs-lookup"><span data-stu-id="95637-171">Static local functions</span></span>

<span data-ttu-id="95637-172">Teď můžete přidávat `static` modifikátor lokální funkce zajistit, že místní funkce nezachytí (referenční dokumentace) všechny proměnné v ohraničujícím oboru.</span><span class="sxs-lookup"><span data-stu-id="95637-172">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="95637-173">Tím se vygeneruje `CS8421`, "statické lokální funkce nesmí obsahovat odkaz na <variable>."</span><span class="sxs-lookup"><span data-stu-id="95637-173">Doing so generates `CS8421`, "A static local function can't contain a reference to <variable>."</span></span> 

<span data-ttu-id="95637-174">Uvažujme následující kód.</span><span class="sxs-lookup"><span data-stu-id="95637-174">Consider the following code.</span></span> <span data-ttu-id="95637-175">Lokální funkce `LocalFunction` přistupuje k proměnné `y`, které jsou deklarovány v ohraničujícím oboru (metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="95637-175">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="95637-176">Proto `LocalFunction` se nedá deklarovat pomocí `static` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="95637-176">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="95637-177">Následující kód obsahuje statické lokální funkce.</span><span class="sxs-lookup"><span data-stu-id="95637-177">The following code contains a static local function.</span></span> <span data-ttu-id="95637-178">Může být statická, protože nemá přístup k žádné proměnné v ohraničujícím oboru:</span><span class="sxs-lookup"><span data-stu-id="95637-178">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="95637-179">Struktury ref uvolnitelné</span><span class="sxs-lookup"><span data-stu-id="95637-179">Disposable ref structs</span></span>

<span data-ttu-id="95637-180">A `struct` deklarované s `ref` modifikátor nemusí implementovat jakékoli rozhraní a proto nemůže implementovat <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="95637-180">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="95637-181">Proto aby `ref struct` odstraněn, musí mít k dispozici přístup `void Dispose()` metoda.</span><span class="sxs-lookup"><span data-stu-id="95637-181">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="95637-182">Typy s možnou hodnotou Null odkazů</span><span class="sxs-lookup"><span data-stu-id="95637-182">Nullable reference types</span></span>

<span data-ttu-id="95637-183">V kontextu poznámky s možnou hodnotou Null, všechny proměnné typu odkazu se považuje za **nonnullable odkazový typ**.</span><span class="sxs-lookup"><span data-stu-id="95637-183">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="95637-184">Pokud chcete určit, že proměnná může mít hodnotu null, musí připojit k názvu typu `?` deklarovat jako proměnnou **typ s možnou hodnotou Null odkazu**.</span><span class="sxs-lookup"><span data-stu-id="95637-184">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="95637-185">Pro typy odkazů nemá kompilátor používá k zajištění, že místní proměnné jsou inicializovány na hodnotu než null při deklaraci analýzy toku.</span><span class="sxs-lookup"><span data-stu-id="95637-185">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="95637-186">Pole musí být inicializován během konstrukce.</span><span class="sxs-lookup"><span data-stu-id="95637-186">Fields must be initialized during construction.</span></span> <span data-ttu-id="95637-187">Kompilátor generuje upozornění, pokud proměnná není nastavená v všechny konstruktory nebo inicializátor.</span><span class="sxs-lookup"><span data-stu-id="95637-187">The compiler generates a warning if the variable is not set in all constructors, or an initializer.</span></span> <span data-ttu-id="95637-188">Kromě toho nemá odkazové typy nelze přiřadit hodnotu, která může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="95637-188">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="95637-189">Typy odkazů s možnou hodnotou Null nejsou kontrola nejsou přiřazen nebo inicializován na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="95637-189">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="95637-190">Však kompilátor používá k zajištění, že všechny proměnné typu odkazu s možnou hodnotou null je porovnány s hodnotou null, předtím, než má získat přístup nebo přiřazený k typu odkazu nonnullable analýzy toku.</span><span class="sxs-lookup"><span data-stu-id="95637-190">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="95637-191">Další informace o funkci v přehledu [typy s možnou hodnotou Null odkazů](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="95637-191">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="95637-192">Vyzkoušejte si to sami v nové aplikaci v tomto [kurzu typy s možnou hodnotou Null reference](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="95637-192">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="95637-193">Seznamte se s kroky při migraci z existujícího základu kódu, aby použití typů s povolenou hodnotou Null odkaz [migrace aplikace pro použití s možnou hodnotou NULL referenční typy kurzu].. /tutorials/upgrade-to-Nullable-References.MD).</span><span class="sxs-lookup"><span data-stu-id="95637-193">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial]../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="95637-194">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="95637-194">Asynchronous streams</span></span>

<span data-ttu-id="95637-195">Počínaje C# 8.0, lze vytvářet a využívat datové proudy asynchronně.</span><span class="sxs-lookup"><span data-stu-id="95637-195">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="95637-196">Metodu vracející asynchronní datový proud má tři vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="95637-196">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="95637-197">Jeho deklaraci byl `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="95637-197">It was declared with the `async` modifier.</span></span>
1. <span data-ttu-id="95637-198">Vrátí <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="95637-198">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="95637-199">Metoda obsahuje `yield return` příkazy vrátit po sobě jdoucí prvky v asynchronního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="95637-199">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="95637-200">Použití asynchronního datového proudu je potřeba přidat `await` – klíčové slovo před `foreach` – klíčové slovo při výčtu prvky datového proudu.</span><span class="sxs-lookup"><span data-stu-id="95637-200">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="95637-201">Přidání `await` – klíčové slovo vyžaduje metodu, která vytvoří výčet asynchronního datového proudu deklarován s `async` modifikátor a návratový typ povolené pro `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="95637-201">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="95637-202">Obvykle to znamená, že vrácení <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="95637-202">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="95637-203">Může být <xref:System.Threading.Tasks.ValueTask> nebo <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="95637-203">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="95637-204">Metoda může současně využívají a produkují asynchronní datový proud, což znamená, že by měla vrátit <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="95637-204">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="95637-205">Následující kód vygeneruje sekvenci od 1 do 20, 100 ms mezi generování každé číslo čekání:</span><span class="sxs-lookup"><span data-stu-id="95637-205">The following code generates a sequence from 1 to 20, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="95637-206">By výčet pomocí pořadí `await foreach` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="95637-206">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="95637-207">Můžete zkusit asynchronními datovými proudy sami v našem kurzu [vytváření a používání asynchronních streamů](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="95637-207">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="95637-208">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="95637-208">Indices and ranges</span></span>

<span data-ttu-id="95637-209">Rozsahy a indexy poskytují stručné syntaxe pro zadání podrozsahů v poli, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="95637-209">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="95637-210">Můžete určit index **od konce**.</span><span class="sxs-lookup"><span data-stu-id="95637-210">You can specify an index **from the end**.</span></span> <span data-ttu-id="95637-211">Zadáte **od konce** pomocí `^` operátor.</span><span class="sxs-lookup"><span data-stu-id="95637-211">You specify **from the end** using the `^` operator.</span></span> <span data-ttu-id="95637-212">Jste obeznámeni s `array[2]` znamená elementu "2 od samého začátku".</span><span class="sxs-lookup"><span data-stu-id="95637-212">You are familiar with `array[2]` meaning the element "2 from the start".</span></span> <span data-ttu-id="95637-213">Nyní `array[^2]` znamená, že element "2 od konce".</span><span class="sxs-lookup"><span data-stu-id="95637-213">Now, `array[^2]` means the element "2 from the end".</span></span> <span data-ttu-id="95637-214">Index `^0` znamená "end", nebo jedna po posledním prvku.</span><span class="sxs-lookup"><span data-stu-id="95637-214">The index `^0` means "the end", or one past that last element.</span></span>

<span data-ttu-id="95637-215">Můžete zadat **rozsah** s **operátor rozsahu**: `..`.</span><span class="sxs-lookup"><span data-stu-id="95637-215">You can specify a **range** with the **range operator**: `..`.</span></span> <span data-ttu-id="95637-216">Například `0..^0` určuje celý rozsah pole: 0 od začátku až do, s výjimkou 0 od konce.</span><span class="sxs-lookup"><span data-stu-id="95637-216">For example, `0..^0` specifies the entire range of the array: 0 from the start up to, but not including 0 from the end.</span></span> <span data-ttu-id="95637-217">Jeden z operandů může používat "z start" nebo "end".</span><span class="sxs-lookup"><span data-stu-id="95637-217">Either operand may use "from the start" or "from the end".</span></span> <span data-ttu-id="95637-218">Kromě toho může vynechat jeden z operandů.</span><span class="sxs-lookup"><span data-stu-id="95637-218">Furthermore, either operand may be omitted.</span></span> <span data-ttu-id="95637-219">Výchozí hodnoty jsou `0` pro počáteční index a `^0` end indexu.</span><span class="sxs-lookup"><span data-stu-id="95637-219">The defaults are `0` for the start index, and `^0` for the end index.</span></span>

<span data-ttu-id="95637-220">Podívejme se na několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="95637-220">Let's look at a few examples.</span></span> <span data-ttu-id="95637-221">Vezměte v úvahu následující pole označena s jeho index od samého začátku a konci:</span><span class="sxs-lookup"><span data-stu-id="95637-221">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};
```

<span data-ttu-id="95637-222">Pojem "od začátku" a "z"konec posiluje indexu každého prvku, a rozsahy adres jsou uvedeny bez konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="95637-222">The index of each element reinforces the concept of "from the start", and "from the end", and that ranges are exclusive of the end of the range.</span></span> <span data-ttu-id="95637-223">"Start" celého pole je první prvek.</span><span class="sxs-lookup"><span data-stu-id="95637-223">The "start" of the entire array is the first element.</span></span> <span data-ttu-id="95637-224">"End" celého pole *minulosti* poslední prvek.</span><span class="sxs-lookup"><span data-stu-id="95637-224">The "end" of the entire array is *past* the last element.</span></span>

<span data-ttu-id="95637-225">Můžete načíst poslední slovo s `^1` indexu:</span><span class="sxs-lookup"><span data-stu-id="95637-225">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="95637-226">Následující kód vytvoří podrozsahu s slova "rychlé", "brown" a "fox".</span><span class="sxs-lookup"><span data-stu-id="95637-226">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="95637-227">Zahrnuje `words[1]` prostřednictvím `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="95637-227">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="95637-228">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="95637-228">The element `words[4]` is not in the range.</span></span>

```csharp
var brownFox = words[1..4];
```

<span data-ttu-id="95637-229">Následující kód vytvoří podrozsahu "opožděné" a "pes".</span><span class="sxs-lookup"><span data-stu-id="95637-229">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="95637-230">Zahrnuje `words[^2]` a `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="95637-230">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="95637-231">Koncová hodnota `words[^0]` nezahrnuje:</span><span class="sxs-lookup"><span data-stu-id="95637-231">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="95637-232">Následující příklady vytváří rozsahy, které jsou otevřené skončila pro zahájení a ukončení:</span><span class="sxs-lookup"><span data-stu-id="95637-232">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

<span data-ttu-id="95637-233">Rozsahy můžete také deklarovat jako proměnné:</span><span class="sxs-lookup"><span data-stu-id="95637-233">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="95637-234">Rozsah je pak možné uvnitř `[` a `]` znaků:</span><span class="sxs-lookup"><span data-stu-id="95637-234">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```