---
title: 'Kurz: Vytvoření řešení .NET Core v macOS pomocí Visual Studio Code'
description: Tento dokument popisuje kroky a pracovní postup pro vytvoření řešení .NET Core pomocí Visual Studio Code.
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: 5df43ae235b9fd901a65f7f8898bec67e24de682
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117368"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Kurz: Vytvoření řešení .NET Core v macOS pomocí Visual Studio Code

Tento dokument popisuje kroky a pracovní postup pro vytvoření řešení .NET Core pro macOS. Naučte se vytvářet projekty, testy jednotek, používat ladicí nástroje a začlenit knihovny třetích stran přes [NuGet](https://www.nuget.org/).

> [!NOTE]
> Tento článek používá [Visual Studio Code](https://code.visualstudio.com) v MacOS.

## <a name="prerequisites"></a>Požadavky

Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download). .NET Core SDK zahrnuje nejnovější verzi rozhraní .NET Core Framework a modulu runtime.

Nainstalujte [Visual Studio Code](https://code.visualstudio.com). V průběhu tohoto článku nainstalujete také rozšíření Visual Studio Code, která zlepšují vývojové prostředí .NET Core.

Visual Studio Code C# rozšíření můžete nainstalovat otevřením Visual Studio Code a stisknutím <kbd>klávesy F1</kbd> otevřete paletu Visual Studio Code. Zadáním **EXT Install** zobrazíte seznam rozšíření. Vyberte C# rozšíření. Pro aktivaci rozšíření restartujte Visual Studio Code. Další informace najdete v dokumentaci k [rozšíření C# Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Začínáme

V tomto kurzu vytvoříte tři projekty: projekt knihovny, testy pro daný projekt knihovny a konzolovou aplikaci, která využívá knihovnu. Zdroj pro toto téma můžete [Zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) v úložišti dotnet/Samples na GitHubu. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Spusťte Visual Studio Code. Stiskněte klávesu <kbd>CTRL</kbd> + <kbd>\`</kbd> (znaková uvozovka nebo znak zaškrtnutí) nebo vyberte **Zobrazit > integrovaného terminálu** z nabídky pro otevření vloženého terminálu v Visual Studio Code. Můžete otevřít externí prostředí pomocí Průzkumníka **otevřít v příkazu příkazového řádku** (**otevřít v terminálu** na Macu nebo Linux), pokud dáváte přednost práci mimo Visual Studio Code.

Začněte vytvořením souboru řešení, který slouží jako kontejner pro jeden nebo více projektů .NET Core. V terminálu spusťte [`dotnet new`](../tools/dotnet-new.md) příkaz pro vytvoření nového řešení *zlatý. sln* uvnitř nové složky s názvem *zlatá*:

```dotnetcli
dotnet new sln -o golden
```

Přejděte do nové *zlaté* složky a spusťte následující příkaz pro vytvoření projektu knihovny, který ve složce *knihovny* vytvoří dva soubory,*Library. csproj* a *Class1.cs*:

```dotnetcli
dotnet new classlib -o library
```

Spusťte příkaz pro přidání nově vytvořeného projektu *Library. csproj* do řešení: [`dotnet sln`](../tools/dotnet-sln.md)

```dotnetcli
dotnet sln add library/library.csproj
```

Soubor *Library. csproj* obsahuje následující informace:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Naše metody knihovny serializovat a deserializovat objekty ve formátu JSON. Pro podporu serializace a deserializace JSON přidejte odkaz na `Newtonsoft.Json` balíček NuGet. `dotnet add` Příkaz přidá nové položky do projektu. Chcete-li přidat odkaz na balíček NuGet, použijte [`dotnet add package`](../tools/dotnet-add-package.md) příkaz a zadejte název balíčku:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Tím se `Newtonsoft.Json` přidá a jeho závislosti do projektu knihovny. Případně ručně upravte soubor *Library. csproj* a přidejte následující uzel:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Execute [`dotnet restore`](../tools/dotnet-restore.md)([Viz poznámku](#dotnet-restore-note)), která obnoví závislosti a vytvoří složku *obj* v *knihovně* se třemi soubory, včetně souboru *Project. assets. JSON* :

```dotnetcli
dotnet restore
```

Ve složce *Library (knihovna* ), přejmenujte soubor *Class1.cs* na *Thing.cs*. Nahraďte kód následujícím kódem:

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

Třída obsahuje jednu veřejnou `Get`metodu, která vrací součet dvou čísel, ale provede převod součtu na řetězec a jeho deserializaci na celé číslo. `Thing` To C# využívá řadu moderních funkcí, [ `using static` ](../../csharp/language-reference/keywords/using-static.md)jako jsou například direktivy, [členy Expression-těle](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)a [interpolace řetězců](../../csharp/language-reference/tokens/interpolated.md).

Sestavte knihovnu pomocí [`dotnet build`](../tools/dotnet-build.md) příkazu. Tím se vytvoří soubor *Library. dll* v rámci *zlaté/knihovny/přihrádky/ladění/netstandard 1.4*:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Vytvořte projekt testu

Sestavte projekt testů pro knihovnu. Ze *zlaté* složky vytvořte nový testovací projekt:

```dotnetcli
dotnet new xunit -o test-library
```

Přidejte testovací projekt do řešení:

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Přidejte projekt odkaz na knihovnu, kterou jste vytvořili v předchozí části, aby kompilátor mohl najít a použít projekt knihovny. [`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Případně ručně upravte soubor *test-Library. csproj* a přidejte následující uzel:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Teď, když jsou závislosti správně nakonfigurované, vytvořte testy pro vaši knihovnu. Otevřete *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Všimněte si, že hodnota 42 se nerovná 19 + 23 (nebo 42) při prvním vytvoření testu jednotek (`Assert.NotEqual`), což selže. Důležitým krokem při sestavování testů jednotek je vytvoření testu pro jeho první selhání a potvrzení jeho logiky.

Ze *zlaté* složky spusťte následující příkazy:

```dotnetcli
dotnet restore 
dotnet test test-library/test-library.csproj
```

Tyto příkazy rekurzivně vyhledají všechny projekty pro obnovení závislostí, sestavují je a aktivují xUnit Test Runner pro spuštění testů. Jeden test se nezdařil, jak očekáváte.

Upravte soubor *UnitTest1.cs* a změňte kontrolní výraz z `Assert.NotEqual` na. `Assert.Equal` Spusťte následující příkaz ze *zlaté* složky a spusťte test znovu, který projde tímto časem:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Vytvoření konzolové aplikace

Aplikace konzoly, kterou vytvoříte pomocí následujících kroků, provede závislost na projektu knihovny, který jste vytvořili dříve, a volá jeho metodu Library při spuštění. Pomocí tohoto modelu vývoje vidíte, jak vytvořit opakovaně použitelné knihovny pro více projektů.

Vytvořit novou konzolovou aplikaci ze *zlaté* složky:

```dotnetcli
dotnet new console -o app
```

Přidejte projekt konzolové aplikace do řešení:

```dotnetcli
dotnet sln add app/app.csproj
```

Vytvořte závislost na knihovně spuštěním `dotnet add reference` příkazu:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Spusťte `dotnet restore` ([Viz poznámku](#dotnet-restore-note)) a obnovte závislosti tří projektů v řešení. Otevřete *program.cs* a nahraďte obsah `Main` metody následujícím řádkem:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Do horní `using` části souboru *program.cs* přidejte dvě direktivy:

```csharp
using static System.Console;
using Library;
```

Spuštěním následujícího `dotnet run` příkazu spusťte spustitelný soubor, `-p` kde možnost `dotnet run` určuje projekt pro hlavní aplikaci. Aplikace vytvoří řetězec "odpověď je 42".

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Ladění aplikace

Nastavte zarážku na `WriteLine` příkaz `Main` v metodě. Provedete to tak, že stisknete klávesu <kbd>F9</kbd> , když se `WriteLine` ukazatel myši nachází na řádku, nebo kliknete myší na levém okraji na řádku, kde chcete nastavit zarážku. Na okraji vedle řádku kódu se zobrazí červené kolečko. Při dosažení zarážky se spuštění kódu zastaví *před* provedením řádku zarážky.

Otevřete kartu ladicí program výběrem ikony ladění na panelu nástrojů Visual Studio Code a výběrem možnosti **Zobrazit > ladění** na panelu nabídek nebo pomocí klávesové zkratky <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:

![Ladicí program Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

Stisknutím tlačítka Přehrát spusťte aplikaci v ladicím programu. Aplikace se spustí a spustí se na zarážku, kde se zastaví. Zajistěte `Get` krok do metody a ujistěte se, že jste předali správné argumenty. Potvrďte, že odpověď je 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
