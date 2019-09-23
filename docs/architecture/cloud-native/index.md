---
title: Architekt cloudových nativních aplikací .NET pro Azure
description: Příručka pro sestavování nativních aplikací cloudu využívajících kontejnery, mikroslužby a funkce bez serveru v Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: ce9898366d0327dd619b36cdf1487229d9cda7f5
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183040"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="fb370-103">Architekt cloudových nativních aplikací .NET pro Azure</span><span class="sxs-lookup"><span data-stu-id="fb370-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![titulní obrázek](./media/cover.png)

<span data-ttu-id="fb370-105">PUBLIKOVAL (A)</span><span class="sxs-lookup"><span data-stu-id="fb370-105">PUBLISHED BY</span></span>

<span data-ttu-id="fb370-106">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fb370-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="fb370-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fb370-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="fb370-108">Jeden způsob Microsoftu</span><span class="sxs-lookup"><span data-stu-id="fb370-108">One Microsoft Way</span></span>

<span data-ttu-id="fb370-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="fb370-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="fb370-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fb370-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="fb370-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="fb370-111">All rights reserved.</span></span> <span data-ttu-id="fb370-112">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="fb370-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="fb370-113">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="fb370-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="fb370-114">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="fb370-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="fb370-115">Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="fb370-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="fb370-116">Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.</span><span class="sxs-lookup"><span data-stu-id="fb370-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="fb370-117">Microsoft a ochranné známky uvedené https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fb370-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="fb370-118">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="fb370-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="fb370-119">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc. Používá se oprávněním.</span><span class="sxs-lookup"><span data-stu-id="fb370-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="fb370-120">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="fb370-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="fb370-121">Autorizova</span><span class="sxs-lookup"><span data-stu-id="fb370-121">Author:</span></span>

> <span data-ttu-id="fb370-122">**Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="fb370-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="fb370-123">**Rob Vettor** – Microsoft-Principal Cloud System architekt/IP architekt – [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="fb370-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="fb370-124">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="fb370-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="fb370-125">**Cesar de la Torre**, Principal program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb370-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fb370-126">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb370-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="fb370-127">Editory</span><span class="sxs-lookup"><span data-stu-id="fb370-127">Editors:</span></span>

> <span data-ttu-id="fb370-128">**Maira Wenzel**, SR. Content Developer, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb370-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="fb370-129">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="fb370-129">Who should use this guide</span></span>

<span data-ttu-id="fb370-130">Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření aplikací určených pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="fb370-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="fb370-131">Sekundární cílová skupina je technickým rozhodnutím, které plánuje vybrat, jestli se mají vytvářet aplikace s využitím nativního přístupu v cloudu.</span><span class="sxs-lookup"><span data-stu-id="fb370-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="fb370-132">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="fb370-132">How you can use this guide</span></span>

<span data-ttu-id="fb370-133">Tato příručka začíná definováním cloudového nativního nasazení a představením referenční aplikace vytvořené pomocí cloudových nativních principů a technologií.</span><span class="sxs-lookup"><span data-stu-id="fb370-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="fb370-134">Kromě těchto prvních dvou kapitol se zbytek knihy rozdělí na konkrétní kapitoly zaměřené na témata, která jsou společná pro většinu cloudových nativních aplikací.</span><span class="sxs-lookup"><span data-stu-id="fb370-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="fb370-135">Pokud se chcete dozvědět víc o přístupech nativních ke cloudu, můžete přejít na libovolnou z těchto kapitol:</span><span class="sxs-lookup"><span data-stu-id="fb370-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="fb370-136">Data a přístup k datům</span><span class="sxs-lookup"><span data-stu-id="fb370-136">Data and data access</span></span>
- <span data-ttu-id="fb370-137">Způsoby komunikace</span><span class="sxs-lookup"><span data-stu-id="fb370-137">Communication patterns</span></span>
- <span data-ttu-id="fb370-138">Škálování a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="fb370-138">Scaling and scalability</span></span>
- <span data-ttu-id="fb370-139">Odolnost aplikace</span><span class="sxs-lookup"><span data-stu-id="fb370-139">Application resiliency</span></span>
- <span data-ttu-id="fb370-140">Monitorování a stav</span><span class="sxs-lookup"><span data-stu-id="fb370-140">Monitoring and health</span></span>
- <span data-ttu-id="fb370-141">Identita a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fb370-141">Identity and security</span></span>
- <span data-ttu-id="fb370-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="fb370-142">DevOps</span></span>

<span data-ttu-id="fb370-143">Tato příručka je k dispozici ve formátu PDF i v online režimu.</span><span class="sxs-lookup"><span data-stu-id="fb370-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="fb370-144">Nebojte se, že tento dokument předáte nebo odkazuje na jeho online verzi týmu, aby se zajistilo běžné porozumění těmto tématům.</span><span class="sxs-lookup"><span data-stu-id="fb370-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="fb370-145">Většina těchto témat přináší konzistentní porozumění základním principům a vzorům a kompromisům, které se týkají rozhodnutí souvisejících s těmito tématy.</span><span class="sxs-lookup"><span data-stu-id="fb370-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="fb370-146">Naším cílem tohoto dokumentu je vybavit týmy a jejich vedoucími informacemi, které potřebují k rozhodování o jejich architektuře, vývoji a hostování svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="fb370-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="fb370-147">Next</span><span class="sxs-lookup"><span data-stu-id="fb370-147">Next</span></span>](introduction.md)