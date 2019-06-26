---
title: Interpolace - C# kurz
description: V tomto kurzu se dozvíte, jak používat C# funkce interpolace řetězců zahrnout výraz formátovaný výsledek ve větším řetězci.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: a39ed5b320f16004f4ddcb35a7fcee5869b97137
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397809"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="ae327-103">Interpolace řetězců umožňuje vytvářet formátované řetězce</span><span class="sxs-lookup"><span data-stu-id="ae327-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="ae327-104">V tomto kurzu se naučíte, jak používat C# [interpolace](../../language-reference/tokens/interpolated.md) vložení hodnoty do jedné výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae327-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="ae327-105">Napíšete kód v C# a zobrazovat výsledky kompilace a spuštění.</span><span class="sxs-lookup"><span data-stu-id="ae327-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="ae327-106">Tento kurz obsahuje sérii lekcí, které ukazují, jak se vkládání hodnot do řetězce a tyto hodnoty formátují různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ae327-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="ae327-107">V tomto kurzu očekává, že máte počítač, který používáte pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="ae327-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="ae327-108">Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="ae327-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="ae327-109">Můžete také použít [interaktivní verze](interpolated-strings.yml) tohoto kurzu v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="ae327-109">You also can complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="ae327-110">Vytvoření interpolovaného řetězce</span><span class="sxs-lookup"><span data-stu-id="ae327-110">Create an interpolated string</span></span>

<span data-ttu-id="ae327-111">Vytvořte adresář **interpolované**.</span><span class="sxs-lookup"><span data-stu-id="ae327-111">Create a directory named **interpolated**.</span></span> <span data-ttu-id="ae327-112">Byl do aktuálního adresáře a spusťte následující příkaz z okna konzoly:</span><span class="sxs-lookup"><span data-stu-id="ae327-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="ae327-113">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="ae327-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="ae327-114">Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem, ve kterém nahradíte `<name>` s názvem:</span><span class="sxs-lookup"><span data-stu-id="ae327-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="ae327-115">Vyzkoušejte tento kód tak, že zadáte `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="ae327-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="ae327-116">Při spuštění programu se zobrazí jeden řetězec, který obsahuje vaše jméno pozdrav.</span><span class="sxs-lookup"><span data-stu-id="ae327-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="ae327-117">Řetězec obsažený ve <xref:System.Console.WriteLine%2A> je volání metody *interpolovaných výrazů řetězec*.</span><span class="sxs-lookup"><span data-stu-id="ae327-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="ae327-118">Je druh šablony, který umožňuje vytvořit jeden řetězec (volá se, *výsledný řetězec*) z řetězce obsahujícího vložený kód.</span><span class="sxs-lookup"><span data-stu-id="ae327-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="ae327-119">Interpolované řetězce se hodí hlavně k vkládání hodnot do řetězce nebo k řetězení (spojování) řetězců.</span><span class="sxs-lookup"><span data-stu-id="ae327-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="ae327-120">Tento jednoduchý příklad obsahuje dva elementy, které musí mít každém interpolovaném řetězci povinné:</span><span class="sxs-lookup"><span data-stu-id="ae327-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="ae327-121">Řetězcový literál, který začíná `$` znak, před jeho znakem uvozovek.</span><span class="sxs-lookup"><span data-stu-id="ae327-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="ae327-122">Nesmí být žádné mezery mezi `$` symbolů a znakem uvozovek.</span><span class="sxs-lookup"><span data-stu-id="ae327-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="ae327-123">(Pokud jste chtěli naleznete v tématu co se stane, když tak přece, vkládat mezeru po `$` znak, uložte soubor a znovu spusťte program zadáním `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="ae327-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="ae327-124">C# Kompilátor zobrazí chybová zpráva "Chyba CS1056: Neočekávaný znak "$" ".)</span><span class="sxs-lookup"><span data-stu-id="ae327-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="ae327-125">Jeden nebo více *interpolace výrazy*.</span><span class="sxs-lookup"><span data-stu-id="ae327-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="ae327-126">Výraz interpolace je indikován otevírací a zavírací závorkou (`{` a `}`).</span><span class="sxs-lookup"><span data-stu-id="ae327-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="ae327-127">Můžete vložit libovolný výraz C#, která vrací hodnotu (včetně `null`) uvnitř složených závorek.</span><span class="sxs-lookup"><span data-stu-id="ae327-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="ae327-128">Teď si vyzkoušíme pár dalších příkladů interpolace řetězce, s jinými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="ae327-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="ae327-129">Zahrnutí různých datových typů</span><span class="sxs-lookup"><span data-stu-id="ae327-129">Include different data types</span></span>

