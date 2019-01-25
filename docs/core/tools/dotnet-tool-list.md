---
title: příkaz listovat nástrojů DotNet
description: Příkaz dotnet nástroj seznam uvádí zadaného nástroje rozhraní .NET Core globální z vašeho počítače.
ms.date: 05/29/2018
ms.openlocfilehash: d3ff7fc90faf6ede3f7de0d5af5112c77ca140db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712914"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="0f380-103">seznam nástrojů DotNet</span><span class="sxs-lookup"><span data-stu-id="0f380-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="0f380-104">Název</span><span class="sxs-lookup"><span data-stu-id="0f380-104">Name</span></span>

<span data-ttu-id="0f380-105">`dotnet tool list` -Obsahuje seznam všech [globální nástroje .NET Core](global-tools.md) aktuálně nainstalované ve výchozím adresáři na svém počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="0f380-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0f380-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0f380-106">Synopsis</span></span>

```console
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="0f380-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0f380-107">Description</span></span>

<span data-ttu-id="0f380-108">`dotnet tool list` Příkaz poskytuje způsob, jak můžete vypsat všechny globální nástroje .NET Core nainstalovat celou uživatel na svém počítači (profil aktuálního uživatele) nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="0f380-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="0f380-109">Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="0f380-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="0f380-110">Použití příkazu seznam, buď musíte zadat, že chcete zobrazit všechny nástroje celou uživatele pomocí `--global` možnost nebo zadat vlastní cesty pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="0f380-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="0f380-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0f380-111">Options</span></span>

`-g|--global`

<span data-ttu-id="0f380-112">Vypíše nástroje globální uživatelské úrovni.</span><span class="sxs-lookup"><span data-stu-id="0f380-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="0f380-113">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="0f380-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="0f380-114">Pokud nezadáte tuto možnost, je nutné zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="0f380-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="0f380-115">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0f380-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="0f380-116">Určuje vlastní umístění, kde najít globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="0f380-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="0f380-117">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="0f380-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="0f380-118">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="0f380-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="0f380-119">Pokud nezadáte tuto možnost, je nutné zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="0f380-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="0f380-120">Příklady</span><span class="sxs-lookup"><span data-stu-id="0f380-120">Examples</span></span>

<span data-ttu-id="0f380-121">Uvádí všechny nainstalované nástroje pro globální uživatelské úrovni na svém počítači (profil aktuálního uživatele):</span><span class="sxs-lookup"><span data-stu-id="0f380-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="0f380-122">Vypíše globální nástroje z konkrétní složky Windows:</span><span class="sxs-lookup"><span data-stu-id="0f380-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="0f380-123">Vypíše globální nástroje z konkrétní složky Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="0f380-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="0f380-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f380-124">See also</span></span>

- [<span data-ttu-id="0f380-125">.NET Core Global Tools</span><span class="sxs-lookup"><span data-stu-id="0f380-125">.NET Core Global Tools</span></span>](global-tools.md)
