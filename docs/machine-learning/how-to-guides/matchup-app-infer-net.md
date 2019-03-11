---
title: Vytvoření hry shoda seznamu aplikaci pomocí Infer.NET a pravděpodobnostní programování
description: Zjistěte, jak používat pravděpodobnostní programování s Infer.NET k vytvoření aplikace seznamu her zápasu založen na zjednodušené verzi TrueSkill.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 06538ec9de26f5aeabe474fbcae69f0a313c8d32
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679130"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="a0797-103">Vytvoření hry shoda seznamu aplikaci pomocí Infer.NET a pravděpodobnostní programování</span><span class="sxs-lookup"><span data-stu-id="a0797-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

> [!NOTE]
> <span data-ttu-id="a0797-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="a0797-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="a0797-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a0797-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="a0797-106">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="a0797-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="a0797-107">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="a0797-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="a0797-108">Tato příručka vás naučí o pravděpodobnostní programování pomocí Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="a0797-108">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="a0797-109">Pravděpodobnostní programování je přístup založený na machine learning, ve kterém jsou vlastní modely vyjádřené jako počítačové programy.</span><span class="sxs-lookup"><span data-stu-id="a0797-109">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="a0797-110">Umožňuje pro začlenění znalosti v těchto modelech a je strojové učení více interpretovatelném systému.</span><span class="sxs-lookup"><span data-stu-id="a0797-110">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="a0797-111">Podporuje také online odvození – proces učení příchodu nových dat.</span><span class="sxs-lookup"><span data-stu-id="a0797-111">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="a0797-112">Infer.NET se používá v různých produktů v Microsoftu v Azure, Xbox a Bing.</span><span class="sxs-lookup"><span data-stu-id="a0797-112">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="a0797-113">Co je pravděpodobnostní programování?</span><span class="sxs-lookup"><span data-stu-id="a0797-113">What is probabilistic programming?</span></span>

<span data-ttu-id="a0797-114">Pravděpodobnostní programování umožňuje vytvořit statistických modelů procesů reálného světa.</span><span class="sxs-lookup"><span data-stu-id="a0797-114">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0797-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0797-115">Prerequisites</span></span>

