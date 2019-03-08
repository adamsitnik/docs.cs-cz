---
title: Oficiální Image .NET Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Oficiální Image .NET Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: c4fce49b079473ddcc2b840527b8aeb951fec780
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674650"
---
# <a name="official-net-docker-images"></a>Oficiální Image .NET Dockeru

Oficiální .NET Dockeru Image jsou Image Dockeru vytvořené a optimalizované od Microsoftu. Jsou veřejně dostupné v úložištích Microsoft ve [Docker Hubu](https://hub.docker.com/u/microsoft/). Každé úložiště může obsahovat více bitových kopií, v závislosti na verze rozhraní .NET a v závislosti na operačním systému a verze (Linux, Debian, Alpine Linuxu, Windows Nano Server, Windows Server Core atd.).

Od verze rozhraní .NET Core 2.1 všechny .NET Core Image, jako je ASP.NET Core najdete na adrese Docker Hubu v úložišti .NET Core bitové kopie: https://hub.docker.com/r/microsoft/dotnet/

Většina úložišť image poskytují rozsáhlé označování pomoct při výběru ne jenom verze konkrétní verzi rozhraní framework, ale také zvolit operační systém (distribuce Linuxu nebo verze Windows).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core a Docker optimalizace image pro vývoj a produkčního prostředí

Při vytváření imagí Dockeru pro vývojáře, zaměřuje Microsoft na následující hlavní scénáře:

- Imagí používaných k *vývoj* a sestavení aplikace .NET Core.

- Imagí používaných k *spustit* aplikace .NET Core.

Proč více bitových kopií? Při vývoji, vytváření a spouštění kontejnerizovaných aplikací, obvykle mají různé priority. Zadáním různých imagí pro tyto jednotlivé úlohy Microsoft pomáhá optimalizovat samostatné procesy vývoje, sestavování a nasazování aplikací.

### <a name="during-development-and-build"></a>Během vývoje a sestavení

Během vývoje co je důležité je můžete jak rychle iterovat změny a možnost ladit změny. Velikost bitové kopie není důležité jako možnost provádět změny kódu a rychle se změny projevily. Některé nástroje a "agent sestavení kontejnery", použít obraz vývoj pro .NET Core (*microsoft / dotnet:2.2-sdk*) během procesu vývoje a sestavení. Při vytváření uvnitř kontejneru Dockeru, důležité aspekty jsou prvky, které jsou potřeba, aby bylo možné zkompilovat vaši aplikaci. To zahrnuje kompilátoru a další závislosti rozhraní .NET.

Proč je důležité tento typ bitové kopie sestavení? Tento obrázek nezvolíte nasazení do produkčního prostředí. Místo toho je obrázek, který používáte k sestavení obsahu, který umístíte do produkce image. Tato image se použije ve vašem prostředí kontinuální integrace (CI) nebo prostředí pro sestavení při použití Dockeru vícefázových sestavení.

### <a name="in-production"></a>V produkčním prostředí

Co je důležité v produkčním prostředí je, jak rychle nasadit a spustit vaše kontejnery založené na bitovou kopii produkčního prostředí .NET Core. Proto pouze modul runtime image na základě *microsoft / dotnet:2.2-aspnetcore-runtime* je malá, takže ho můžete projít rychle přes síť z registru Dockeru do hostitelů Docker. Obsah je připraven ke spuštění, povolení nejrychlejší doba spuštění kontejneru na zpracování výsledků. V modelu Dockeru, není nutné pro kompilaci from C\# kódu, protože došlo při spuštění sestavení dotnet nebo dotnet publikovat, kdy používá sestavení kontejneru.

V tomto optimalizované bitové kopie vložíte pouze binární soubory a jiný obsah potřebných ke spuštění aplikace. Například publikování obsahu vytvořeného v dotnet obsahuje pouze kompilované binární soubory rozhraní .NET, obrázků, JS a CSS souborů. V průběhu času se zobrazí imagí, které obsahují zpracované kompilátorem JIT předem (kompilace z IL na nativní, ke které dochází za běhu) balíčky.

I když existuje více verzí rozhraní .NET Core a ASP.NET Core imagí, ale všechny sdílet jednu nebo více vrstev, včetně základní vrstvě. Proto je malé množství místa na disku potřebné k uložení obrázku se skládá pouze rozdílů mezi vlastní image a jeho základní image. Výsledkem je, že je rychlé načíst image z registru.

Při prozkoumávání úložiště .NET image v Docker Hubu najdete několik verzí bitové kopie klasifikované nebo označené značkami. Tyto značky pomoct rozhodnout, který se má použít, v závislosti na verzi, které potřebujete, stejně jako v následující tabulce:

| Image                                       | Komentáře                                                                                          |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Microsoft/dotnet:**2.2-aspnetcore-modulu runtime** | ASP.NET Core s pouze modul runtime a optimalizace ASP.NET Core v Linuxu a Windows (více arch) |
| microsoft/dotnet:**2.2-sdk**                | .NET core, s zahrnutých sad SDK, na Linuxu a Windows (více arch)                                  |

> [!div class="step-by-step"]
> [Předchozí](net-container-os-targets.md)
> [další](../architect-microservice-container-applications/index.md)
