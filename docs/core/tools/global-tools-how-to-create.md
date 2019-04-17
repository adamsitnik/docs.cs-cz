---
title: Vytvoření globální nástroje .NET Core
description: Popisuje, jak vytvořit globální nástroj. Nástroj globální je konzolová aplikace, která se instaluje prostřednictvím rozhraní příkazového řádku .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 3d0a64d0473f51d73892cd40633e2982c1130469
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612664"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="af304-104">Vytvoření globální nástroje .NET Core pomocí rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="af304-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="af304-105">V tomto článku se naučíte, jak vytvořit a balíček globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="af304-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="af304-106">Rozhraní příkazového řádku .NET Core umožňuje vytvořit konzolovou aplikaci jako globální nástroj, který ostatní snadno nainstalovat a spustit.</span><span class="sxs-lookup"><span data-stu-id="af304-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="af304-107">Globální nástroje .NET core jsou balíčky NuGet, které jsou instalovány z rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="af304-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="af304-108">Další informace o těchto nástrojích, globální, naleznete v tématu [globální nástroje .NET Core přehled](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="af304-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="af304-109">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="af304-109">Create a project</span></span>

<span data-ttu-id="af304-110">Tento článek používá rozhraní příkazového řádku .NET Core k vytváření a správě projektu.</span><span class="sxs-lookup"><span data-stu-id="af304-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="af304-111">Náš příklad nástroj bude konzolovou aplikaci, která generuje bot ASCII a vytiskne zprávu.</span><span class="sxs-lookup"><span data-stu-id="af304-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="af304-112">Nejprve vytvořte novou konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="af304-112">First, create a new .NET Core Console Application.</span></span>

```console
dotnet new console -o botsay
```

<span data-ttu-id="af304-113">Přejděte `botsay` adresář vytvořený v předchozím příkazu.</span><span class="sxs-lookup"><span data-stu-id="af304-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="af304-114">Přidejte kód</span><span class="sxs-lookup"><span data-stu-id="af304-114">Add the code</span></span>

