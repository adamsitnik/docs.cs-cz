---
title: Čísla v C# úvodu k C# kurzu
description: Naučte C# se prozkoumat číselné typy, jejich vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: a06bc57e5c979b62e19407747cb2c8a2447ca114
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739136"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipulace s čísly integrálních a plovoucích bodů v jazyce C \#

V tomto kurzu se naučíte, aby se číselné C# typy v interaktivně. Budete psát malé množství kódu, potom zkompilujete a spustíte tento kód. Kurz obsahuje řadu lekcí, které prozkoumají čísla a matematické operace v C#. V těchto lekcích se naučíte základy C# jazyka.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="explore-integer-math"></a>Prozkoumat celočíselné matematické

Vytvořte adresář s názvem *Numbers – rychlý Start*. Zajistěte, aby byl aktuální adresář, a spusťte následující příkaz:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte `Console.WriteLine("Hello World!");` řádku následujícím způsobem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Spusťte tento kód zadáním `dotnet run` v příkazovém okně.

Právě jste viděli jednu ze základních matematických operací s celými čísly. Typ `int` představuje **celé**číslo, nula, kladné nebo záporné celé číslo. K přidání použijte symbol `+`. Mezi další běžné matematické operace pro celá čísla patří:

- `-` pro odčítání
- `*` pro násobení
- `/` pro dělení

Začněte tím, že prozkoumáte tyto různé operace. Přidejte tyto řádky za řádek, který zapíše hodnotu `c`:

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

Spusťte tento kód zadáním `dotnet run` v příkazovém okně.

Můžete také experimentovat při provádění více matematických operací na stejném řádku, pokud byste chtěli. Zkuste například `c = a + b - 12 * 17;`. Jsou povoleny kombinace proměnných a konstantních čísel.

> [!TIP]
> Při prozkoumávání C# (nebo jakémkoli programovacím jazyce) budete při psaní kódu dělat chyby. **Kompilátor** tyto chyby vyhledá a nahlásí je. Pokud výstup obsahuje chybové zprávy, Prohlédněte si v příkladu kód a kód v okně, co je třeba opravit.
> Toto cvičení vám pomůže zjistit strukturu C# kódu.

Dokončili jste první krok. Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte metodu `Main` na `WorkingWithIntegers` a zapište novou `Main` metodu, která volá `WorkingWithIntegers`. Až skončíte, váš kód by měl vypadat takto:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            
            // addition
            int c = a + b;
            Console.WriteLine(c);
            
            // subtraction
            c = a - b;
            Console.WriteLine(c);
            
            // multiplication
            c = a * b;
            Console.WriteLine(c);
            
            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>Prozkoumat pořadí operací

Odkomentujte volání `WorkingWithIntegers()`. Výsledkem je, že při práci v této části bude výstup méně zbytečný:

```csharp
//WorkingWithIntegers();
```

`//` spustí **Komentář** v C#. Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

C# Jazyk definuje prioritu různých matematických operací s pravidly, která jsou v souladu s pravidly, která jste se naučili v matematice.
Násobení a dělení mají přednost před sčítáním a odčítáním.
Prozkoumejte to přidáním následujícího kódu do metody `Main` a spuštěním `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Výstup ukazuje, že násobení je provedeno před sčítáním.

Můžete vynutit jiné pořadí operací přidáním závorek kolem operace nebo operací, které chcete provést jako první. Přidejte následující řádky a spusťte znovu:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Kombinování různých operací vám umožní prozkoumat víc. V dolní části metody `Main` přidejte něco jako na následující řádky. Zkuste to znovu `dotnet run`.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Možná jste si všimli zajímavého chování pro celá čísla. Celočíselné dělení vždy vytváří celočíselný výsledek, i když byste očekávali, že by výsledek zahrnoval desítkovou nebo zlomkovou část.

Pokud jste toto chování neviděli, vyzkoušejte následující kód na konci vaší `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Opětovným zadáním `dotnet run` zobrazíte výsledky.

Než začnete pokračovat, Pojďme si z tohoto oddílu pořizovat veškerý kód, který jste napsali, a vložte ho do nové metody. Zavolejte novou metodu `OrderPrecedence`.
Měli byste skončit přibližně takto:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            
            // addition
            int c = a + b;
            Console.WriteLine(c);
            
            // subtraction
            c = a - b;
            Console.WriteLine(c);
            
            // multiplication
            c = a * b;
            Console.WriteLine(c);
            
            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>Prozkoumat celočíselnou přesnost a omezení

