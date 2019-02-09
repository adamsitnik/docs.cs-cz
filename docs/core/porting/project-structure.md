---
title: Uspořádání projektů pro rozhraní .NET Framework a .NET Core
description: Nápovědu k projektu vlastníky, kteří chtějí kompilaci své řešení pro rozhraní .NET Framework a .NET Core side-by-side.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 57bb766f1d91c502a508b6362dc642310009c8c4
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904027"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="c9c9a-103">Uspořádání vašeho projektu pro podporu rozhraní .NET Framework a .NET Core</span><span class="sxs-lookup"><span data-stu-id="c9c9a-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="c9c9a-104">Zjistěte, jak vytvořit řešení, které zkompiluje pro rozhraní .NET Framework a .NET Core – souběžně.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="c9c9a-105">Zobrazit několik možností, jak uspořádat projektech při dosažení tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="c9c9a-106">Tady jsou některé typické scénáře, které je třeba zvážit, když jste rozhodování o tom, jak nastavit rozložení projektu s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="c9c9a-107">V seznamu nemusí zahrnovat všechno, co chcete, aby; prioritizujte podle potřeb vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* [<span data-ttu-id="c9c9a-108">**Existující projekty a projekty .NET Core zkombinovat do jedné projekty**</span><span class="sxs-lookup"><span data-stu-id="c9c9a-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="c9c9a-109">*Co to platí pro:*</span><span class="sxs-lookup"><span data-stu-id="c9c9a-109">*What this is good for:*</span></span>
  * <span data-ttu-id="c9c9a-110">Zjednodušení procesu sestavení kompilaci jednoho projektu, spíše než sestavování více projektů, každý cílí na různé verze rozhraní .NET Framework nebo platformu.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="c9c9a-111">Protože je třeba spravovat jediného souboru projektu, která zjednodušuje jejich správa zdrojového souboru pro více cílových projekty.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="c9c9a-112">Při přidávání nebo odebírání zdrojových souborů, alternativ vyžadují ruční synchronizaci těchto s vašimi projekty.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="c9c9a-113">Snadno generování balíčku NuGet pro spotřebu.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="c9c9a-114">Umožňuje napsat kód pro konkrétní verzi rozhraní .NET Framework ve vašich knihovnách pomocí direktivy kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="c9c9a-115">*Nepodporované scénáře:*</span><span class="sxs-lookup"><span data-stu-id="c9c9a-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="c9c9a-116">Vyžaduje, aby pomocí sady Visual Studio 2017 otevřete existující projekty vývojáři.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="c9c9a-117">Pro podporu starších verzích sady Visual Studio [uchovávání souborů projektu v různých složkách](#support-vs) je lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="c9c9a-118">[**Oddělovat existující projekty a nové projekty .NET Core**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="c9c9a-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="c9c9a-119">*Co to platí pro:*</span><span class="sxs-lookup"><span data-stu-id="c9c9a-119">*What this is good for:*</span></span>
  * <span data-ttu-id="c9c9a-120">Pokračování pro podporu vývoje na existující projekty bez nutnosti upgradu pro vývojáře/přispěvatele, kteří nemají Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="c9c9a-121">Snižuje možnost vytvářet nové chyby v existujících projektů, protože vyžaduje žádné změny kódu v těchto projektech.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="c9c9a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9c9a-122">Example</span></span>

<span data-ttu-id="c9c9a-123">Vezměte v úvahu následující úložiště:</span><span class="sxs-lookup"><span data-stu-id="c9c9a-123">Consider the repository below:</span></span>

![Existující projekt](media/project-structure/project.png)

[<span data-ttu-id="c9c9a-125">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="c9c9a-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="c9c9a-126">Následující část popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na tom, omezení a složitosti existujících projektů.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="c9c9a-127">Nahraďte existující projekty cílené více projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c9c9a-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="c9c9a-128">Uspořádání úložiště tak, že všechny existující  *\*.csproj* soubory jsou odebrané a jednu  *\*.csproj* se vytvoří soubor, který cílí na více platforem.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="c9c9a-129">To je skvělá možnost, protože jednoho projektu je schopen kompilace pro různá rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="c9c9a-130">Má také výkon pro zpracování různých kompilace možností a závislosti na cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Vytvoření csproj, který cílí na více platforem](media/project-structure/project.csproj.png)

[<span data-ttu-id="c9c9a-132">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="c9c9a-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="c9c9a-133">Všimněte si změny jsou:</span><span class="sxs-lookup"><span data-stu-id="c9c9a-133">Changes to note are:</span></span>

* <span data-ttu-id="c9c9a-134">Nahrazení *souboru packages.config* a  *\*.csproj* s novou [.NET Core  *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="c9c9a-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="c9c9a-135">Balíčky NuGet jsou zadány s `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="c9c9a-136">Zachovat existující projekty a vytvořte projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="c9c9a-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="c9c9a-137">Pokud je existující projekty, které jsou cíleny na starší rozhraní, můžete ponechat beze změny těchto projektů a používat projekt .NET Core pro budoucí platforem.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projekt .NET core s existující projekt do jiné složky](media/project-structure/project.csproj.different.png)

[<span data-ttu-id="c9c9a-139">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="c9c9a-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="c9c9a-140">Všimněte si změny jsou:</span><span class="sxs-lookup"><span data-stu-id="c9c9a-140">Changes to note are:</span></span>

* <span data-ttu-id="c9c9a-141">Existující projekty .NET Core a jsou uchovávány v oddělených složek.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="c9c9a-142">Udržování projektů do samostatné složky zabraňuje vynucení, abyste měli Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="c9c9a-143">Můžete vytvořit samostatné řešení, které otevře pouze starých projektů.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9c9a-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9c9a-144">See also</span></span>

<span data-ttu-id="c9c9a-145">Podrobnosti najdete [portování dokumentace k .NET Core](index.md) další pokyny k migraci až po .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9c9a-145">Please see the [.NET Core porting documentation](index.md) for more guidance on migrating to .NET Core.</span></span>