<span data-ttu-id="ae327-130">V předchozí části jste použili interpolace řetězců vložili jeden řetězec do druhého.</span><span class="sxs-lookup"><span data-stu-id="ae327-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="ae327-131">Výsledek výrazu interpolace může být libovolného datového typu, ale.</span><span class="sxs-lookup"><span data-stu-id="ae327-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="ae327-132">Umožňuje zahrnout hodnoty různých datových typů v interpolovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="ae327-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="ae327-133">V následujícím příkladu nejdřív nadefinujeme [třídy](../../programming-guide/classes-and-structs/classes.md) datový typ `Vegetable` , který má `Name` [vlastnost](../../properties.md) a `ToString` [metoda](../../methods.md), které [přepíše](../../language-reference/keywords/override.md) chování <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ae327-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae327-134">[ `public` Modifikátor přístupu](../../language-reference/keywords/public.md) zpřístupní metody pro jakýkoli kód klienta, k získání řetězcové reprezentace `Vegetable` instance.</span><span class="sxs-lookup"><span data-stu-id="ae327-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="ae327-135">V příkladu `Vegetable.ToString` metoda vrátí hodnotu `Name` vlastnost, která je inicializována na `Vegetable` [konstruktor](../../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="ae327-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="ae327-136">Pak vytvoříme instanci `Vegetable` třídu s názvem `item` pomocí [ `new` operátor](../../language-reference/operators/new-operator.md) a poskytnutí názvu pro konstruktor `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="ae327-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="ae327-137">Nakonec jsme zahrnuli `item` proměnné v interpolovaném řetězci, který také obsahuje <xref:System.DateTime> hodnotu, <xref:System.Decimal> hodnotu a `Unit` [výčet](../../programming-guide/enumeration-types.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ae327-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="ae327-138">Veškerý kód jazyka C# ve svém editoru nahraďte následujícím kódem a pak použít `dotnet run` příkazu ho spusťte:</span><span class="sxs-lookup"><span data-stu-id="ae327-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

<span data-ttu-id="ae327-139">Všimněte si, že výraz interpolace `item` v interpolovaném řetězci se překládá na text "eggplant" ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="ae327-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="ae327-140">Je to proto, že pokud typ výsledku výrazu není řetězec, výsledek je přeložen na řetězec následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ae327-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="ae327-141">Pokud je vyhodnocen jako výraz interpolace `null`, prázdný řetězec ("", nebo <xref:System.String.Empty?displayProperty=nameWithType>) se používá.</span><span class="sxs-lookup"><span data-stu-id="ae327-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="ae327-142">Pokud interpolace výraz není vyhodnocen na `null`, obvykle `ToString` je volána metoda typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="ae327-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="ae327-143">Můžete ho otestovat provádění aktualizací `Vegetable.ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="ae327-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="ae327-144">Ještě není nutné implementovat `ToString` metoda vzhledem k tomu, že každý typ má některé implementace této metody.</span><span class="sxs-lookup"><span data-stu-id="ae327-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="ae327-145">Abyste to mohli otestovat, okomentujte definici `Vegetable.ToString` metoda v příkladu (stačí vložit symbol komentáře `//`, před).</span><span class="sxs-lookup"><span data-stu-id="ae327-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="ae327-146">Ve výstupu se řetězec "eggplant" nahradí podle plně kvalifikovaného názvu ("rostlinné" v tomto příkladu), což je výchozí chování sady <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ae327-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae327-147">Výchozí chování `ToString` metodou hodnota výčtu je vrátí řetězcovou reprezentaci hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ae327-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="ae327-148">Ve výstupu tohoto příkladu je datum zbytečně přesné (cena lilku nemění každou sekundu) a hodnota ceny neuvádí jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="ae327-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="ae327-149">V další části se dozvíte, jak tyto problémy napravit prostřednictvím nastavení formátu řetězcové reprezentace výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="ae327-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="ae327-150">Ovládací prvek formátování interpolace výrazy</span><span class="sxs-lookup"><span data-stu-id="ae327-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="ae327-151">V předchozí části vložily dva špatně naformátované řetězce do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae327-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="ae327-152">Jedna se hodnoty data a času, pro který byl pouze data odpovídající.</span><span class="sxs-lookup"><span data-stu-id="ae327-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="ae327-153">Druhým byla cena, která nebyla označení jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="ae327-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="ae327-154">Jsou oba problémy můžeme snadno vyřešit.</span><span class="sxs-lookup"><span data-stu-id="ae327-154">Both issues are easy to address.</span></span> <span data-ttu-id="ae327-155">Interpolace řetězců umožňuje určit *řetězce formátu* , které nastavují formátování konkrétních typů.</span><span class="sxs-lookup"><span data-stu-id="ae327-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="ae327-156">Upravte volání `Console.WriteLine` z předchozího příkladu zahrnout formátovací řetězce pro výrazy data a ceny, jak je znázorněno na následujícím řádku:</span><span class="sxs-lookup"><span data-stu-id="ae327-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="ae327-157">Zadejte řetězec formátu podle interpolace výraz s čárkou (":") a nakonec formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="ae327-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="ae327-158">"d" je [řetězec formátu data a času](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) , která představuje formátu krátkého data.</span><span class="sxs-lookup"><span data-stu-id="ae327-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="ae327-159">"C2" je [řetězec standardního číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) , který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="ae327-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="ae327-160">Počet typů v knihovny .NET podporují předdefinovanou množinu řetězců formátu.</span><span class="sxs-lookup"><span data-stu-id="ae327-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="ae327-161">Patří mezi ně číselné typy a typy data a času.</span><span class="sxs-lookup"><span data-stu-id="ae327-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="ae327-162">Úplný seznam typů podporujících formátovací řetězce, naleznete v tématu [formátovací řetězce a typy v knihovně tříd rozhraní .NET](../../../standard/base-types/formatting-types.md#stringRef) v [formátovací typy v .NET](../../../standard/base-types/formatting-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="ae327-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="ae327-163">Zkuste upravit formátovací řetězce v textovém editoru a pokaždé, když provedete změnu, znovu spusťte aplikaci a zjistěte, jak změny se projeví u formátování data a času a číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ae327-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="ae327-164">Změňte "d" v `{date:d}` "t" (pro zobrazení formátu krátkého formátu času), "y" (zobrazí se rok a měsíc) a "yyyy" (zobrazí se rok jako čtyřmístné číslo).</span><span class="sxs-lookup"><span data-stu-id="ae327-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="ae327-165">Změňte "C2" v `{price:C2}` "e" (pro exponenciální notaci) a "F3" (pro číselnou hodnotu, s třemi číslicemi za desetinnou čárkou).</span><span class="sxs-lookup"><span data-stu-id="ae327-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="ae327-166">Vedle nastavení formátování můžete také řídit šířku pole a zarovnání formátovaného řetězce, které jsou obsaženy ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="ae327-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="ae327-167">V další části se dozvíte, jak na to.</span><span class="sxs-lookup"><span data-stu-id="ae327-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="ae327-168">Řídit šířku pole a zarovnání interpolace výrazů</span><span class="sxs-lookup"><span data-stu-id="ae327-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="ae327-169">Obvykle když výsledek výrazu interpolace je formátovaný řetězec, tento řetězec je součástí výsledného řetězce bez úvodní a koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="ae327-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="ae327-170">Zejména při práci se sadou dat, nebudou moct řídit šířku pole a zarovnání textu pomáhá lépe čitelný výstup.</span><span class="sxs-lookup"><span data-stu-id="ae327-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="ae327-171">Tento údaj zobrazíte, veškerý kód v textovém editoru nahraďte následujícím kódem, zadejte `dotnet run` spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="ae327-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

<span data-ttu-id="ae327-172">Jména autorů jsou zarovnané vlevo a názvy, které vytvořil jsou zarovnaná vpravo.</span><span class="sxs-lookup"><span data-stu-id="ae327-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="ae327-173">Zarovnání určíte přidáním čárky (",") po interpolaci výraz a uvedením *minimální* šířku pole.</span><span class="sxs-lookup"><span data-stu-id="ae327-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="ae327-174">Pokud zadaná hodnota je kladné číslo, pole zarovnané vpravo.</span><span class="sxs-lookup"><span data-stu-id="ae327-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="ae327-175">Pokud je záporné číslo, pole zarovnané vlevo.</span><span class="sxs-lookup"><span data-stu-id="ae327-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="ae327-176">Zkuste odstranit záporná znaménka z `{"Author",-25}` a `{title.Key,-25}` kód a znovu spustit příklad jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="ae327-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="ae327-177">Tentokrát, informace o autorovi zarovnán doprava.</span><span class="sxs-lookup"><span data-stu-id="ae327-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="ae327-178">Můžete kombinovat specifikátor zarovnání a řetězec formátu pro výraz jedné interpolace.</span><span class="sxs-lookup"><span data-stu-id="ae327-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="ae327-179">K tomuto účelu Určuje zarovnání nejprve, za nímž následuje dvojtečka a nakonec formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="ae327-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="ae327-180">Nahraďte kód uvnitř `Main` definována metoda následujícím kódem, který zobrazí tři zformátované řetězce s určenými šířkami polí.</span><span class="sxs-lookup"><span data-stu-id="ae327-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="ae327-181">Potom spusťte program zadáním `dotnet run` příkazu.</span><span class="sxs-lookup"><span data-stu-id="ae327-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="ae327-182">Výstup bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="ae327-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="ae327-183">Dokončili jste kurz interpolace řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae327-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="ae327-184">Další informace najdete v tématu [interpolace](../../language-reference/tokens/interpolated.md) tématu a [interpolace v jazyce C#](../../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="ae327-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
