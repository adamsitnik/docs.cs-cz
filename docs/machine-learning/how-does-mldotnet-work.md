---
title: Co je ML.NET a jak to funguje?
description: ML.NET dává možnost Přidat strojového učení pro aplikace .NET. Díky této funkci můžete vytvářet automatické predikce data dostupná pro vaše aplikace. Tento článek vysvětluje základy strojového učení v ML.NET.
ms.date: 04/10/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: ea5797cb8f2fd0654d9facb636bc857eeb8e5aad
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063699"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="e60be-105">Co je ML.NET a jak to funguje?</span><span class="sxs-lookup"><span data-stu-id="e60be-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="e60be-106">ML.NET dává možnost Přidat strojového učení pro aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="e60be-106">ML.NET gives you the ability to add machine learning to .NET applications.</span></span> <span data-ttu-id="e60be-107">Díky této funkci můžete vytvářet automatické predikce data dostupná pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="e60be-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="e60be-108">Tento článek vysvětluje základy strojového učení v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e60be-108">This article explains the basics of machine learning in ML.NET.</span></span> 

<span data-ttu-id="e60be-109">Mezi příklady typu predikcí, které můžete použít s ML.NET patří:</span><span class="sxs-lookup"><span data-stu-id="e60be-109">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="e60be-110">Klasifikace a kategorizaci</span><span class="sxs-lookup"><span data-stu-id="e60be-110">Classification/Categorization</span></span>|<span data-ttu-id="e60be-111">Automaticky dělit zpětné vazby od zákazníků do kladnou a zápornou kategorií</span><span class="sxs-lookup"><span data-stu-id="e60be-111">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="e60be-112">Regrese/Predict průběžné hodnoty</span><span class="sxs-lookup"><span data-stu-id="e60be-112">Regression/Predict continuous values</span></span>|<span data-ttu-id="e60be-113">Odhadnout cenu na základě velikosti a umístění Domů</span><span class="sxs-lookup"><span data-stu-id="e60be-113">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="e60be-114">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="e60be-114">Anomaly Detection</span></span>|<span data-ttu-id="e60be-115">Zjištění podvodné bankovních transakcí</span><span class="sxs-lookup"><span data-stu-id="e60be-115">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="e60be-116">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e60be-116">Recommendations</span></span>|<span data-ttu-id="e60be-117">Navrhnout produktů, které si chcete koupit, může být vhodné nakupující online podle jejich předchozí nákupů</span><span class="sxs-lookup"><span data-stu-id="e60be-117">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="e60be-118">Hello ML.NET World</span><span class="sxs-lookup"><span data-stu-id="e60be-118">Hello ML.NET World</span></span>

<span data-ttu-id="e60be-119">Kódu následující fragment kódu ukazuje nejjednodušší ML.NET aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e60be-119">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="e60be-120">Tento příklad vytvoří model lineární regrese k předvídání cen house pomocí velikosti a ceny dat organizace.</span><span class="sxs-lookup"><span data-stu-id="e60be-120">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="e60be-121">V reálné aplikace data a model bude mnohem složitější.</span><span class="sxs-lookup"><span data-stu-id="e60be-121">In your real-life applications, your data and model will be much more complex.</span></span>

 ```csharp
    using System;
    using System.IO;
    using Microsoft.Data.DataView;
    using Microsoft.ML;
    using Microsoft.ML.Data;
    
    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }
    
        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }
    
        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();
    
            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100);
    
            // 3. Train model
            var model = pipeline.Fit(trainingData);
    
            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    } 
```

## <a name="code-workflow"></a><span data-ttu-id="e60be-122">Kód pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e60be-122">Code workflow</span></span>

