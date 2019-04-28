---
title: Odebrat balíček příkaz DotNet
description: Příkaz dotnet odebrat balíček poskytuje pohodlné možnost pro odebrání odkazu na balíček NuGet do projektu.
ms.date: 05/29/2018
ms.openlocfilehash: 4cc8ac927b761547dc5e53be9abeba827bf1e1d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664854"
---
# <a name="dotnet-remove-package"></a>DotNet odebrat balíček

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet remove package` – Odebere odkaz na balíček ze souboru projektu.

## <a name="synopsis"></a>Souhrn

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Popis

`dotnet remove package` Příkaz poskytuje vhodnou možnost odebrat z projektu odkaz na balíček NuGet.

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.

`PACKAGE_NAME`

Odkaz na balíček k odebrání.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

## <a name="examples"></a>Příklady

Odebere `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:

`dotnet remove package Newtonsoft.Json`