<span data-ttu-id="af304-115">Otevřít `Program.cs` souboru v oblíbeném textovém editoru, jako například `vim` nebo [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="af304-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="af304-116">Přidejte následující `using` směrnice do horní části souboru, to pomáhá zkrátit kódu zobrazíte informace o verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="af304-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="af304-117">Dále přejděte dolů `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="af304-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="af304-118">Metoda nahraďte následující kód pro zpracování argumentů příkazového řádku pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="af304-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="af304-119">Pokud byly předány žádné argumenty, zobrazí se krátký nápovědu.</span><span class="sxs-lookup"><span data-stu-id="af304-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="af304-120">V opačném případě všechny tyto argumenty jsou transformuje na řetězec a vytisknout s roboty.</span><span class="sxs-lookup"><span data-stu-id="af304-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

```csharp
static void Main(string[] args)
{
    if (args.Length == 0)
    {
        var versionString = Assembly.GetEntryAssembly()
                                .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                .InformationalVersion
                                .ToString();

        Console.WriteLine($"botsay v{versionString}");
        Console.WriteLine("-------------");
        Console.WriteLine("\nUsage:");
        Console.WriteLine("  botsay <message>");
        return;
    }

    ShowBot(string.Join(' ', args));
}
```

### <a name="create-the-bot"></a><span data-ttu-id="af304-121">Vytvořte robota</span><span class="sxs-lookup"><span data-stu-id="af304-121">Create the bot</span></span>

<span data-ttu-id="af304-122">V dalším kroku přidejte novou metodu s názvem `ShowBot` , která použije parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="af304-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="af304-123">Tato metoda vytiskne zprávu a ASCII bot.</span><span class="sxs-lookup"><span data-stu-id="af304-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="af304-124">Kód ASCII bot byla získána z [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) vzorku.</span><span class="sxs-lookup"><span data-stu-id="af304-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

```csharp
static void ShowBot(string message)
{
    string bot = $"\n        {message}";
    bot += @"
    __________________
                      \
                       \
                          ....
                          ....'
                           ....
                        ..........
                    .............'..'..
                 ................'..'.....
               .......'..........'..'..'....
              ........'..........'..'..'.....
             .'....'..'..........'..'.......'.
             .'..................'...   ......
             .  ......'.........         .....
             .    _            __        ......
            ..    #            ##        ......
           ....       .                 .......
           ......  .......          ............
            ................  ......................
            ........................'................
           ......................'..'......    .......
        .........................'..'.....       .......
     ........    ..'.............'..'....      ..........
   ..'..'...      ...............'.......      ..........
  ...'......     ...... ..........  ......         .......
 ...........   .......              ........        ......
.......        '...'.'.              '.'.'.'         ....
.......       .....'..               ..'.....
   ..       ..........               ..'........
          ............               ..............
         .............               '..............
        ...........'..              .'.'............
       ...............              .'.'.............
      .............'..               ..'..'...........
      ...............                 .'..............
       .........                        ..............
        .....
";
    Console.WriteLine(bot);
}
```

### <a name="test-the-tool"></a><span data-ttu-id="af304-125">Testovací nástroje</span><span class="sxs-lookup"><span data-stu-id="af304-125">Test the tool</span></span>

<span data-ttu-id="af304-126">Spusťte projekt a zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="af304-126">Run the project and see the output.</span></span> <span data-ttu-id="af304-127">Vyzkoušejte tyto odchylky z příkazového řádku, pokud chcete zobrazit odlišné výsledky:</span><span class="sxs-lookup"><span data-stu-id="af304-127">Try these variations of the command-line to see different results:</span></span>

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="af304-128">Všechny argumenty po `--` oddělovače jsou předány do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="af304-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="setup-the-global-tool"></a><span data-ttu-id="af304-129">Instalační program nástroje global</span><span class="sxs-lookup"><span data-stu-id="af304-129">Setup the global tool</span></span>

<span data-ttu-id="af304-130">Před aktualizací Service pack a distribuce aplikace jako globální nástroj, budete muset upravit soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="af304-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="af304-131">Otevřít `botsay.csproj` a přidejte tři nové uzly XML k `<Project><PropertyGroup>` uzlu:</span><span class="sxs-lookup"><span data-stu-id="af304-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`\
<span data-ttu-id="af304-132">[POVINNÉ] Označuje, že aplikace se zabalí pro instalaci jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="af304-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`\
<span data-ttu-id="af304-133">[VOLITELNÉ] Alternativní název pro nástroj, jinak název příkazu pro nástroj bude mít název souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="af304-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="af304-134">Může mít několik nástrojů v balíčku, při výběru že jedinečný a popisný název pomáhá odlišil od jiných nástrojů ve stejném balíku.</span><span class="sxs-lookup"><span data-stu-id="af304-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`\
<span data-ttu-id="af304-135">[VOLITELNÉ] Kde se budou vytvářet balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="af304-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="af304-136">Balíček NuGet je globální nástroje .NET Core CLI používá k instalaci nástroj.</span><span class="sxs-lookup"><span data-stu-id="af304-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

<span data-ttu-id="af304-137">I když `<PackageOutputPath>` je volitelný, jeho použití v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="af304-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="af304-138">Ujistěte se, že ji nastavíte: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span><span class="sxs-lookup"><span data-stu-id="af304-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="af304-139">Dále vytvořte balíček NuGet pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="af304-139">Next, create a NuGet package for your application.</span></span>

```console
dotnet pack
```

<span data-ttu-id="af304-140">`botsay.1.0.0.nupkg` Vytvoří soubor ve složce identifikován `<PackageOutputPath>` hodnotu XML z `botsay.csproj` soubor, který v tomto příkladu je `./nupkg` složky.</span><span class="sxs-lookup"><span data-stu-id="af304-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="af304-141">To usnadňuje instalaci a testování.</span><span class="sxs-lookup"><span data-stu-id="af304-141">This makes it easy to install and test.</span></span> <span data-ttu-id="af304-142">Pokud chcete uvolnit nástroj veřejně, nahrajte ho do <https://www.nuget.org>.</span><span class="sxs-lookup"><span data-stu-id="af304-142">When you want to release a tool publicly, upload it to <https://www.nuget.org>.</span></span> <span data-ttu-id="af304-143">Až nástroj je k dispozici na webu NuGet, vývojáři můžete provést instalaci celou uživatele pomocí nástroje `--global` možnost [instalace nástrojů dotnet](dotnet-tool-install.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="af304-143">Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="af304-144">Teď, když máte balíček, nainstalujte nástroj z tohoto balíčku:</span><span class="sxs-lookup"><span data-stu-id="af304-144">Now that you have a package, install the tool from that package:</span></span>

```console
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="af304-145">`--add-source` Určuje parametr příkazového řádku .NET Core pro dočasně použití `./nupkg` složky (naše `<PackageOutputPath>` složky) jako další zdroj datového kanálu pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="af304-145">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="af304-146">Další informace o instalaci nástrojů pro globální, naleznete v tématu [globální nástroje .NET Core přehled](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="af304-146">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="af304-147">Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkazu používaný k volání nástroje a verze nainstalovaná, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="af304-147">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="af304-148">Nyní byste měli být schopni zadejte `botsay` a získat odpověď z nástroje.</span><span class="sxs-lookup"><span data-stu-id="af304-148">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="af304-149">Pokud byla instalace úspěšná, ale nemůžete použít `botsay` příkazu, budete muset otevřít nové zařízení k aktualizaci cesty.</span><span class="sxs-lookup"><span data-stu-id="af304-149">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="af304-150">Odeberte nástroj</span><span class="sxs-lookup"><span data-stu-id="af304-150">Remove the tool</span></span>

<span data-ttu-id="af304-151">Jakmile budete mít experimentování s nástroji, můžete ho odebrat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="af304-151">Once you're done experimenting with the tool, you can remove it with the following command:</span></span>

```console
dotnet tool uninstall -g botsay
```
