---
title: Registry, image a kontejnery Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Kontejnery dockeru, obrázky a registry
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: f10d7d03bbf88ed8f7a89a5d3919a39b3c124ae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025536"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="2f914-103">Registry, image a kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="2f914-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="2f914-104">Při použití Dockeru, vytvoří vývojář aplikace nebo služby a balíčky a jeho závislosti do image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2f914-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="2f914-105">Bitovou je statických reprezentace aplikace nebo služby a jeho konfiguraci a závislostech.</span><span class="sxs-lookup"><span data-stu-id="2f914-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="2f914-106">Ke spuštění aplikace nebo služby, je vytvořena instance aplikace image k vytvoření kontejneru, který bude spuštěn na hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="2f914-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="2f914-107">Kontejnery jsou zpočátku testovat ve vývojovém prostředí nebo PC.</span><span class="sxs-lookup"><span data-stu-id="2f914-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="2f914-108">Vývojáři by měly ukládat Image v registru, který funguje jako knihovny imagí a je potřeba při nasazení do produkčního prostředí orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="2f914-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="2f914-109">Udržuje prostřednictvím veřejného registru docker [Docker Hubu](https://hub.docker.com/); ostatní dodavatelé poskytují registrů pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="2f914-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="2f914-110">Alternativně můžete podniky mají privátního registru on-premises pro vlastní Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="2f914-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="2f914-111">Obrázek 2 – 4 zobrazuje obrázky a registry v Dockeru vztah k jiné komponenty.</span><span class="sxs-lookup"><span data-stu-id="2f914-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="2f914-112">Také ukazuje několik nabídek registru od dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="2f914-112">It also shows the multiple registry offerings from vendors.</span></span>

![Základní taxonomie v Dockeru: Registr je stejně jako bookshelf kde Image jsou uložené a k dispozici i pro vytváření kontejnerů ke spuštění služeb nebo webových aplikací.](./media/image5.PNG)

<span data-ttu-id="2f914-117">**Obrázek 2 – 4**.</span><span class="sxs-lookup"><span data-stu-id="2f914-117">**Figure 2-4**.</span></span> <span data-ttu-id="2f914-118">Taxonomie služby Docker terminologie a koncepty</span><span class="sxs-lookup"><span data-stu-id="2f914-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="2f914-119">Vložení imagí v registru umožňuje ukládat bits statické a neměnné aplikace, včetně všech jeho závislostí na úrovni rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="2f914-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="2f914-120">Tyto Image můžete pak se systémovou správou verzí a nasazených v různých prostředích a proto poskytují jednotku, konzistentní nasazování.</span><span class="sxs-lookup"><span data-stu-id="2f914-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="2f914-121">Privátní image registrů, buď hostovaný místně nebo v cloudu, se doporučuje při:</span><span class="sxs-lookup"><span data-stu-id="2f914-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="2f914-122">Bitové kopie nesmí veřejně sdílené z důvodu důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="2f914-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="2f914-123">Chcete mít minimální latence mezi vašich imagí a prostředí pro vybrané nasazení.</span><span class="sxs-lookup"><span data-stu-id="2f914-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="2f914-124">Například pokud vaše produkční prostředí cloudu Azure, pravděpodobně chcete ukládat Image v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, že bude minimální latence sítě.</span><span class="sxs-lookup"><span data-stu-id="2f914-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="2f914-125">Podobným způsobem Pokud je v místním prostředí produkčního prostředí můžete chtít mít místní Docker Trusted Registry k dispozici v rámci stejné místní síti.</span><span class="sxs-lookup"><span data-stu-id="2f914-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2f914-126">[Předchozí](docker-terminology.md)
>[další](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="2f914-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>