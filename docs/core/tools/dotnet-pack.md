---
title: příkaz DotNet pack
description: Příkaz dotnet pack vytvoří balíčky NuGet pro projekt .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: 8faa99bf35d9802b16f951082b20644d45a939c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672123"
---
# <a name="dotnet-pack"></a><span data-ttu-id="c69b0-103">balíčku DotNet</span><span class="sxs-lookup"><span data-stu-id="c69b0-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c69b0-104">Name</span><span class="sxs-lookup"><span data-stu-id="c69b0-104">Name</span></span>

<span data-ttu-id="c69b0-105">`dotnet pack` -Sbalit kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="c69b0-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c69b0-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c69b0-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c69b0-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c69b0-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c69b0-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c69b0-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="c69b0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c69b0-109">Description</span></span>

<span data-ttu-id="c69b0-110">`dotnet pack` Příkaz sestaví projekt a vytváří balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="c69b0-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="c69b0-111">Výsledek tohoto příkazu je balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="c69b0-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="c69b0-112">Pokud `--include-symbols` možnost je k dispozici, je vytvořen jiný balíček, který obsahuje symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="c69b0-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="c69b0-113">Závislostí NuGet komprimovat komprimovaný objekt projektu jsou přidány do *souboru .nuspec* souboru, aby byly správně přeložit, při instalaci balíčku.</span><span class="sxs-lookup"><span data-stu-id="c69b0-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="c69b0-114">Odkazy typu projekt projekt nejsou zabaleny v projektu.</span><span class="sxs-lookup"><span data-stu-id="c69b0-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="c69b0-115">V současné době musí mít balíček na projekt, pokud máte závislosti projektu k projektu.</span><span class="sxs-lookup"><span data-stu-id="c69b0-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="c69b0-116">Ve výchozím nastavení `dotnet pack` nejprve sestaví projekt.</span><span class="sxs-lookup"><span data-stu-id="c69b0-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="c69b0-117">Pokud chcete-li toto chování vyhnout, předejte `--no-build` možnost.</span><span class="sxs-lookup"><span data-stu-id="c69b0-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="c69b0-118">Tato možnost je často užitečné pro scénáře sestavení kontinuální integrace (CI), kdy víte, že kód byl vytvořen dříve.</span><span class="sxs-lookup"><span data-stu-id="c69b0-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="c69b0-119">Můžete zadat vlastnosti nástroje MSBuild k `dotnet pack` příkaz pro proces balení.</span><span class="sxs-lookup"><span data-stu-id="c69b0-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="c69b0-120">Další informace najdete v tématu [vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="c69b0-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="c69b0-121">[Příklady](#examples) části ukazuje, jak pomocí přepínače -p MSBuild pro několik různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="c69b0-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="c69b0-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="c69b0-122">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="c69b0-123">Projekt se zabalit.</span><span class="sxs-lookup"><span data-stu-id="c69b0-123">The project to pack.</span></span> <span data-ttu-id="c69b0-124">Je buď cestu k [souboru csproj](csproj.md) nebo do adresáře.</span><span class="sxs-lookup"><span data-stu-id="c69b0-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="c69b0-125">Pokud není zadán, použije se výchozí do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c69b0-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="c69b0-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c69b0-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c69b0-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c69b0-127">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="c69b0-128">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="c69b0-128">Defines the build configuration.</span></span> <span data-ttu-id="c69b0-129">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-129">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="c69b0-130">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="c69b0-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="c69b0-131">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="c69b0-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c69b0-132">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c69b0-132">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="c69b0-133">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="c69b0-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="c69b0-134">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="c69b0-135">Vygeneruje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-135">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="c69b0-136">Nelze sestavit projekt před balení.</span><span class="sxs-lookup"><span data-stu-id="c69b0-136">Doesn't build the project before packing.</span></span> <span data-ttu-id="c69b0-137">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="c69b0-137">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="c69b0-138">Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.</span><span class="sxs-lookup"><span data-stu-id="c69b0-138">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="c69b0-139">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c69b0-139">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c69b0-140">Umístí sestavené balíčky v adresáři uvedeném.</span><span class="sxs-lookup"><span data-stu-id="c69b0-140">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c69b0-141">Určuje cílový modul runtime pro obnovování balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="c69b0-141">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="c69b0-142">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="c69b0-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="c69b0-143">Nastaví příznak nacházet v balíčku.</span><span class="sxs-lookup"><span data-stu-id="c69b0-143">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="c69b0-144">Další informace najdete v tématu [Blog k .NET: .NET 4.5.1 aktualizace zabezpečení Microsoftu podporuje pro NuGet knihovny .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="c69b0-144">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="c69b0-145">Definuje hodnotu pro `$(VersionSuffix)` vlastnost MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="c69b0-145">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c69b0-146">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="c69b0-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c69b0-147">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

> [!NOTE]
> <span data-ttu-id="c69b0-148">Webové projekty nejsou packable ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c69b0-148">Web projects aren't packable by default.</span></span> <span data-ttu-id="c69b0-149">Pokud chcete přepsat výchozí chování, přidejte následující vlastnost, která má vaše *.csproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="c69b0-149">To override the default behavior, add the following property to your *.csproj* file:</span></span>
>
> ```xml
> <PropertyGroup>
>    <IsPackable>true</IsPackable>
> </PropertyGroup>
> ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c69b0-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c69b0-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="c69b0-151">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="c69b0-151">Defines the build configuration.</span></span> <span data-ttu-id="c69b0-152">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c69b0-153">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c69b0-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="c69b0-154">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="c69b0-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="c69b0-155">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="c69b0-156">Vygeneruje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="c69b0-157">Nelze sestavit projekt před balení.</span><span class="sxs-lookup"><span data-stu-id="c69b0-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c69b0-158">Umístí sestavené balíčky v adresáři uvedeném.</span><span class="sxs-lookup"><span data-stu-id="c69b0-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="c69b0-159">Nastaví příznak nacházet v balíčku.</span><span class="sxs-lookup"><span data-stu-id="c69b0-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="c69b0-160">Další informace najdete v tématu [Blog k .NET: .NET 4.5.1 aktualizace zabezpečení Microsoftu podporuje pro NuGet knihovny .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="c69b0-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="c69b0-161">Definuje hodnotu pro `$(VersionSuffix)` vlastnost MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="c69b0-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c69b0-162">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="c69b0-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c69b0-163">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c69b0-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c69b0-164">Příklady</span><span class="sxs-lookup"><span data-stu-id="c69b0-164">Examples</span></span>

* <span data-ttu-id="c69b0-165">Sada projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="c69b0-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="c69b0-166">Balíček `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="c69b0-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="c69b0-167">Zabalit projekt v aktuálním adresáři a umístí výsledný balíčky do `nupkgs` složky:</span><span class="sxs-lookup"><span data-stu-id="c69b0-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="c69b0-168">Sbalení projekt v aktuálním adresáři, do `nupkgs` složky a přeskočit krok sestavení:</span><span class="sxs-lookup"><span data-stu-id="c69b0-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="c69b0-169">S projektem verze příponu nakonfigurovaná jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v *.csproj* souborů, aktuální projekt pack a aktualizovaných výsledný verze balíčku s danou příponou:</span><span class="sxs-lookup"><span data-stu-id="c69b0-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="c69b0-170">Nastavte verzi balíčku `2.1.0` s `PackageVersion` vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="c69b0-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="c69b0-171">Projekt pro konkrétní Pack [Cílová architektura](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="c69b0-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="c69b0-172">Zabalte projektu a použití konkrétního modulu runtime (Windows 10) pro operaci obnovení (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="c69b0-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="c69b0-173">Pack projekt pomocí [soubor souboru .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="c69b0-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