Poslední ukázka ukázala, že dělení celého čísla zkráte výsledek.
**Zbytek** můžete získat pomocí operátoru **modulo** , `%`ho znaku. Vyzkoušejte následující kód v metodě `Main`:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# Celočíselný typ se liší od matematických celých čísel jiným způsobem: typ `int` má minimální a maximální limity. Přidejte tento kód do metody `Main`, abyste viděli tato omezení:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Pokud výpočet vytvoří hodnotu, která překračuje tato omezení, **dojde k podtečení nebo** **podtečení** . Odpověď se zobrazí jako zabalení od jednoho limitu k druhému. Přidejte tyto dva řádky do metody `Main`, abyste viděli příklad:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Všimněte si, že odpověď se velmi blíží minimálnímu (zápornému) celému číslu. Je stejný jako `min + 2`.
Operace sčítání **přetéká** povolené hodnoty pro celá čísla.
Odpověď je velmi velké záporné číslo, protože přetečení se zalomí od největší možné celočíselné hodnoty k nejmenší.

Existují i jiné číselné typy s různými limity a přesností, které byste použili, když `int` typ nevyhovuje vašim potřebám. Pojďme se podívat na další.

Později můžete kód, který jste napsali v této části, přesunout do samostatné metody. Pojmenujte ji `TestLimits`.

## <a name="work-with-the-double-type"></a>Práce s typem Double

Číselný typ `double` představuje číslo s dvojitou přesností s plovoucí desetinnou čárkou. Tyto výrazy můžou být pro vás nové. Číslo s **plovoucí desetinnou** čárkou je užitečné k vyjádření neintegrálních čísel, která mohou být velmi velká nebo malá. **Dvojitá přesnost** znamená, že se tato čísla ukládají s větší přesností než s **jednoduchou přesností**. Na moderních počítačích je častější používat dvojitou přesnost než čísla s jednoduchou přesností.
Pojďme prozkoumat. Přidejte následující kód a podívejte se na výsledek:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

Všimněte si, že odpověď obsahuje desetinnou část podílu. Vyzkoušejte trochu složitější výraz s dvojitou přesností:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

Rozsah hodnoty Double je mnohem větší než celočíselné hodnoty. Vyzkoušejte následující kód, který jste doposud napsali:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Tyto hodnoty se tisknou v matematickém zápisu. Číslo nalevo od `E` je mantisa. Číslo vpravo je exponent, jako mocnina 10.

Stejně jako desítková čísla v matematických případech můžou C# být v uvozovkách chyby zaokrouhlení. Vyzkoušejte tento kód:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Víte, že `0.3` opakování není přesně stejné jako `1/3`.

***Výzev***

Zkuste další výpočty s velkými čísly, malými čísly, násobení a dělení pomocí typu `double`. Vyzkoušejte složitější výpočty.

Po vykonání nějakého času u výzvy Vezměte kód, který jste napsali, a umístěte ho do nové metody. Pojmenujte novou metodu `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Práce s pevnými typy bodů

Viděli jste základní číselné typy v C#: celá čísla a Dvojitá přesnost.  Existuje jeden další typ, se kterým se naučíte: typ `decimal`. Typ `decimal` má menší rozsah, ale větší přesnost než `double`. **Pevný** bod znamená, že desetinná čárka (nebo binární bod) nepřesouvá. Pojďme se podívat:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Všimněte si, že rozsah je menší než typ `double`. Větší přesnost s typem Decimal můžete zobrazit tak, že zkusíte následující kód:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Přípona `M` v číslech představuje způsob, jakým by měla konstanta používat typ `decimal`.

Všimněte si, že matematický použití typu Decimal má na pravé straně desetinné čárky více číslic.

***Výzev***

Teď, když jste viděli různé číselné typy, napište kód, který vypočítá oblast kruhu, jehož poloměr je 2,50 centimetrů. Pamatujte, že oblast kruhu je poloměr čtvercového vynásobený hodnotou pí. Jedna Nápověda: .NET obsahuje konstantu pro PI, <xref:System.Math.PI?displayProperty=nameWithType>, kterou můžete použít pro tuto hodnotu.

Měli byste získat odpověď mezi 19 a 20.
Svou odpověď si můžete prohlédnout na [stránce dokončený vzorový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) .

Pokud chcete, zkuste použít jiné vzorce.

Dokončili jste rychlý Start s čísly C#. Můžete pokračovat v rychlém startu [větví a smyček](branches-and-loops-local.md) ve vlastním vývojovém prostředí.

Další informace o číslech v C# najdete v následujících tématech:

- [Celočíselné číselné typy](../../language-reference/builtin-types/integral-numeric-types.md)
- [Číselné typy s plovoucí desetinnou čárkou](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Předdefinované číselné převody](../../language-reference/builtin-types/numeric-conversions.md)
