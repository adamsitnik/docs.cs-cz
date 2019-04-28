---
title: příkaz DotNet serveru sestavení
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665309"
---
# <a name="dotnet-build-server"></a>DotNet – server sestavení

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.

## <a name="synopsis"></a>Souhrn

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Příkazy

* **`shutdown`**

  Vypne sestavovací servery, které jsou spuštěny z dotnet. Ve výchozím nastavení jsou všechny servery vypnout.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--msbuild`**

  Ukončí MSBuild serveru sestavení.

* **`--razor`**

  Server sestavení vypne syntaxi Razor.

* **`--vbcscompiler`**

  Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.