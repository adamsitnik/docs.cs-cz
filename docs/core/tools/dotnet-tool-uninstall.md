---
title: odinstalační příkaz DotNet
description: Příkaz odinstalovat nástroj dotnet odinstaluje zadané globální nástroji .NET Core z vašeho počítače.
ms.date: 05/29/2018
ms.openlocfilehash: 4d53d305131e3399ab5d9c19f9319f3ba3544c19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648552"
---
# <a name="dotnet-tool-uninstall"></a>Odinstalace nástrojů DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet tool uninstall` -Odinstaluje zadané [globální nástroje .NET Core](global-tools.md) z vašeho počítače.

## <a name="synopsis"></a>Souhrn

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool uninstall` Příkaz poskytuje způsob, jak vás k odinstalaci globální nástroje .NET Core z vašeho počítače. Použití příkazu, buď musíte zadat, že chcete odebrat uživatele celou nástroj pomocí `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje globální nástroji .NET Core pro odinstalaci. Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkazu.

## <a name="options"></a>Možnosti

`-g|--global`

Určuje, že nástroj má být odebrán z instalace na úrovni uživatele. Nelze kombinovat s `--tool-path` možnost. Pokud nezadáte tuto možnost, je nutné zadat `--tool-path` možnost.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--tool-path <PATH>`

Určuje umístění, kam chcete-li odinstalovat nástroj globální. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možnost. Pokud nezadáte tuto možnost, je nutné zadat `--global` možnost.

## <a name="examples"></a>Příklady

Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:

`dotnet tool uninstall -g dotnetsay`

Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z konkrétní složky Windows:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z konkrétní složky Linux nebo macOS:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

- [.NET Core Global Tools](global-tools.md)
