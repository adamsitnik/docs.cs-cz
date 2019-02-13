---
title: Aplikace SOA
description: Berte v úvahu, že kontejnery můžou být také možnost užitečné nasazení pro aplikace SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221261"
---
# <a name="soa-applications"></a><span data-ttu-id="5362e-103">Aplikace SOA</span><span class="sxs-lookup"><span data-stu-id="5362e-103">SOA applications</span></span>

<span data-ttu-id="5362e-104">SOA se Nepromyšlené termín a určená tolik různé věci pro různé osoby.</span><span class="sxs-lookup"><span data-stu-id="5362e-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="5362e-105">Ale minimálně a jako společným faktorem, SOA, nebo orientaci na služby, střední architekturu aplikace podle rozložení u více služeb (nejčastěji jako služeb HTTP), které mohou být zařazeny do různých typů struktury, jako jsou subsystémů nebo v jiných případech jako úrovní.</span><span class="sxs-lookup"><span data-stu-id="5362e-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="5362e-106">V současné době můžete nasadit tyto služby jako kontejnery Dockeru, které řeší problémy týkající se nasazení, protože všechny závislosti jsou zahrnuté do image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5362e-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="5362e-107">Ale pokud potřebujete SOAs horizontální navýšení kapacity, může dojít výzvy Pokud provádíte nasazení na základě jedné instance.</span><span class="sxs-lookup"><span data-stu-id="5362e-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="5362e-108">To je, kde Docker clustering softwaru nebo produktu orchestrator vám pomůže.</span><span class="sxs-lookup"><span data-stu-id="5362e-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="5362e-109">Podíváme na to podrobněji v další části při prozkoumáme přístupy mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="5362e-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="5362e-110">Na konci dne jsou užitečné pro obě tradiční architektura SOA nebo pro pokročilejší architekturu mikroslužeb, ve kterém je vlastníkem jednotlivých mikroslužeb její datový model clusteringu řešení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="5362e-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="5362e-111">A, díky více databází, můžete také můžete škálovat datovou vrstvu, místo abyste pracovali s monolitické databází sdílí služby SOA.</span><span class="sxs-lookup"><span data-stu-id="5362e-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="5362e-112">Diskuze o rozdělení dat je však čistě o architektuře a designu.</span><span class="sxs-lookup"><span data-stu-id="5362e-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5362e-113">[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="5362e-113">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>