---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632119"
---
> [!NOTE]
> Počínaje .NET Core 2.0 SDK, není nutné spustit [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) vzhledem k tomu, že je implicitně spouštět všechny příkazy, které vyžadují obnovení pravděpodobnější, jako například `dotnet new`, `dotnet build` a `dotnet run`.
> Je stále platný příkaz v některých scénářích, kde to explicitního obnovení dává smysl, jako například [sestavení kontinuální integrace ve službě Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je nutné explicitně určit čas, kdy dojde k obnovení.
