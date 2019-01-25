---
title: příkaz DotNet úložiště
description: "'Dotnet Restore' příkaz uloží na zadaná sestavení do úložiště balíčků modulu runtime."
author: bleroy
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 58889039d117a2231cda693e4aca7790f018d1b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606748"
---
# <a name="dotnet-store"></a><span data-ttu-id="4958c-103">DotNet Restore</span><span class="sxs-lookup"><span data-stu-id="4958c-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="4958c-104">Název</span><span class="sxs-lookup"><span data-stu-id="4958c-104">Name</span></span>

<span data-ttu-id="4958c-105">`dotnet store` -Ukládá zadané sestavení v [úložiště balíčků modulu runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="4958c-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="4958c-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="4958c-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="4958c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4958c-107">Description</span></span>

<span data-ttu-id="4958c-108">`dotnet store` ukládá zadané sestavení v [úložiště balíčků modulu runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="4958c-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="4958c-109">Ve výchozím nastavení jsou sestavení optimalizované pro cílový modul runtime a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4958c-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="4958c-110">Další informace najdete v tématu [úložiště balíčků modulu runtime](../deploying/runtime-store.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="4958c-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="4958c-111">Požadované možnosti</span><span class="sxs-lookup"><span data-stu-id="4958c-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4958c-112">Určuje, [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4958c-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="4958c-113">*Souboru manifestu balíčku úložiště* je soubor XML, který obsahuje seznam balíčků pro uložení.</span><span class="sxs-lookup"><span data-stu-id="4958c-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="4958c-114">Formát souboru manifestu je kompatibilní s formátem SDK – vizuální styl projektu.</span><span class="sxs-lookup"><span data-stu-id="4958c-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="4958c-115">Ano, soubor projektu, který odkazuje na požadované balíčky je možné s `-m|--manifest` možnosti k uložení sestavení v úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4958c-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="4958c-116">Pokud chcete zadat více souborů manifestu, opakujte pro každý soubor možnost a cestu.</span><span class="sxs-lookup"><span data-stu-id="4958c-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="4958c-117">Například: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="4958c-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4958c-118">[Identifikátor modulu runtime](../rid-catalog.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="4958c-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="4958c-119">Volitelné možnosti</span><span class="sxs-lookup"><span data-stu-id="4958c-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="4958c-120">Určuje verzi .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4958c-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="4958c-121">Tato možnost umožňuje vybrat konkrétní verzi rozhraní framework verze mimo rámec určené `-f|--framework` možnost.</span><span class="sxs-lookup"><span data-stu-id="4958c-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="4958c-122">Zobrazí nápovědu informace.</span><span class="sxs-lookup"><span data-stu-id="4958c-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4958c-123">Určuje cestu k úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4958c-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="4958c-124">Pokud není zadán, použije se výchozí *ukládání* podadresář instalační adresář uživatelského profilu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4958c-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="4958c-125">Přeskočí fáze optimalizace.</span><span class="sxs-lookup"><span data-stu-id="4958c-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="4958c-126">Přeskočí symbol generace.</span><span class="sxs-lookup"><span data-stu-id="4958c-126">Skips symbol generation.</span></span> <span data-ttu-id="4958c-127">V současné době můžete generovat jenom symboly, s Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="4958c-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4958c-128">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="4958c-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4958c-129">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4958c-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="4958c-130">Pracovní adresář použité příkazem.</span><span class="sxs-lookup"><span data-stu-id="4958c-130">The working directory used by the command.</span></span> <span data-ttu-id="4958c-131">Pokud není zadán, použije *obj* podadresář aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="4958c-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="4958c-132">Příklady</span><span class="sxs-lookup"><span data-stu-id="4958c-132">Examples</span></span>

<span data-ttu-id="4958c-133">Balíčky zadané v Store *packages.csproj* soubor projektu pro .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="4958c-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="4958c-134">Balíčky zadané v Store *packages.csproj* bez optimalizace:</span><span class="sxs-lookup"><span data-stu-id="4958c-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="4958c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4958c-135">See also</span></span>

- [<span data-ttu-id="4958c-136">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="4958c-136">Runtime package store</span></span>](../deploying/runtime-store.md)
