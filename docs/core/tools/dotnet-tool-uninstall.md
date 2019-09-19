---
title: příkaz dotnet nástroje pro odinstalaci
description: Příkaz pro odinstalaci nástroje dotnet odinstaluje zadaný globální nástroj .NET Core z počítače.
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117541"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="5e855-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="5e855-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="5e855-104">Name</span><span class="sxs-lookup"><span data-stu-id="5e855-104">Name</span></span>

<span data-ttu-id="5e855-105">`dotnet tool uninstall`– Odinstaluje zadaný [globální nástroj .NET Core](global-tools.md) z počítače.</span><span class="sxs-lookup"><span data-stu-id="5e855-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5e855-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5e855-106">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="5e855-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5e855-107">Description</span></span>

<span data-ttu-id="5e855-108">`dotnet tool uninstall` Příkaz nabízí způsob, jak odinstalovat globální nástroje .NET Core z počítače.</span><span class="sxs-lookup"><span data-stu-id="5e855-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="5e855-109">Chcete-li použít příkaz, musíte určit, že chcete odebrat nástroj pro všechny uživatele pomocí `--global` možnosti nebo zadat cestu k umístění nástroje `--tool-path` pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="5e855-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="5e855-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="5e855-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5e855-111">Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core pro odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="5e855-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="5e855-112">Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="5e855-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="5e855-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5e855-113">Options</span></span>

`-g|--global`

<span data-ttu-id="5e855-114">Určuje, že nástroj, který se má odebrat, pochází z instalace v rámci uživatele.</span><span class="sxs-lookup"><span data-stu-id="5e855-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="5e855-115">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="5e855-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="5e855-116">Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="5e855-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="5e855-117">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="5e855-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="5e855-118">Určuje umístění, kam se má globální nástroj odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="5e855-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="5e855-119">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="5e855-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="5e855-120">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="5e855-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="5e855-121">Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="5e855-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="5e855-122">Příklady</span><span class="sxs-lookup"><span data-stu-id="5e855-122">Examples</span></span>

<span data-ttu-id="5e855-123">Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :</span><span class="sxs-lookup"><span data-stu-id="5e855-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="5e855-124">Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z určité složky systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5e855-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="5e855-125">Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétní složky Linux/MacOS:</span><span class="sxs-lookup"><span data-stu-id="5e855-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="5e855-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e855-126">See also</span></span>

- [<span data-ttu-id="5e855-127">Globální nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e855-127">.NET Core Global Tools</span></span>](global-tools.md)
