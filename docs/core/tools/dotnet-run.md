---
title: Spusťte příkaz DotNet
description: Spusťte příkaz dotnet poskytuje vhodnou možnost ke spuštění aplikace ze zdrojového kódu.
ms.date: 05/29/2018
ms.openlocfilehash: 489429e2371c807e09f9fb8c2de6f96d091edc6d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632010"
---
# <a name="dotnet-run"></a><span data-ttu-id="9b30e-103">Spusťte příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="9b30e-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9b30e-104">Name</span><span class="sxs-lookup"><span data-stu-id="9b30e-104">Name</span></span>

<span data-ttu-id="9b30e-105">`dotnet run` -Spuštění zdrojový kód bez žádné explicitní kompilace a spuštění příkazů.</span><span class="sxs-lookup"><span data-stu-id="9b30e-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9b30e-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="9b30e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9b30e-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9b30e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9b30e-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9b30e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9b30e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9b30e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="9b30e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9b30e-110">Description</span></span>

<span data-ttu-id="9b30e-111">`dotnet run` Příkaz poskytuje vhodnou možnost ke spuštění aplikace ze zdrojového kódu pomocí jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="9b30e-112">To je užitečné pro rychlé iterativní vývoj z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9b30e-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="9b30e-113">Příkaz závisí [ `dotnet build` ](dotnet-build.md) příkaz sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="9b30e-114">Všechny požadavky pro sestavení, jako je projekt, je potřeba obnovit nejdřív použijte k `dotnet run` také.</span><span class="sxs-lookup"><span data-stu-id="9b30e-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="9b30e-115">Výstupní soubory jsou zapsány do výchozího umístění, což je `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="9b30e-116">Například pokud máte `netcoreapp2.1` aplikace a spusťte `dotnet run`, výstup je umístěn v `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-116">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="9b30e-117">Soubory jsou přepsány, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="9b30e-117">Files are overwritten as needed.</span></span> <span data-ttu-id="9b30e-118">Dočasné soubory jsou umístěny v `obj` adresáře.</span><span class="sxs-lookup"><span data-stu-id="9b30e-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="9b30e-119">Pokud projekt určuje více platforem, provádí `dotnet run` způsobí chybu, pokud `-f|--framework <FRAMEWORK>` možnost slouží k určení rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="9b30e-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="9b30e-120">`dotnet run` Příkaz se používá v rámci projektů nejsou vytvořená sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b30e-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="9b30e-121">Pokud se snažíte místo něj spustí aplikace závisí na architektuře knihovny DLL, je nutné použít [dotnet](dotnet.md) bez příkaz.</span><span class="sxs-lookup"><span data-stu-id="9b30e-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="9b30e-122">Chcete-li například spustit `myapp.dll`, použijte:</span><span class="sxs-lookup"><span data-stu-id="9b30e-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="9b30e-123">Další informace o `dotnet` ovladač, najdete v článku [.NET Core příkazového řádku nástroje (CLI)](index.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="9b30e-124">Ke spuštění aplikace, `dotnet run` příkaz řeší závislosti aplikace, které se nachází mimo sdílený modul runtime z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="9b30e-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="9b30e-125">Protože ho používá uložené v mezipaměti závislosti, se nedoporučuje používat `dotnet run` ke spouštění aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9b30e-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="9b30e-126">Místo toho [vytvořit nasazení](../deploying/index.md) pomocí [ `dotnet publish` ](dotnet-publish.md) příkazů a nasaďte publikovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="9b30e-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="9b30e-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9b30e-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9b30e-128">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9b30e-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="9b30e-129">Odděluje citaci argumenty `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9b30e-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9b30e-130">Všechny argumenty za tento oddělovač jsou předány do aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="9b30e-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9b30e-131">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b30e-131">Defines the build configuration.</span></span> <span data-ttu-id="9b30e-132">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9b30e-133">Vytvoří a spustí aplikaci pomocí zadaného [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b30e-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9b30e-134">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="9b30e-135">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9b30e-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9b30e-136">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="9b30e-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9b30e-137">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9b30e-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="9b30e-138">Název spuštění profilu (pokud existuje) má použít při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b30e-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="9b30e-139">Profily spuštění, které jsou definovány v *launchSettings.json* a souborů jsou běžně označována jako `Development`, `Staging`, a `Production`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="9b30e-140">Další informace najdete v tématu [práce v různých prostředích](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="9b30e-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="9b30e-141">Nelze sestavit projekt před provozováním.</span><span class="sxs-lookup"><span data-stu-id="9b30e-141">Doesn't build the project before running.</span></span> <span data-ttu-id="9b30e-142">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="9b30e-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9b30e-143">Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="9b30e-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="9b30e-144">Nebude se pokusí použít *launchSettings.json* konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b30e-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="9b30e-145">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9b30e-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="9b30e-146">Určuje cestu k souboru projektu pro spuštění (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="9b30e-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="9b30e-147">Pokud není zadán, použije se výchozí do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="9b30e-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9b30e-148">Určuje cílový modul runtime pro obnovování balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="9b30e-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9b30e-149">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9b30e-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9b30e-150">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9b30e-151">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9b30e-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9b30e-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="9b30e-153">Odděluje citaci argumenty `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9b30e-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9b30e-154">Všechny argumenty za tento oddělovač jsou předány do aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="9b30e-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9b30e-155">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b30e-155">Defines the build configuration.</span></span> <span data-ttu-id="9b30e-156">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9b30e-157">Vytvoří a spustí aplikaci pomocí zadaného [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b30e-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9b30e-158">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="9b30e-159">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9b30e-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9b30e-160">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="9b30e-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9b30e-161">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9b30e-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="9b30e-162">Název spuštění profilu (pokud existuje) má použít při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b30e-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="9b30e-163">Profily spuštění, které jsou definovány v *launchSettings.json* a souborů jsou běžně označována jako `Development`, `Staging`, a `Production`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="9b30e-164">Další informace najdete v tématu [práce v různých prostředích](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="9b30e-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="9b30e-165">Nelze sestavit projekt před provozováním.</span><span class="sxs-lookup"><span data-stu-id="9b30e-165">Doesn't build the project before running.</span></span> <span data-ttu-id="9b30e-166">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="9b30e-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9b30e-167">Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="9b30e-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="9b30e-168">Nebude se pokusí použít *launchSettings.json* konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b30e-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="9b30e-169">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9b30e-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="9b30e-170">Určuje cestu k souboru projektu pro spuštění (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="9b30e-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="9b30e-171">Pokud není zadán, použije se výchozí do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="9b30e-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9b30e-172">Určuje cílový modul runtime pro obnovování balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="9b30e-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9b30e-173">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9b30e-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9b30e-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9b30e-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="9b30e-175">Odděluje citaci argumenty `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9b30e-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9b30e-176">Všechny argumenty za tento oddělovač jsou předány do aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="9b30e-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9b30e-177">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b30e-177">Defines the build configuration.</span></span> <span data-ttu-id="9b30e-178">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9b30e-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9b30e-179">Vytvoří a spustí aplikaci pomocí zadaného [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b30e-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9b30e-180">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="9b30e-181">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9b30e-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="9b30e-182">Určuje cestu a název souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9b30e-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="9b30e-183">(Viz poznámky). Pokud není zadán, použije se výchozí do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="9b30e-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9b30e-184">Použít cestu a název souboru projektu se `-p|--project` možnost.</span><span class="sxs-lookup"><span data-stu-id="9b30e-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="9b30e-185">Zabraňuje Regrese v rozhraní příkazového řádku .NET Core SDK poskytuje cestu ke složce 1.x.</span><span class="sxs-lookup"><span data-stu-id="9b30e-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="9b30e-186">Další informace o tomto problému najdete v tématu [dotnet spustit -p, nelze spustit projekt (.NET/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="9b30e-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="9b30e-187">Příklady</span><span class="sxs-lookup"><span data-stu-id="9b30e-187">Examples</span></span>

<span data-ttu-id="9b30e-188">Spusťte projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="9b30e-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="9b30e-189">Spusťte zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="9b30e-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="9b30e-190">Spusťte projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, od prázdnou `--` možnost se používá):</span><span class="sxs-lookup"><span data-stu-id="9b30e-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="9b30e-191">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři jenom minimální výstupní a spuštění projektu: (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="9b30e-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
