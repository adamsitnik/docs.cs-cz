---
title: Testování F# částí v .NET Core pomocí příkazu dotnet test a nunit
description: Seznamte se s koncepty F# testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a nunit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 1a5320f47b880c2d84132d70e1d0be19d6de486b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116211"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Testování F# částí knihoven v .NET Core pomocí příkazu dotnet test a nunit

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Požadavky

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo Editor kódu dle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-with-FSharp* , který bude obsahovat řešení.
V tomto novém adresáři spusťte následující příkaz, který vytvoří nový soubor řešení pro knihovnu tříd a testovací projekt:

```dotnetcli
dotnet new sln
```

Potom vytvořte adresář *MathService* . Následující osnova ukazuje strukturu adresářů a souborů, které jsou tak daleko:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Vytvořte *MathService* aktuální adresář a spusťte následující příkaz pro vytvoření zdrojového projektu:

```dotnetcli
dotnet new classlib -lang F#
```

Vytvoříte nefunkční implementaci služby Math Service:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Změňte adresář zpátky na adresář *testování částí s* adresářem-FSharp. Spuštěním následujícího příkazu přidejte projekt knihovny tříd do řešení:

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a>Vytváření testovacího projektu

Dále vytvořte adresář *MathService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Vytvořte adresář *MathService. Tests* pro aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:

```dotnetcli
dotnet new nunit -lang F#
```

Tím se vytvoří testovací projekt, který jako testovací rozhraní používá NUnit. Vygenerovaná šablona konfiguruje Test Runner v *MathServiceTests. fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new`v předchozím kroku jste přidali NUnit a testovací adaptér NUnit. Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.

Máte následující konečné rozložení řešení:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

Spusťte následující příkaz v adresáři *Unit-Testing-with-FSharp* :

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. Otevřete *UnitTest1. FS* a přidejte následující kód:

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

`[<TestFixture>]` Atribut označuje třídu, která obsahuje testy. `[<Test>]` Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner. Z adresáře *Unit-Testing-with-FSharp* spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz pro sestavení testů a knihovny tříd a poté spusťte testy. NUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

Tyto dva testy znázorňují základní a neúspěšné testy. `My test`projde a `Fail every time` dojde k chybě. Nyní vytvořte test pro `squaresOfOdds` metodu. `squaresOfOdds` Metoda vrací sekvenci čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence. Místo toho, abyste se pokusili zapsat všechny tyto funkce najednou, můžete iteračním vytvořit testy, které ověřují funkčnost. Provedení každého testovacího průchodu znamená vytvoření nezbytné funkce pro metodu.

Nejjednodušší test, který můžeme napsat, je zavolat `squaresOfOdds` se všemi sudými čísly, kde výsledek by měl být prázdná sekvence celých čísel.  Zde je tento test:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Všimněte si, `expected` že se sekvence převedla na seznam. NUnit Framework spoléhá na mnoho standardních typů .NET. Tato závislost znamená, že vaše veřejné rozhraní a očekávané výsledky <xref:System.Collections.ICollection> podporují spíše <xref:System.Collections.IEnumerable>než.

Když spustíte test, uvidíte, že test se nezdařil. Ještě jste nevytvořili implementaci. Proveďte tento test průchodu tak, že napíšete nejjednodušší kód v *knihovně Library. FS* v projektu MathService, který funguje:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

V adresáři *Unit-Testing-with-FSharp* spusťte `dotnet test` znovu. Příkaz spustí sestavení `MathService` pro`MathService.Tests` projekt a potom pro projekt. `dotnet test` Po sestavení obou projektů spustí vaše testy. Dva testy proběhnou nyní.

## <a name="completing-the-requirements"></a>Splnění požadavků

Teď, když jste udělali jeden test Pass, je čas zapsat další. Následující jednoduchý případ funguje s posloupností, jejíž pouze liché číslo `1`je. Číslo 1 je snazší, protože čtvercem 1 je 1. Následující test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Spuštění `dotnet test` selhalo v novém testu. Je nutné aktualizovat `squaresOfOdds` metodu pro zpracování tohoto nového testu. Chcete-li provést tento test, je nutné vyfiltrovat všechna sudá čísla mimo sekvenci. Můžete to udělat tak, že napíšete malou funkci filtru `Seq.filter`a použijete:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Všimněte si volání `Seq.toList`. Tím se vytvoří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.

K dispozici je ještě ještě jeden krok: čtverce každé liché číslice. Začněte zápisem nového testu:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Test můžete vyřešit tak, že provedete vyfiltrování filtrované sekvence pomocí operace mapování pro výpočet čtverce každého lichého čísla:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu. Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu. Vyrostli jste většinu času a úsilí při řešení cílů aplikace.
