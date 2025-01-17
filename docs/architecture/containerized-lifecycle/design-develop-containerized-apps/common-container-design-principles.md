---
title: Běžné zásady návrhu kontejneru
description: Seznamte se se základní princip dobrých návrhů kontejnerů, je to, že by měl být kontejner hostitelem pouze jednoho procesu.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295329"
---
# <a name="common-container-design-principles"></a>Běžné zásady návrhu kontejneru

Před přihlédnutím k procesu vývoje existuje několik základních konceptů, které se týkají použití kontejnerů.

## <a name="container-equals-a-process"></a>Kontejner se rovná procesu

V modelu kontejneru představuje kontejner jeden proces. Definováním kontejneru jako hranice procesu začínáte vytvářet primitivní prvky, které se používají ke škálování nebo dávkování procesů. Při spuštění kontejneru Docker se zobrazí definice [vstupního bodu](https://docs.docker.com/engine/reference/builder/#/entrypoint) . Tím se definuje proces a doba života kontejneru. Po dokončení procesu skončí životní cyklus kontejneru. Existují dlouhotrvající procesy, jako jsou například webové servery, a krátkodobé procesy, například dávkové úlohy, které mohou být implementovány jako Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). Pokud se proces nezdařil, kontejner skončí a nástroj Orchestrator převezme. Pokud byl Orchestrator pokyn, aby zachoval pět instancí a jeden selže, Orchestrator vytvoří další kontejner, který nahradí neúspěšný proces. V úloze Batch se proces spouští s parametry. Po dokončení procesu se práce dokončí.

Můžete najít scénář, ve kterém chcete, aby více procesů běželo v jednom kontejneru. V jakémkoli dokumentu architektury není nikdy "nikdy", ani není vždy vždy "Always". Pro scénáře, které vyžadují více procesů, je běžným vzorem použití [správce](http://supervisord.org/).

>[!div class="step-by-step"]
>[Předchozí](design-docker-applications.md)Další
>[](monolithic-applications.md)