- <span data-ttu-id="a0797-116">Nastavení místního vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="a0797-116">Local development environment setup</span></span>

  <span data-ttu-id="a0797-117">Tato příručka se očekává, že budete mít počítač, který používáte pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="a0797-117">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="a0797-118">.NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) kurz obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="a0797-118">The .NET [Get Started in 10 minutes](https://www.microsoft.com/net/core) tutorial has instructions for setting up your local development environment on Mac, PC, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="a0797-119">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="a0797-119">Create your app</span></span>

1. <span data-ttu-id="a0797-120">Otevřete nový příkazový řádek a spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="a0797-120">Open a new command prompt and run the following commands:</span></span>

```console
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="a0797-121">`dotnet` Příkaz vytvoří `new` aplikace typu `console`.</span><span class="sxs-lookup"><span data-stu-id="a0797-121">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="a0797-122">`-o` Parametr vytvoří adresář s názvem `myApp` kde vaše aplikace je uložena a naplní ho s požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="a0797-122">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="a0797-123">`cd myApp` Příkaz vloží do adresáře nově vytvořené aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0797-123">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="a0797-124">Nainstalujte balíček Infer.NET</span><span class="sxs-lookup"><span data-stu-id="a0797-124">Install Infer.NET package</span></span>

<span data-ttu-id="a0797-125">Pokud chcete použít Infer.NET, je potřeba nainstalovat `Microsoft.ML.Probabilistic.Compiler` balíčku.</span><span class="sxs-lookup"><span data-stu-id="a0797-125">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="a0797-126">V příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a0797-126">In your command prompt, run the following command:</span></span>

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="a0797-127">Návrh modelu</span><span class="sxs-lookup"><span data-stu-id="a0797-127">Design your model</span></span>

<span data-ttu-id="a0797-128">Vzorový příklad používá tenis tabulky nebo foosball shody přehrát v kanceláři.</span><span class="sxs-lookup"><span data-stu-id="a0797-128">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="a0797-129">Máte účastníky a výsledek jednotlivých shod.</span><span class="sxs-lookup"><span data-stu-id="a0797-129">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="a0797-130">Chcete hráče dovednosti z těchto dat odvodit.</span><span class="sxs-lookup"><span data-stu-id="a0797-130">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="a0797-131">Předpokládejme, že oba hráči má obvykle distribuované latentní dovedností a jejich výkon daného shoda je hlučného verzi této dovedností.</span><span class="sxs-lookup"><span data-stu-id="a0797-131">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="a0797-132">Data omezí vítěze výkon a být větší než odstraněných výkonu.</span><span class="sxs-lookup"><span data-stu-id="a0797-132">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="a0797-133">Toto je zjednodušenou verzi Oblíbené [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, který podporuje také týmy, nakreslí a další rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a0797-133">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="a0797-134">[Rozšířená verze](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tento model se používá pro matchmaking v nejprodávanějšího herních titulů Halo a Gears War.</span><span class="sxs-lookup"><span data-stu-id="a0797-134">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="a0797-135">Seznam odvozené player dovedností, společně s jejich odchylky – míra nejistoty dovednosti, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a0797-135">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="a0797-136">*Herní výsledek ukázková data*</span><span class="sxs-lookup"><span data-stu-id="a0797-136">*Game result sample data*</span></span>

<span data-ttu-id="a0797-137">Hra</span><span class="sxs-lookup"><span data-stu-id="a0797-137">Game</span></span> |<span data-ttu-id="a0797-138">Vítěz</span><span class="sxs-lookup"><span data-stu-id="a0797-138">Winner</span></span> | <span data-ttu-id="a0797-139">Odstraněných</span><span class="sxs-lookup"><span data-stu-id="a0797-139">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="a0797-140">1</span><span class="sxs-lookup"><span data-stu-id="a0797-140">1</span></span> | <span data-ttu-id="a0797-141">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="a0797-141">Player 0</span></span> | <span data-ttu-id="a0797-142">Přehrávač 1</span><span class="sxs-lookup"><span data-stu-id="a0797-142">Player 1</span></span>
 <span data-ttu-id="a0797-143">2</span><span class="sxs-lookup"><span data-stu-id="a0797-143">2</span></span> | <span data-ttu-id="a0797-144">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="a0797-144">Player 0</span></span> | <span data-ttu-id="a0797-145">Přehrávač 3</span><span class="sxs-lookup"><span data-stu-id="a0797-145">Player 3</span></span>
 <span data-ttu-id="a0797-146">3</span><span class="sxs-lookup"><span data-stu-id="a0797-146">3</span></span> | <span data-ttu-id="a0797-147">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="a0797-147">Player 0</span></span> | <span data-ttu-id="a0797-148">Přehrávač 4</span><span class="sxs-lookup"><span data-stu-id="a0797-148">Player 4</span></span>
 <span data-ttu-id="a0797-149">4</span><span class="sxs-lookup"><span data-stu-id="a0797-149">4</span></span> | <span data-ttu-id="a0797-150">Přehrávač 1</span><span class="sxs-lookup"><span data-stu-id="a0797-150">Player 1</span></span> | <span data-ttu-id="a0797-151">Přehrávač 2</span><span class="sxs-lookup"><span data-stu-id="a0797-151">Player 2</span></span>
 <span data-ttu-id="a0797-152">5</span><span class="sxs-lookup"><span data-stu-id="a0797-152">5</span></span> | <span data-ttu-id="a0797-153">Přehrávač 3</span><span class="sxs-lookup"><span data-stu-id="a0797-153">Player 3</span></span> | <span data-ttu-id="a0797-154">Přehrávač 1</span><span class="sxs-lookup"><span data-stu-id="a0797-154">Player 1</span></span>
 <span data-ttu-id="a0797-155">6</span><span class="sxs-lookup"><span data-stu-id="a0797-155">6</span></span> | <span data-ttu-id="a0797-156">Přehrávač 4</span><span class="sxs-lookup"><span data-stu-id="a0797-156">Player 4</span></span> | <span data-ttu-id="a0797-157">Přehrávač 2</span><span class="sxs-lookup"><span data-stu-id="a0797-157">Player 2</span></span>

<span data-ttu-id="a0797-158">S bližší pohled na ukázková data můžete si všimnout, že přehrávače 3 a 4 mají jeden win a ztráty jedné.</span><span class="sxs-lookup"><span data-stu-id="a0797-158">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="a0797-159">Podívejme se, jak pořadí vypadat, pomocí pravděpodobnostní programování.</span><span class="sxs-lookup"><span data-stu-id="a0797-159">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="a0797-160">Všimněte si že také je přehrávač nule vzhledem k tomu, že i office odpovídající seznamy jsou pro nás vývojáře od nuly.</span><span class="sxs-lookup"><span data-stu-id="a0797-160">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="a0797-161">Napsání kódu</span><span class="sxs-lookup"><span data-stu-id="a0797-161">Write some code</span></span>

<span data-ttu-id="a0797-162">S navržená modelem, je čas ji je možné vyjádřit jako pravděpodobnostní programu pomocí Infer.NET modelování rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="a0797-162">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="a0797-163">Otevřít `Program.cs` ve svém oblíbeném textovém editoru a veškerý jeho obsah nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="a0797-163">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a><span data-ttu-id="a0797-164">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="a0797-164">Run your app</span></span>

<span data-ttu-id="a0797-165">V příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a0797-165">In your command prompt, run the following command:</span></span>

```console
dotnet run
```

## <a name="results"></a><span data-ttu-id="a0797-166">Výsledky</span><span class="sxs-lookup"><span data-stu-id="a0797-166">Results</span></span>

<span data-ttu-id="a0797-167">Výsledky by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="a0797-167">Your results should be similar to the following:</span></span>

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

<span data-ttu-id="a0797-168">Ve výsledcích Všimněte si, že tento přehrávač 3 řadí mírně zvýšené v přehrávači 4 podle našeho modelu.</span><span class="sxs-lookup"><span data-stu-id="a0797-168">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="a0797-169">Důvodem je, že vítězství player 3 přes player 1 je mnohem závažnější než vítězství player 4 přes player 2 – Poznámka: Tento přehrávač 1 údery player 2.</span><span class="sxs-lookup"><span data-stu-id="a0797-169">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="a0797-170">Přehrávač 0 je celkový specialita!</span><span class="sxs-lookup"><span data-stu-id="a0797-170">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="a0797-171">Zajištění, že výuka</span><span class="sxs-lookup"><span data-stu-id="a0797-171">Keep learning</span></span>

<span data-ttu-id="a0797-172">Navrhování statistických modelů je dovednosti sama o sobě.</span><span class="sxs-lookup"><span data-stu-id="a0797-172">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="a0797-173">Tým Microsoft Research Cambridge zapsala [bezplatné online knihy](http://mbmlbook.com/), což dává mírného Úvod do článku.</span><span class="sxs-lookup"><span data-stu-id="a0797-173">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="a0797-174">Tato kniha kapitolu 3 se týká modelu TrueSkill podrobněji.</span><span class="sxs-lookup"><span data-stu-id="a0797-174">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="a0797-175">Jakmile budete mít modelu v paměti, můžete jeho transformaci na kódu pomocí [si rozsáhlou dokumentaci k](https://dotnet.github.io/infer/) na webu Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="a0797-175">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a0797-176">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a0797-176">Next steps</span></span>

<span data-ttu-id="a0797-177">Projděte si úložiště Infer.NET GitHub pokračujte ve čtení a najít další ukázky.</span><span class="sxs-lookup"><span data-stu-id="a0797-177">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a0797-178">DotNet/odvodit úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="a0797-178">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