<span data-ttu-id="e60be-123">Následující diagram představuje strukturu kódu aplikace a také iterativní proces vývoje modelu:</span><span class="sxs-lookup"><span data-stu-id="e60be-123">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>
- <span data-ttu-id="e60be-124">Shromažďování a načíst trénovacích dat do **IDataView** objektu</span><span class="sxs-lookup"><span data-stu-id="e60be-124">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="e60be-125">Zadat kanál operací pro extrakci funkce a použití algoritmu strojového učení</span><span class="sxs-lookup"><span data-stu-id="e60be-125">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="e60be-126">Trénování modelu voláním **Fit()** ke kanálu</span><span class="sxs-lookup"><span data-stu-id="e60be-126">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="e60be-127">Vyhodnocení modelu a iterovat ke zlepšení</span><span class="sxs-lookup"><span data-stu-id="e60be-127">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="e60be-128">Uložit model do binárního formátu pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="e60be-128">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="e60be-129">Načtení modelu zpět do **ITransformer** objektu</span><span class="sxs-lookup"><span data-stu-id="e60be-129">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="e60be-130">Predikci voláním **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="e60be-130">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Běh vývoj aplikace ML.NET včetně komponent pro generování dat, vývoj kanálu, model školení, vyhodnocení modelu a využití modelu](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="e60be-132">Pojďme se podívat trochu hlouběji do těchto konceptů.</span><span class="sxs-lookup"><span data-stu-id="e60be-132">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="e60be-133">Model strojového učení</span><span class="sxs-lookup"><span data-stu-id="e60be-133">Machine learning model</span></span>

<span data-ttu-id="e60be-134">ML.NET model je objekt, který obsahuje transformace provádět na vstupní data můžete přejít na výstup předpokládaná.</span><span class="sxs-lookup"><span data-stu-id="e60be-134">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="e60be-135">Základní</span><span class="sxs-lookup"><span data-stu-id="e60be-135">Basic</span></span>

<span data-ttu-id="e60be-136">Základní model je dvojrozměrné lineární regrese, kde je úměrný do jiného, stejně jako v výše uvedený příklad ceny uložení jednoho průběžné množství.</span><span class="sxs-lookup"><span data-stu-id="e60be-136">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![Lineární regrese Model s parametry posun a váhy záznamu](./media/linear-regression-model.svg)

<span data-ttu-id="e60be-138">Model je jednoduše: $Price = b + velikost \* w$.</span><span class="sxs-lookup"><span data-stu-id="e60be-138">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="e60be-139">Posunout řádek na spektru jsou odhady parametry $b$ a $w$ (velikost, cena) dvojice.</span><span class="sxs-lookup"><span data-stu-id="e60be-139">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="e60be-140">Data použitá k vyhledání parametrů model se nazývá **trénovacích dat**.</span><span class="sxs-lookup"><span data-stu-id="e60be-140">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="e60be-141">Vstupy modelu strojového učení se nazývají **funkce**.</span><span class="sxs-lookup"><span data-stu-id="e60be-141">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="e60be-142">V tomto příkladu je $Size$ pouze funkce.</span><span class="sxs-lookup"><span data-stu-id="e60be-142">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="e60be-143">Hodnoty základu pravdy využívají k tréninku modelu strojového učení se nazývají **popisky**.</span><span class="sxs-lookup"><span data-stu-id="e60be-143">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="e60be-144">Tady hodnoty $ $Price v trénovací datové sady jsou popisky.</span><span class="sxs-lookup"><span data-stu-id="e60be-144">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="e60be-145">Složitější</span><span class="sxs-lookup"><span data-stu-id="e60be-145">More complex</span></span>

<span data-ttu-id="e60be-146">Složitější modelu klasifikuje finanční transakce do kategorií pomocí textový popis transakce.</span><span class="sxs-lookup"><span data-stu-id="e60be-146">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="e60be-147">Popis každého transakce je rozdělena do sadu funkcí odebráním redundantní slova a znaků a počítání kombinace aplikace word a znaků.</span><span class="sxs-lookup"><span data-stu-id="e60be-147">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="e60be-148">Sada funkcí se používá pro trénování modelu lineární na základě sady kategorií v trénovací data.</span><span class="sxs-lookup"><span data-stu-id="e60be-148">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="e60be-149">Čím více podobně jako nový popis v cvičnou sadou, tím spíše se přiřadí do stejné kategorie.</span><span class="sxs-lookup"><span data-stu-id="e60be-149">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![Model klasifikace textu](./media/text-classification-model.svg)

<span data-ttu-id="e60be-151">Cenový model house i textový model klasifikace jsou **lineární** modely.</span><span class="sxs-lookup"><span data-stu-id="e60be-151">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="e60be-152">V závislosti na povaze vašich dat a jsou řešení problému, můžete také použít **rozhodovací strom** modely, **zobecněný additive** modely a další.</span><span class="sxs-lookup"><span data-stu-id="e60be-152">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="e60be-153">Můžete najít další informace o modelů v [úlohy](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="e60be-153">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="e60be-154">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="e60be-154">Data preparation</span></span>

<span data-ttu-id="e60be-155">Ve většině případů se data, že máte k dispozici není vhodný pro použití přímo k natrénování modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e60be-155">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="e60be-156">Nezpracovaná data musí být připravené nebo předem zpracovaných předtím, než je možné najít parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="e60be-156">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="e60be-157">Vaše data potřebovat pro převod z řetězcových hodnot na číselné vyjádření.</span><span class="sxs-lookup"><span data-stu-id="e60be-157">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="e60be-158">Nadbytečné informace pravděpodobně ve vstupní data.</span><span class="sxs-lookup"><span data-stu-id="e60be-158">You might have redundant information in your input data.</span></span> <span data-ttu-id="e60be-159">Potřebujete omezit nebo rozšířit dimenze vstupní data.</span><span class="sxs-lookup"><span data-stu-id="e60be-159">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="e60be-160">Normalizovaná nebo škálování může být potřeba data.</span><span class="sxs-lookup"><span data-stu-id="e60be-160">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="e60be-161">[ML.NET kurzy](./tutorials/index.md) naučit vás o kanálů jiné zpracování dat pro text, image, číselná a časových řad dat pro úlohy konkrétních strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e60be-161">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="e60be-162">[Postup přípravy dat](./how-to-guides/prepare-data-ml-net.md) vám ukáže, jak na použita přípravu dat obecně.</span><span class="sxs-lookup"><span data-stu-id="e60be-162">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="e60be-163">Dodatek všech můžete najít [dostupných transformací](./resources/transforms.md) v části prostředky.</span><span class="sxs-lookup"><span data-stu-id="e60be-163">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="e60be-164">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="e60be-164">Model evaluation</span></span>

<span data-ttu-id="e60be-165">Jakmile máte Trénink modelu, jak poznáte, jak dobře budou předpovědi budoucích?</span><span class="sxs-lookup"><span data-stu-id="e60be-165">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="e60be-166">S ML.NET můžete si vyzkoušet model pro některé nové testovací data.</span><span class="sxs-lookup"><span data-stu-id="e60be-166">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="e60be-167">Každý typ úlohy machine learning má metriky k vyhodnocení, přesnost a přesnost modelu proti testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="e60be-167">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="e60be-168">V našem příkladu cena house jsme použili **regrese** úloh.</span><span class="sxs-lookup"><span data-stu-id="e60be-168">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="e60be-169">K vyhodnocení modelu, přidejte následující kód k původní ukázce.</span><span class="sxs-lookup"><span data-stu-id="e60be-169">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(houseData);
        var testPriceDataView = model.Transform(testHouseDataView);
                
        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.99
        // RMS error: 0.09
```

<span data-ttu-id="e60be-170">Metrik hodnocení říct, že chyba je low-ish a této korelace mezi výstup předpokládaná a výstup testu je vysoká.</span><span class="sxs-lookup"><span data-stu-id="e60be-170">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="e60be-171">To bylo snadné!</span><span class="sxs-lookup"><span data-stu-id="e60be-171">That was easy!</span></span> <span data-ttu-id="e60be-172">V reálné příkladech trvá další ladění k dosažení dobré modelu metriky.</span><span class="sxs-lookup"><span data-stu-id="e60be-172">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="e60be-173">Architektura ML.NET</span><span class="sxs-lookup"><span data-stu-id="e60be-173">ML.NET architecture</span></span>

<span data-ttu-id="e60be-174">V této části jsme projít architektury vzory ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e60be-174">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="e60be-175">Pokud jste vývojáři .NET, některé z těchto vzorců se se známými a některé budou méně známé.</span><span class="sxs-lookup"><span data-stu-id="e60be-175">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="e60be-176">Podržte vysoké, můžeme začít!</span><span class="sxs-lookup"><span data-stu-id="e60be-176">Hold tight, while we dive in!</span></span>

<span data-ttu-id="e60be-177">Aplikace ML.NET začíná <xref:Microsoft.ML.MLContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="e60be-177">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="e60be-178">Tento objekt typu singleton obsahuje **katalogy**.</span><span class="sxs-lookup"><span data-stu-id="e60be-178">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="e60be-179">Katalog je objekt pro vytváření dat, načítání a transformace, školitelé a součástí modelu operace ukládání.</span><span class="sxs-lookup"><span data-stu-id="e60be-179">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="e60be-180">Každý objekt katalogu má metody k vytvoření různých typů komponent:</span><span class="sxs-lookup"><span data-stu-id="e60be-180">Each catalog object has methods to create the different types of components:</span></span>

||||
|-|-|-|
|<span data-ttu-id="e60be-181">Ukládání a načítání dat</span><span class="sxs-lookup"><span data-stu-id="e60be-181">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>|
|<span data-ttu-id="e60be-182">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="e60be-182">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>|
|<span data-ttu-id="e60be-183">Trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="e60be-183">Training algorithms</span></span>|<span data-ttu-id="e60be-184">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="e60be-184">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>|
||<span data-ttu-id="e60be-185">Klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="e60be-185">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>|
||<span data-ttu-id="e60be-186">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="e60be-186">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>|
||<span data-ttu-id="e60be-187">Hodnocení</span><span class="sxs-lookup"><span data-stu-id="e60be-187">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>|
||<span data-ttu-id="e60be-188">Regrese</span><span class="sxs-lookup"><span data-stu-id="e60be-188">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>|
||<span data-ttu-id="e60be-189">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e60be-189">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|
|<span data-ttu-id="e60be-190">Využití modelu</span><span class="sxs-lookup"><span data-stu-id="e60be-190">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>|

<span data-ttu-id="e60be-191">Můžete přejít do metod vytváření v každé z výše uvedených kategoriích.</span><span class="sxs-lookup"><span data-stu-id="e60be-191">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="e60be-192">Pomocí sady Visual Studio, katalogy zobrazí prostřednictvím technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e60be-192">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Technologie IntelliSense pro školitele regrese](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="e60be-194">Vytvoření kanálu</span><span class="sxs-lookup"><span data-stu-id="e60be-194">Build the pipeline</span></span>

<span data-ttu-id="e60be-195">V každé katalogu je sadu rozšiřujících metod.</span><span class="sxs-lookup"><span data-stu-id="e60be-195">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="e60be-196">Podívejme se na použití rozšiřující metody k vytvoření kanálu školení.</span><span class="sxs-lookup"><span data-stu-id="e60be-196">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100);
```

<span data-ttu-id="e60be-197">V tomto fragmentu kódu `Concatenate` a `Sdca` jsou obě metody v katalogu.</span><span class="sxs-lookup"><span data-stu-id="e60be-197">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="e60be-198">Každá vytvořit [IEstimator](xref:Microsoft.ML.IEstimator`1) objekt, který se připojí k kanálu.</span><span class="sxs-lookup"><span data-stu-id="e60be-198">They each create an [IEstimator](xref:Microsoft.ML.IEstimator`1) object that is appended to the pipeline.</span></span>

<span data-ttu-id="e60be-199">Objekty v tomto okamžiku se vytvoří pouze.</span><span class="sxs-lookup"><span data-stu-id="e60be-199">At this point, the objects are created only.</span></span> <span data-ttu-id="e60be-200">Žádná spuštění se stalo.</span><span class="sxs-lookup"><span data-stu-id="e60be-200">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="e60be-201">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="e60be-201">Train the model</span></span>

<span data-ttu-id="e60be-202">Po vytvoření objektů v kanálu dat je možné pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="e60be-202">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="e60be-203">Volání `Fit()` používá vstupní trénovacích dat k odhadu parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="e60be-203">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="e60be-204">To se označuje jako trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="e60be-204">This is known as training the model.</span></span> <span data-ttu-id="e60be-205">Nezapomeňte, že výše uvedené trénování modelu lineární regrese má dva parametry modelu: **posun** a **váha**.</span><span class="sxs-lookup"><span data-stu-id="e60be-205">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="e60be-206">Po `Fit()` volání, jsou známé hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="e60be-206">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="e60be-207">Většina modely mají mnoho dalších parametrů, než to.</span><span class="sxs-lookup"><span data-stu-id="e60be-207">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="e60be-208">Další informace o tréninku modelu v [trénování modelu](./how-to-guides/train-machine-learning-model-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="e60be-208">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="e60be-209">Výsledný objekt modelu implementuje <xref:Microsoft.ML.ITransformer> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e60be-209">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="e60be-210">To znamená, že model transformuje vstupní data do predikce.</span><span class="sxs-lookup"><span data-stu-id="e60be-210">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="e60be-211">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="e60be-211">Use the model</span></span>

<span data-ttu-id="e60be-212">Najednou můžete transformovat vstupní data do predikce v hromadné nebo jeden vstup.</span><span class="sxs-lookup"><span data-stu-id="e60be-212">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="e60be-213">V příkladu cena house jsme to udělali obojí: hromadné pro účely vyhodnocení modelu a jeden po druhém vytvoří předpověď nového.</span><span class="sxs-lookup"><span data-stu-id="e60be-213">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="e60be-214">Podívejme se na provedení jednoho předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e60be-214">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = model.CreatePredictionEngine<HouseData, Prediction>(mlContext);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="e60be-215">`CreatePredictionEngine()` Metoda přijímá vstupní třídy a výstupu.</span><span class="sxs-lookup"><span data-stu-id="e60be-215">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="e60be-216">Názvy polí a/nebo atributy kódu určete názvy sloupců dat, použita během cvičení modelu a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e60be-216">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="e60be-217">Informace o [jak jeden předpověď](./how-to-guides/single-predict-model-ml-net.md) v části s postupy.</span><span class="sxs-lookup"><span data-stu-id="e60be-217">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="e60be-218">Datové modely a schématu</span><span class="sxs-lookup"><span data-stu-id="e60be-218">Data models and schema</span></span>

<span data-ttu-id="e60be-219">V jádru služby kanál ML.NET strojového učení se [DataView](xref:Microsoft.ML.IDataView) objekty.</span><span class="sxs-lookup"><span data-stu-id="e60be-219">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="e60be-220">Každá transformace v kanálu má vstupní schéma (názvy datových typů a velikostí, které transformací, která se očekává, že chcete zobrazit ve vzorci); a výstupní schéma (názvy datových typů a velikostí, mezi které transformací, která se vytváří po transformaci).</span><span class="sxs-lookup"><span data-stu-id="e60be-220">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> 

<span data-ttu-id="e60be-221">Pokud schéma výstupu z jedna transformace v kanálu neodpovídá schématu vstupu další transformace, ML.NET vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="e60be-221">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="e60be-222">Objekt dat zobrazení obsahuje sloupce a řádky.</span><span class="sxs-lookup"><span data-stu-id="e60be-222">A data view object has columns and rows.</span></span> <span data-ttu-id="e60be-223">Název a typ a délku má každý sloupec.</span><span class="sxs-lookup"><span data-stu-id="e60be-223">Each column has a name and a type and a length.</span></span> <span data-ttu-id="e60be-224">Příklad: vstupní sloupce v příkladu cena house **velikost** a **cena**.</span><span class="sxs-lookup"><span data-stu-id="e60be-224">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="e60be-225">Jsou obě zadání a že jsou skalární spíše než těch, které jsou vektorové.</span><span class="sxs-lookup"><span data-stu-id="e60be-225">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![Příklad zobrazení dat ML.NET s daty predikce ceny house](./media/ml-net-dataview.png)

<span data-ttu-id="e60be-227">Všechny algoritmy ML.NET hledejte vstupní sloupec, který je vektor.</span><span class="sxs-lookup"><span data-stu-id="e60be-227">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="e60be-228">Ve výchozím nastavení je volána v tomto sloupci vektoru **funkce**.</span><span class="sxs-lookup"><span data-stu-id="e60be-228">By default this vector column is called **Features**.</span></span> <span data-ttu-id="e60be-229">To je důvod, proč jsme zřetězeny **velikost** názvem sloupce do nového sloupce **funkce** v našem příkladu house cena.</span><span class="sxs-lookup"><span data-stu-id="e60be-229">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="e60be-230">Po provedení predikcí, všechny algoritmy také vytvářet nové sloupce.</span><span class="sxs-lookup"><span data-stu-id="e60be-230">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="e60be-231">Oprava názvy těchto nových sloupců závisí na typu algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e60be-231">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="e60be-232">Pro úlohu regrese jedna nové sloupce se nazývá **skóre**.</span><span class="sxs-lookup"><span data-stu-id="e60be-232">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="e60be-233">To je důvod, proč jsme s atributy naší cenové údaje s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="e60be-233">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="e60be-234">Můžete najít další informace o výstupní sloupce úloh různých strojového učení v [Machine Learning úlohy](resources/tasks.md) průvodce.</span><span class="sxs-lookup"><span data-stu-id="e60be-234">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="e60be-235">Důležité vlastnost DataView objekty je, že jsou vyhodnocovány **laxně**.</span><span class="sxs-lookup"><span data-stu-id="e60be-235">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="e60be-236">Zobrazení dat jsou pouze načíst a zpracovat. během cvičení modelu a vyhodnocení a data předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e60be-236">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="e60be-237">Při psaní a testování vaší aplikace ML.NET ladicího programu sady Visual Studio můžete provést náhled na libovolný objekt dat zobrazení pomocí volání [ve verzi Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) metody.</span><span class="sxs-lookup"><span data-stu-id="e60be-237">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="e60be-238">Můžete se podívat `debug` proměnné v ladicím programu a prozkoumat její obsah.</span><span class="sxs-lookup"><span data-stu-id="e60be-238">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="e60be-239">Nepoužívejte metodu ve verzi Preview v produkčním kódu, protože výrazně snižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="e60be-239">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="e60be-240">Nasazení modelu</span><span class="sxs-lookup"><span data-stu-id="e60be-240">Model Deployment</span></span>

<span data-ttu-id="e60be-241">V reálné aplikace bude váš kód trénování a vyhodnocování modelu nezávisle na predikci.</span><span class="sxs-lookup"><span data-stu-id="e60be-241">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="e60be-242">Ve skutečnosti, že obě aktivity často provádějí mají samostatné týmy.</span><span class="sxs-lookup"><span data-stu-id="e60be-242">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="e60be-243">Váš vývojový tým modelu můžete uložit model pro použití v aplikaci předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e60be-243">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="e60be-244">Kam chcete nyní?</span><span class="sxs-lookup"><span data-stu-id="e60be-244">Where to now?</span></span>

<span data-ttu-id="e60be-245">Zjistěte, jak vytvářet aplikace pomocí úlohy různých strojového učení s víc odpovídají realitě datovými sadami v [kurzy](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="e60be-245">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="e60be-246">Nebo můžete informace o konkrétních tématech v části [příručky a návody](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="e60be-246">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="e60be-247">A pokud je pro vás velmi webu, můžete rovnou přímo do [dokumentaci Reference k rozhraní API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span><span class="sxs-lookup"><span data-stu-id="e60be-247">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>