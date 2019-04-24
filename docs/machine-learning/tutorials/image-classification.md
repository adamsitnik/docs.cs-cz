---
title: Sestavení klasifikátoru vlastní image ML.NET s TensorFlow
description: Objevte, jak vytvářet třídění ML.NET vlastní image ve TensorFlow přenos učení scénář klasifikace obrázků opětovným použitím předem natrénovaných modelů TensorFlow.
ms.date: 04/05/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9b9ac1f1f15b4003a19a3d30d6cadf3e86946376
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517964"
---
# <a name="tutorial-build-an-mlnet-custom-image-classifier-with-tensorflow"></a><span data-ttu-id="95a7b-103">Kurz: Sestavení klasifikátoru vlastní image ML.NET s TensorFlow</span><span class="sxs-lookup"><span data-stu-id="95a7b-103">Tutorial: Build an ML.NET custom image classifier with TensorFlow</span></span>

<span data-ttu-id="95a7b-104">Tento ukázkový kurz ukazuje, jak můžete používat již trénovaného třídění Image `TensorFlow` modelu k vytvoření nového vlastního modelu pro klasifikaci obrázků do několika kategorií.</span><span class="sxs-lookup"><span data-stu-id="95a7b-104">This sample tutorial illustrates how you can use an already trained Image Classifier `TensorFlow` model to build a new custom model to classify images into a few categories.</span></span>

<span data-ttu-id="95a7b-105">Co když můžete znovu použít model, který již byl před vyškolit tak, aby podobný problém vyřešit a přeučování všechny nebo některé z vrstev tento model, aby byl váš problém vyřešit?</span><span class="sxs-lookup"><span data-stu-id="95a7b-105">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="95a7b-106">Opětovné použití součást již trénovaného modelu vytvoříte nový model Tato technika se nazývá [přenos learning](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="95a7b-106">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

<span data-ttu-id="95a7b-107">Školení [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model úplně od začátku vyžaduje nastavení miliony parametry, spoustu s popiskem trénovacích dat a velké množství výpočetních prostředků (vzdálené stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="95a7b-107">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="95a7b-108">Přestože není tak účinné jako trénujete model pro vlastní úplně od začátku, learningu vám umožní místní tento proces při práci s tisíci imagí a miliony označené obrázky a poměrně rychle vytvářet vlastní model (za hodinu na počítači bez GPU).</span><span class="sxs-lookup"><span data-stu-id="95a7b-108">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="95a7b-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="95a7b-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="95a7b-110">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="95a7b-110">Understand the problem</span></span>
> * <span data-ttu-id="95a7b-111">Opakovaně používat a vyladit předem natrénovaných modelů</span><span class="sxs-lookup"><span data-stu-id="95a7b-111">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="95a7b-112">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="95a7b-112">Classify Images</span></span>

> [!NOTE]
> <span data-ttu-id="95a7b-113">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="95a7b-113">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="95a7b-114">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="95a7b-114">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="95a7b-115">Tento kurz a související ukázkové právě používáte **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-115">This tutorial and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="95a7b-116">Další informace najdete v tématu poznámky k verzi v [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="95a7b-116">For more information, see the release notes at the [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) GitHub repository.</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="95a7b-117">Přehled ukázky klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="95a7b-117">Image classification sample overview</span></span>

<span data-ttu-id="95a7b-118">Ukázka je konzolová aplikace, která používá ML.NET k sestavení třídění image opětovným použitím předem vytrénovaných model pro klasifikaci obrázků s menším objemem trénovací data.</span><span class="sxs-lookup"><span data-stu-id="95a7b-118">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="95a7b-119">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) úložiště.</span><span class="sxs-lookup"><span data-stu-id="95a7b-119">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95a7b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95a7b-120">Prerequisites</span></span>

* <span data-ttu-id="95a7b-121">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="95a7b-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="95a7b-122">Balíček Nuget Microsoft.ML 0.10.0</span><span class="sxs-lookup"><span data-stu-id="95a7b-122">Microsoft.ML 0.10.0 Nuget package</span></span>
* <span data-ttu-id="95a7b-123">Balíček Nuget Microsoft.ML.ImageAnalytics 0.10.0</span><span class="sxs-lookup"><span data-stu-id="95a7b-123">Microsoft.ML.ImageAnalytics 0.10.0 Nuget package</span></span>
* <span data-ttu-id="95a7b-124">Balíček Nuget Microsoft.ML.TensorFlow 0.10.0</span><span class="sxs-lookup"><span data-stu-id="95a7b-124">Microsoft.ML.TensorFlow 0.10.0 Nuget package</span></span>

* [<span data-ttu-id="95a7b-125">Adresář, který kurzů aktiv. Soubor ZIP</span><span class="sxs-lookup"><span data-stu-id="95a7b-125">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="95a7b-126">Model InceptionV3 strojového učení</span><span class="sxs-lookup"><span data-stu-id="95a7b-126">The InceptionV3 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="95a7b-127">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="95a7b-127">Select the appropriate machine learning task</span></span>

<span data-ttu-id="95a7b-128">[Obsáhlý learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, která je revolutionizing oblastem, jako pro počítačové zpracování obrazu a řeči.</span><span class="sxs-lookup"><span data-stu-id="95a7b-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="95a7b-129">Obsáhlý learning jsou trénované modely s využitím velkých sad [označené data](https://en.wikipedia.org/wiki/Labeled_data) a [neuronových sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více vrstev učení.</span><span class="sxs-lookup"><span data-stu-id="95a7b-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="95a7b-130">Obsáhlý learning:</span><span class="sxs-lookup"><span data-stu-id="95a7b-130">Deep learning:</span></span>

* <span data-ttu-id="95a7b-131">Na některé úkoly, jako je pro počítačové zpracování obrazu vrací lepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="95a7b-131">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="95a7b-132">Provádí také data obrovské objemy.</span><span class="sxs-lookup"><span data-stu-id="95a7b-132">Performs well on huge data amounts.</span></span>

<span data-ttu-id="95a7b-133">Klasifikace obrázků je běžný úkol Machine Learning, která umožňuje automaticky klasifikovat bitové kopie do více kategorií, jako například:</span><span class="sxs-lookup"><span data-stu-id="95a7b-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="95a7b-134">Detekuje lidské tváře v obrázku nebo ne.</span><span class="sxs-lookup"><span data-stu-id="95a7b-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="95a7b-135">Zjišťování koček a psů.</span><span class="sxs-lookup"><span data-stu-id="95a7b-135">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="95a7b-136">Nebo jako v následujících imagí zjištění, zda je bitová kopie položku food, hračka nebo zařízení:</span><span class="sxs-lookup"><span data-stu-id="95a7b-136">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="95a7b-137">![Obrázek pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![míša opatřeny image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="95a7b-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="95a7b-138">Předchozí obrázky Commons o Wikimedia patří a mají atributy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="95a7b-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="95a7b-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="95a7b-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="95a7b-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" podle [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) -svým fotografovali kopie BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="95a7b-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="95a7b-141">"193px-Broodrooster.jpg" podle [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) – vlastní práci, CC BY SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="95a7b-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="95a7b-142">Přenos learning obsahuje několik strategií, jako například *přeučování všechny vrstvy* a *předposlední vrstvy*.</span><span class="sxs-lookup"><span data-stu-id="95a7b-142">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="95a7b-143">V tomto kurzu se vysvětlují, ukazují, jak používat *předposlední vrstvy strategie*.</span><span class="sxs-lookup"><span data-stu-id="95a7b-143">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="95a7b-144">*Předposlední vrstvy strategie* opětovně používá model, který je již předběžně školení k vyřešení konkrétního problému.</span><span class="sxs-lookup"><span data-stu-id="95a7b-144">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="95a7b-145">Strategie pak retrains poslední vrstva tohoto modelu k němu nový problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="95a7b-145">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="95a7b-146">Opětovné použití předem natrénovaných modelů jako součást nového modelu vám ušetří spoustu času a prostředků.</span><span class="sxs-lookup"><span data-stu-id="95a7b-146">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="95a7b-147">Opětovně používá model klasifikace obrázků [vzniku modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), model rozpoznávání image Oblíbené trénovaných na `ImageNet` datovou sadu, ve kterém modelu TensorFlow pokusí o klasifikaci celého Image na tisíc třídy, jako je třeba " Zastřešující","Jersey"a"Nádobí".</span><span class="sxs-lookup"><span data-stu-id="95a7b-147">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="95a7b-148">`Inception v3 model` Dají považovat za [hluboké konvoluční neuronové sítě](https://en.wikipedia.org/wiki/Convolutional_neural_network) a dosáhnout adekvátní výkon na pevné visual rozpoznávání úloh, odpovídající nebo překročení lidské výkonu v některé domény.</span><span class="sxs-lookup"><span data-stu-id="95a7b-148">The `Inception v3 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="95a7b-149">/ Algoritmem modelu byla vypracovanou organizací cccppf více výzkumní pracovníci a podle původního dokumentu: ["Jiný pohled na architekturu zahájení pro počítačové zpracování obrazu" podle Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="95a7b-149">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="95a7b-150">Protože `Inception model` již byl před trénovaných na tisíce jinou Image, obsahuje [obrázku funkce](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné k identifikaci image.</span><span class="sxs-lookup"><span data-stu-id="95a7b-150">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="95a7b-151">Nižších vrstvách funkce image rozpoznat jednoduché funkce (například okraje) a vyšší vrstvy rozpoznávání podobě komplexních funkcí (jako je například tvary).</span><span class="sxs-lookup"><span data-stu-id="95a7b-151">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="95a7b-152">Poslední vrstva se trénuje proti mnohem menší sady dat, vzhledem k tomu, že začínáte s pre trénovaného modelu, která již analyzuje jak klasifikovat bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="95a7b-152">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="95a7b-153">Jako model umožňuje klasifikovat více než dvě kategorie, toto je příklad [roc třídění](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="95a7b-153">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="95a7b-154">`TensorFlow` je oblíbená obsáhlého learningu a nástrojů strojového učení pro školení hluboké neuronové sítě (a obecné numerické výpočty) a je implementovaný jako `transformer` v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="95a7b-154">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="95a7b-155">V tomto kurzu se používá pro opětovné použití `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-155">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="95a7b-156">Jak je znázorněno v následujícím diagramu, přidejte odkaz na balíčky ML.NET NuGet v aplikacích .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95a7b-156">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="95a7b-157">Pod pokličkou, ML.NET zahrnuje a odkazuje na nativní `TensorFlow` knihovnu, která umožňuje napsat kód, který načte existující školení `TensorFlow` souboru modelu pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="95a7b-157">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Transformace TensorFlow ML.NET Arch diagramu](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="95a7b-159">`Inception model` Trénovaných ke klasifikaci obrázků do tisíce kategorií, ale je potřeba klasifikace obrázků v menší sadu kategorií a pouze tyto kategorie.</span><span class="sxs-lookup"><span data-stu-id="95a7b-159">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="95a7b-160">Zadejte `transfer` součástí `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-160">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="95a7b-161">Můžete převést `Inception model`vaší schopnost rozpoznat a klasifikace obrázků na nové omezené kategorie klasifikátoru vlastní image.</span><span class="sxs-lookup"><span data-stu-id="95a7b-161">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="95a7b-162">Chystáte se přeučování poslední vrstva tohoto modelu používáte sadu tří kategorií:</span><span class="sxs-lookup"><span data-stu-id="95a7b-162">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="95a7b-163">Potravinářství</span><span class="sxs-lookup"><span data-stu-id="95a7b-163">Food</span></span>
* <span data-ttu-id="95a7b-164">Hračka</span><span class="sxs-lookup"><span data-stu-id="95a7b-164">Toy</span></span>
* <span data-ttu-id="95a7b-165">Zařízení</span><span class="sxs-lookup"><span data-stu-id="95a7b-165">Appliance</span></span>

<span data-ttu-id="95a7b-166">Používá vaše vrstvy [algoritmu logistické regrese multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) co nejrychleji najít správnou kategorii.</span><span class="sxs-lookup"><span data-stu-id="95a7b-166">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="95a7b-167">Tento algoritmus klasifikuje pomocí pravděpodobnosti určit odpověď, poskytuje jednu hodnotu na správnou kategorii a nulová hodnota ostatním.</span><span class="sxs-lookup"><span data-stu-id="95a7b-167">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="95a7b-168">DataSet</span><span class="sxs-lookup"><span data-stu-id="95a7b-168">DataSet</span></span>

<span data-ttu-id="95a7b-169">Existují dva zdroje dat: `.tsv` souborů a souborů obrázků.</span><span class="sxs-lookup"><span data-stu-id="95a7b-169">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="95a7b-170">`tags.tsv` Soubor obsahuje dva sloupce: první z nich je definován jako `ImagePath` a druhý je `Label` odpovídající do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="95a7b-170">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="95a7b-171">Následující příklad souboru nemá řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="95a7b-171">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="95a7b-172">Trénovací a testovací bitové kopie jsou umístěny ve složkách prostředky, které budete stáhnout jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="95a7b-172">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="95a7b-173">Tyto Image patří do Commons o Wikimedia.</span><span class="sxs-lookup"><span data-stu-id="95a7b-173">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="95a7b-174">*[Commons o Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), úložiště volných médií.*</span><span class="sxs-lookup"><span data-stu-id="95a7b-174">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="95a7b-175">Načtená 10:48, 17. října 2018 od:</span><span class="sxs-lookup"><span data-stu-id="95a7b-175">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="95a7b-176">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="95a7b-176">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="95a7b-177">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="95a7b-177">Create a project</span></span>

1. <span data-ttu-id="95a7b-178">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="95a7b-178">Open Visual Studio 2017.</span></span> <span data-ttu-id="95a7b-179">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="95a7b-179">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="95a7b-180">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-180">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="95a7b-181">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-181">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="95a7b-182">V **název** textového pole zadejte "TransferLearningTF" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="95a7b-182">In the **Name** text box, type "TransferLearningTF" and then select the **OK** button.</span></span>

2. <span data-ttu-id="95a7b-183">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="95a7b-183">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="95a7b-184">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-184">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="95a7b-185">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-185">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="95a7b-186">Klikněte na **verze** rozevíracího seznamu, vyberte **0.10.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="95a7b-186">Click on the **Version** drop-down, select the **0.10.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="95a7b-187">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="95a7b-187">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="95a7b-188">Opakujte tyto kroky pro **Microsoft.ML.ImageAnalytics v0.10.0** a **Microsoft.ML.TensorFlow v0.10.0**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-188">Repeat these steps for **Microsoft.ML.ImageAnalytics v0.10.0** and **Microsoft.ML.TensorFlow v0.10.0**.</span></span>

  > [!NOTE]
  > <span data-ttu-id="95a7b-189">Tento kurz používá **Microsoft.ML v0.10.0**, **Microsoft.ML.ImageAnalytics v0.10.0**, a **Microsoft.ML.TensorFlow v0.10.0**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-189">This tutorial uses **Microsoft.ML v0.10.0**, **Microsoft.ML.ImageAnalytics v0.10.0**, and **Microsoft.ML.TensorFlow v0.10.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="95a7b-190">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="95a7b-190">Prepare your data</span></span>

1. <span data-ttu-id="95a7b-191">Stáhněte si [souboru zip projektu prostředků adresáře](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="95a7b-191">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="95a7b-192">Kopírovat `assets` adresáře do vašeho *TransferLearningTF* adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-192">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="95a7b-193">Tento adresář a jeho podadresářích obsahovat soubory dat a podporu (s výjimkou vzniku modelu, který budete stáhnout a přidat v dalším kroku) pro tento kurz potřeba.</span><span class="sxs-lookup"><span data-stu-id="95a7b-193">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="95a7b-194">Stáhněte si [vzniku modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="95a7b-194">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="95a7b-195">Zkopírujte obsah `inception5h` rozzipoval. stačí do adresáře vašeho *TransferLearningTF* projektu `assets\inputs-train\inception` adresáře.</span><span class="sxs-lookup"><span data-stu-id="95a7b-195">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="95a7b-196">Tento adresář obsahuje model a další podpůrné soubory pro tento kurz potřeba, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="95a7b-196">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Obsah adresáře zahájení](./media/image-classification/inception-files.png)

5. <span data-ttu-id="95a7b-198">V Průzkumníku řešení klikněte pravým tlačítkem myši na každém ze souborů v majetku adresáře a podadresářů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-198">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="95a7b-199">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-199">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="95a7b-200">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="95a7b-200">Create classes and define paths</span></span>

<span data-ttu-id="95a7b-201">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="95a7b-201">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="95a7b-202">Vytvořte globální pole pro uložení cest k různým prostředkům a globálních proměnných pro `LabelTokey`,`ImageReal`, a `PredictedLabelValue`:</span><span class="sxs-lookup"><span data-stu-id="95a7b-202">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="95a7b-203">`_assetsPath` obsahuje cestu k prostředky.</span><span class="sxs-lookup"><span data-stu-id="95a7b-203">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="95a7b-204">`_trainTagsTsv` má cestu k souboru tsv školení image data značek.</span><span class="sxs-lookup"><span data-stu-id="95a7b-204">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="95a7b-205">`_predictTagsTsv` má cestu k souboru tsv předpovědi image data značek.</span><span class="sxs-lookup"><span data-stu-id="95a7b-205">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="95a7b-206">`_trainImagesFolder` obsahuje v cestě k obrázkům využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-206">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="95a7b-207">`_predictImagesFolder` obsahuje v cestě k obrázkům zařazují trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-207">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="95a7b-208">`_inceptionPb` obsahuje cestu k předem vytrénovaných vzniku model znovu použije k přeučování modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-208">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="95a7b-209">`_inputImageClassifierZip` má cesta kde trénovaný model je načtený z.</span><span class="sxs-lookup"><span data-stu-id="95a7b-209">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="95a7b-210">`_outputImageClassifierZip` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-210">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="95a7b-211">`LabelTokey` je `Label` hodnotu namapovány na klíče.</span><span class="sxs-lookup"><span data-stu-id="95a7b-211">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="95a7b-212">`ImageReal`  je sloupec obsahující hodnotu předpokládané obrázku.</span><span class="sxs-lookup"><span data-stu-id="95a7b-212">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="95a7b-213">`PredictedLabelValue` je sloupec obsahující hodnoty předpovězené popisku.</span><span class="sxs-lookup"><span data-stu-id="95a7b-213">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="95a7b-214">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="95a7b-214">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="95a7b-215">Vytvořte některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="95a7b-215">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="95a7b-216">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-216">Add a new class to your project:</span></span>

1. <span data-ttu-id="95a7b-217">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-217">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="95a7b-218">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="95a7b-218">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="95a7b-219">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="95a7b-219">Then, select the **Add** button.</span></span>

    <span data-ttu-id="95a7b-220">*ImageData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-220">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="95a7b-221">Přidejte následující `using` příkaz do horní části *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="95a7b-221">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="95a7b-222">Odeberte stávající definice třídy a přidejte následující kód `ImageData` třídu *ImageData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="95a7b-222">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="95a7b-223">`ImageData` je třída dat vstupního obrázku a má následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="95a7b-223">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="95a7b-224">`ImagePath` obsahuje název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="95a7b-224">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="95a7b-225">`Label` obsahuje hodnotu pro popisek image.</span><span class="sxs-lookup"><span data-stu-id="95a7b-225">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="95a7b-226">Přidejte novou třídu do projektu pro `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="95a7b-226">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="95a7b-227">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="95a7b-227">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="95a7b-228">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="95a7b-228">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="95a7b-229">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="95a7b-229">Then, select the **Add** button.</span></span>

    <span data-ttu-id="95a7b-230">*ImagePrediction.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-230">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="95a7b-231">Odebrat i `System.Collections.Generic` a `System.Text` `using` příkazů v horní části *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="95a7b-231">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="95a7b-232">Odeberte stávající definice třídy a přidejte následující kód, který má `ImagePrediction` do třídy *ImagePrediction.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="95a7b-232">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="95a7b-233">`ImagePrediction` je třída prediktivní vkládání obrázků a obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="95a7b-233">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="95a7b-234">`Score` obsahuje procento spolehlivosti pro danou image klasifikaci.</span><span class="sxs-lookup"><span data-stu-id="95a7b-234">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="95a7b-235">`PredictedLabelValue` obsahuje hodnotu pro popisek klasifikace předpokládané image.</span><span class="sxs-lookup"><span data-stu-id="95a7b-235">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="95a7b-236">`ImagePrediction` Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="95a7b-236">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="95a7b-237">Má `string` (`ImagePath`) pro cestu k obrázku.</span><span class="sxs-lookup"><span data-stu-id="95a7b-237">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="95a7b-238">`Label` Se používá pro opětovné použití přeučování modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-238">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="95a7b-239">`PredictedLabelValue` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="95a7b-239">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="95a7b-240">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="95a7b-240">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="95a7b-241">[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-241">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="95a7b-242">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="95a7b-242">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="95a7b-243">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="95a7b-243">Initialize variables in Main</span></span>

<span data-ttu-id="95a7b-244">Inicializovat `mlContext` proměnné s novou instanci třídy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-244">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="95a7b-245">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-245">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="95a7b-246">Vytvořte strukturu pro výchozí parametry</span><span class="sxs-lookup"><span data-stu-id="95a7b-246">Create a struct for default parameters</span></span>

<span data-ttu-id="95a7b-247">Zahájení model má několik výchozích parametrů, které je potřeba předat.</span><span class="sxs-lookup"><span data-stu-id="95a7b-247">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="95a7b-248">Vytvořte strukturu pro mapování výchozí hodnoty parametrů pro popisných názvů následujícím kódem, bezprostředně po `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-248">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="95a7b-249">Vytvořit metodu nástroj zobrazení</span><span class="sxs-lookup"><span data-stu-id="95a7b-249">Create a display utility method</span></span>

<span data-ttu-id="95a7b-250">Párování a zobrazení dat obrázků a související predikcí více než jednou a nechcete duplicitní kód.</span><span class="sxs-lookup"><span data-stu-id="95a7b-250">Pair and display the image data and the related predictions more than once, and you don't want to duplicate code.</span></span> <span data-ttu-id="95a7b-251">Vytvořte zobrazení nástroje metodu ke zpracování párování a zobrazení výsledků image a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="95a7b-251">Create a display utility method to handle pairing and displaying the image and prediction results.</span></span>

<span data-ttu-id="95a7b-252">`PairAndDisplayResults()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="95a7b-252">The `PairAndDisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="95a7b-253">Kombinací dat a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="95a7b-253">Combines data and predictions for reporting.</span></span>
* <span data-ttu-id="95a7b-254">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="95a7b-254">Displays the predicted results.</span></span>

<span data-ttu-id="95a7b-255">Vytvořte `PairAndDisplayResults()` metoda, hned za `InceptionSettings` struktury, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-255">Create the `PairAndDisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void PairAndDisplayResults(IEnumerable<ImageNetData> imageData, IEnumerable<ImageNetPrediction> imagePredictionData)
{

}
```

<span data-ttu-id="95a7b-256">Před zobrazením předpokládané výsledky, kombinovat `imageData` a `imagePrediction` společně zobrazíte původní `Image Path` s jeho předpokládané kategorie.</span><span class="sxs-lookup"><span data-stu-id="95a7b-256">Before displaying the predicted results, combine the `imageData` and `imagePrediction` together to see the original `Image Path` with its predicted category.</span></span> <span data-ttu-id="95a7b-257">Následující kód používá <xref:System.Linq.Enumerable.Zip%2A?displayProperty=nameWithType> metoda docílit, takže přidejte jako první řádek `PairAndDisplayResults()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-257">The following code uses the <xref:System.Linq.Enumerable.Zip%2A?displayProperty=nameWithType> method to make that happen, so add it as the first line of the `PairAndDisplayResults()` method:</span></span>

[!code-csharp[BuildImagePredictionPairs](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#BuildImagePredictionPairs)]

<span data-ttu-id="95a7b-258">Teď, když jste kombinovat `imageData` a `imageData` do třídy, můžete zobrazit výsledky pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-258">Now that you've combined the `imageData` and `imageData` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="95a7b-259">Budete volat `PairAndDisplayResults()` metoda v následujících dvou metod.</span><span class="sxs-lookup"><span data-stu-id="95a7b-259">You'll call the `PairAndDisplayResults()` method in the next two methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="95a7b-260">Vytvořit metodu nástroj soubor TSV</span><span class="sxs-lookup"><span data-stu-id="95a7b-260">Create a .tsv file utility method</span></span>

<span data-ttu-id="95a7b-261">`ReadFromTsv()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="95a7b-261">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="95a7b-262">Přečte data bitové kopie `tags.tsv` souboru.</span><span class="sxs-lookup"><span data-stu-id="95a7b-262">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="95a7b-263">Cesta k souboru se přidá k názvu souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="95a7b-263">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="95a7b-264">Načte datový soubor do použití rozhraní IEnumerable`ImageData` objektu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-264">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="95a7b-265">Vytvořte `ReadFromTsv()` metoda, hned za `PairAndDisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-265">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="95a7b-266">Následující kód analyzuje prostřednictvím `tags.tsv` soubor a přidejte cestu k souboru na název souboru obrázku `ImagePath` vlastnost a načtěte ho a `Label` do `ImageData` objektu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-266">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="95a7b-267">Přidejte jako první řádek `ReadFromTsv()` metody.</span><span class="sxs-lookup"><span data-stu-id="95a7b-267">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="95a7b-268">Budete potřebovat plně kvalifikovanou cestu k zobrazení výsledků předpovědí.</span><span class="sxs-lookup"><span data-stu-id="95a7b-268">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="95a7b-269">Existují tři hlavní koncepty v ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [transformátory](../basic-concepts-model-training-in-mldotnet.md#transformer), a [odhady](../basic-concepts-model-training-in-mldotnet.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="95a7b-269">There are three major concepts in ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [Transformers](../basic-concepts-model-training-in-mldotnet.md#transformer), and [Estimators](../basic-concepts-model-training-in-mldotnet.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="95a7b-270">Opakovaně používat a vyladit předem natrénovaných modelů</span><span class="sxs-lookup"><span data-stu-id="95a7b-270">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="95a7b-271">Přidejte následující volání `ReuseAndTuneInceptionModel()`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-271">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="95a7b-272">`ReuseAndTuneInceptionModel()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="95a7b-272">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="95a7b-273">Načte data</span><span class="sxs-lookup"><span data-stu-id="95a7b-273">Loads the data</span></span>
* <span data-ttu-id="95a7b-274">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="95a7b-274">Extracts and transforms the data.</span></span>
* <span data-ttu-id="95a7b-275">Stanoví skóre TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="95a7b-275">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="95a7b-276">Vyladí (retrains) modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-276">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="95a7b-277">Zobrazí výsledky modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-277">Displays model results.</span></span>
* <span data-ttu-id="95a7b-278">Vyhodnotí modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-278">Evaluates the model.</span></span>
* <span data-ttu-id="95a7b-279">Uloží modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-279">Saves the model.</span></span>

<span data-ttu-id="95a7b-280">Vytvořit `ReuseAndTuneInceptionModel()` metoda, hned za `InceptionSettings` struktury a těsně před `PairAndDisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-280">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="95a7b-281">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="95a7b-281">Load the data</span></span>

<span data-ttu-id="95a7b-282">Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.Data.DataView.IDataView).</span><span class="sxs-lookup"><span data-stu-id="95a7b-282">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.Data.DataView.IDataView).</span></span> <span data-ttu-id="95a7b-283">`IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové).</span><span class="sxs-lookup"><span data-stu-id="95a7b-283">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="95a7b-284">Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-284">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="95a7b-285">Načtení dat pomocí `MLContext.Data.ReadFromTextFile` obálky.</span><span class="sxs-lookup"><span data-stu-id="95a7b-285">Load the data using the `MLContext.Data.ReadFromTextFile` wrapper.</span></span> <span data-ttu-id="95a7b-286">Přidejte následující kód jako další řádek `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-286">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="95a7b-287">Extrakce funkce a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="95a7b-287">Extract Features and transform the data</span></span>

<span data-ttu-id="95a7b-288">Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="95a7b-288">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="95a7b-289">Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="95a7b-289">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="95a7b-290">Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) dat, a při práci s hluboké neuronové sítě musí přizpůsobit imagí do formátu očekávaném v síti.</span><span class="sxs-lookup"><span data-stu-id="95a7b-290">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="95a7b-291">Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="95a7b-291">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="95a7b-292">Po trénování a hodnocení předpovědět **popisek** hodnot sloupců.</span><span class="sxs-lookup"><span data-stu-id="95a7b-292">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="95a7b-293">Jak při použití předem natrénovaných modelů, mapování polí na nový model [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="95a7b-293">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="95a7b-294">Tato metoda transformuje `Label` na číselný typ klíče (`LabelTokey`) sloupce a přidejte ho jako nový sloupec datové sady:  Pojmenujte toto `estimator` jako také přidáte školitele k němu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-294">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="95a7b-295">Přidáte další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-295">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="95a7b-296">Váš odhad používá předem pro zpracování obrázků [hluboké Neuronové Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers pro extrakci funkce.</span><span class="sxs-lookup"><span data-stu-id="95a7b-296">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="95a7b-297">Při zpracování komplexnějších hluboké neuronové sítě, můžete přizpůsobit bitové kopie do formátu očekávanému sítě.</span><span class="sxs-lookup"><span data-stu-id="95a7b-297">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="95a7b-298">To je důvod, že použití několika transformací bitové kopie k načtení dat obrázků do očekávanému vzoru:</span><span class="sxs-lookup"><span data-stu-id="95a7b-298">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="95a7b-299">`LoadImages`Transformace obrázky jsou načtena do paměti jako typ rastrového obrázku.</span><span class="sxs-lookup"><span data-stu-id="95a7b-299">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="95a7b-300">`Resize` Transformace změní velikost obrázků předem natrénovaných modelů má definovaný vstupní image šířku a výšku.</span><span class="sxs-lookup"><span data-stu-id="95a7b-300">The `Resize` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="95a7b-301">`ImagePixelExtractingEstimator` Transformace extrahuje pixely ze vstupní Image a převede je na číselné vektoru.</span><span class="sxs-lookup"><span data-stu-id="95a7b-301">The `ImagePixelExtractingEstimator` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="95a7b-302">Přidejte tyto image transformace jako další řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-302">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="95a7b-303">`TensorFlowTransform` Výpisy zadaný výstupy ( `Inception model`vaší image funkce `softmax2_pre_activation`) a stanoví skóre datové sady pomocí předem vytrénovaných `TensorFlow` modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-303">The `TensorFlowTransform` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="95a7b-304">`softmax2_pre_activation` sestavit model k zjištění, které třída obrázků patří.</span><span class="sxs-lookup"><span data-stu-id="95a7b-304">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="95a7b-305">`softmax2_pre_activation` vrací pravděpodobnost pro každou kategorii pro bitovou kopii a ve všech těchto pravděpodobností musíte přidat až 1.</span><span class="sxs-lookup"><span data-stu-id="95a7b-305">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="95a7b-306">Předpokládá, že obraz bude patřit pouze jednu kategorii, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-306">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="95a7b-307">Třída</span><span class="sxs-lookup"><span data-stu-id="95a7b-307">Class</span></span>         | <span data-ttu-id="95a7b-308">Pravděpodobnost</span><span class="sxs-lookup"><span data-stu-id="95a7b-308">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="95a7b-309">0.001</span><span class="sxs-lookup"><span data-stu-id="95a7b-309">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="95a7b-310">0.95</span><span class="sxs-lookup"><span data-stu-id="95a7b-310">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="95a7b-311">0,06</span><span class="sxs-lookup"><span data-stu-id="95a7b-311">0.06</span></span>         |

<span data-ttu-id="95a7b-312">Připojte `TensorFlowTransform` k `estimator` s následující řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-312">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="95a7b-313">Zvolte cvičení algoritmu</span><span class="sxs-lookup"><span data-stu-id="95a7b-313">Choose a training algorithm</span></span>

<span data-ttu-id="95a7b-314">Chcete-li přidat cvičení algoritmu, zavolejte `mlContext.MulticlassClassification.Trainers.LogisticRegression()` obalující metodu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-314">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LogisticRegression()` wrapper method.</span></span>  <span data-ttu-id="95a7b-315">`LogisticRegression` Se připojí `estimator` a přijímá funkce vzniku bitové kopie (`softmax2_pre_activation`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="95a7b-315">The `LogisticRegression` is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="95a7b-316">Přidáte trainer následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="95a7b-316">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="95a7b-317">Je také nutné `predictedlabel` k `predictedlabelvalue`:</span><span class="sxs-lookup"><span data-stu-id="95a7b-317">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="95a7b-318">`Fit()` Metoda trénovat modelu pomocí zadaného trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="95a7b-318">The `Fit()` method trains your model with the provided training dataset.</span></span> <span data-ttu-id="95a7b-319">Je spuštěn `Estimator` definice transformace dat a použitím školení a vrátí zpět trénovaného modelu, který je `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-319">It executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span> <span data-ttu-id="95a7b-320">Přizpůsobit modelu, který má `Train` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-320">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="95a7b-321">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda vytváří předpovědi pro více poskytuje vstupní řádky z datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="95a7b-321">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="95a7b-322">Transformace `Training` data přidáním následujícího kódu do `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="95a7b-322">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="95a7b-323">Převod dat obrázků a předpovědi `DataViews` do silného typu `IEnumerables` spárovat pro snadnější zobrazení.</span><span class="sxs-lookup"><span data-stu-id="95a7b-323">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="95a7b-324">Použití `MLContext.CreateEnumerable()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-324">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="95a7b-325">Volání `PairAndDisplayResults()` metodu spárovat a zobrazení vašich dat a předpovědi jako další řádek v `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-325">Call the `PairAndDisplayResults()` method to pair and display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallPairAndDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults1)]

<span data-ttu-id="95a7b-326">Jakmile budete mít předpovědi nastavit, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-326">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="95a7b-327">Posuzuje modelu (porovná předpovězené hodnoty v datové sadě skutečná `Labels`).</span><span class="sxs-lookup"><span data-stu-id="95a7b-327">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="95a7b-328">Vrátí metriky výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-328">Returns the model performance metrics.</span></span> 

<span data-ttu-id="95a7b-329">Přidejte následující kód, který `ReuseAndTuneInceptionModel()` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="95a7b-329">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="95a7b-330">Klasifikace obrázků, se vyhodnotí následující metriky:</span><span class="sxs-lookup"><span data-stu-id="95a7b-330">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="95a7b-331">`Log-loss` -naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="95a7b-331">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="95a7b-332">Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="95a7b-332">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="95a7b-333">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-333">`Per class Log-loss`.</span></span> <span data-ttu-id="95a7b-334">Budete chtít na třídu protokolu ztrátu byly co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="95a7b-334">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="95a7b-335">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="95a7b-335">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

<span data-ttu-id="95a7b-336">`mlContext.Model.Save` uloží do souboru ZIP (ve složce "prostředky či výstupy"), které lze použít v ostatních aplikacích .NET k vytváření predikcí trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-336">`mlContext.Model.Save` saves your trained model to a .zip file (in the "assets/outputs" folder), which can be used in other .NET applications to make predictions.</span></span> <span data-ttu-id="95a7b-337">Přidejte následující kód, který `ReuseAndTuneInceptionModel()` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="95a7b-337">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#SaveModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="95a7b-338">Klasifikace obrázků s načíst model</span><span class="sxs-lookup"><span data-stu-id="95a7b-338">Classify images with a loaded model</span></span>

<span data-ttu-id="95a7b-339">Přidejte následující volání `ClassifyImages()` metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-339">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="95a7b-340">`ClassifyImages()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="95a7b-340">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="95a7b-341">Načte model.</span><span class="sxs-lookup"><span data-stu-id="95a7b-341">Loads the model.</span></span>
* <span data-ttu-id="95a7b-342">Operace čtení. Soubor TSV do `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-342">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="95a7b-343">Předpovídá klasifikace obrázků na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-343">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="95a7b-344">Vytvořit `ClassifyImages()` metoda, hned za `ReuseAndTuneInceptionModel()` metoda a těsně před `PairAndDisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-344">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation)
{

}
```

<span data-ttu-id="95a7b-345">Nejdřív načtěte model, který jste si předtím uložili následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="95a7b-345">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel)]

<span data-ttu-id="95a7b-346">Volání `ReadFromTsv()` metodu pro vytvoření `IEnumerable<ImageData>` třídu, která obsahuje plně kvalifikovanou cestu pro každý `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-346">Call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="95a7b-347">Je nutné tuto cesta k souboru spárovat se vaše data a předpovědi výsledky.</span><span class="sxs-lookup"><span data-stu-id="95a7b-347">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="95a7b-348">Je také potřeba převést `IEnumerable<ImageData>` třídu `IDataView` , kterou použijete k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="95a7b-348">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="95a7b-349">Přidejte následující kód jako následující dva řádky v `ClassifyImages()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-349">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[ReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTSV)]

<span data-ttu-id="95a7b-350">Kategorie testu image data s využitím předpovědět, jako jste to udělali dříve s trénovací data bitové kopie, [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="95a7b-350">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method.</span></span> <span data-ttu-id="95a7b-351">Přidejte následující kód, který `ClassifyImages()` metodu pro předpovědi a k převodu `predictions` `IDataView` do `IEnumerable` pro párování a zobrazení:</span><span class="sxs-lookup"><span data-stu-id="95a7b-351">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="95a7b-352">Spárujte a zobrazit testovací data bitové kopie a predikcí, přidejte následující kód k volání `PairAndDisplayResults()` metoda dříve vytvořeny jako další řádek v `ClassifyImages()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-352">To pair and display your test image data and predictions, add the following code to call the `PairAndDisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallPairAndDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="95a7b-353">Klasifikovat jedné image s načíst model</span><span class="sxs-lookup"><span data-stu-id="95a7b-353">Classify a single image with a loaded model</span></span>

<span data-ttu-id="95a7b-354">Přidejte následující volání `ClassifySingleImage()` metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-354">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="95a7b-355">`ClassifyImages()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="95a7b-355">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="95a7b-356">Načte model.</span><span class="sxs-lookup"><span data-stu-id="95a7b-356">Loads the model.</span></span>
* <span data-ttu-id="95a7b-357">Načtení `ImageData` instance.</span><span class="sxs-lookup"><span data-stu-id="95a7b-357">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="95a7b-358">Předpovídá klasifikace obrázků na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="95a7b-358">Predicts image classification based on test data.</span></span>

<span data-ttu-id="95a7b-359">Vytvořit `ClassifySingleImage()` metoda, hned za `ClassifyImages()` metoda a těsně před `PairAndDisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="95a7b-359">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation)
{

}
```

<span data-ttu-id="95a7b-360">Nejdřív načtěte model, který jste si předtím uložili následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="95a7b-360">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel2)]

<span data-ttu-id="95a7b-361">Vytvoření `ImageData` třídu, která obsahuje plně kvalifikovaný název souboru cestu a image pro jednoho `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="95a7b-361">Create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="95a7b-362">Přidejte následující kód jako následující řádky `ClassifySingleImage()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-362">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="95a7b-363">[PredictionEngine třídy](xref:Microsoft.ML.PredictionEngine%602) je pohodlné rozhraní API, které provádí predikcí na jednu instanci data.</span><span class="sxs-lookup"><span data-stu-id="95a7b-363">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="95a7b-364">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce vytváří predikcí na jeden sloupec data.</span><span class="sxs-lookup"><span data-stu-id="95a7b-364">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="95a7b-365">Předejte `imageData` k `PredictionEngine` předpovědět kategorie obrázku tak, že přidáte následující kód, který `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="95a7b-365">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="95a7b-366">Jako další řádek kódu v zobrazení výsledků předpovědí `ClassifySingleImage()` metody:</span><span class="sxs-lookup"><span data-stu-id="95a7b-366">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="95a7b-367">Výsledky</span><span class="sxs-lookup"><span data-stu-id="95a7b-367">Results</span></span>

<span data-ttu-id="95a7b-368">Po provedení předchozích kroků spuštění aplikace konzoly (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="95a7b-368">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="95a7b-369">Vaše výsledky by měly být podobně jako následující výstup.</span><span class="sxs-lookup"><span data-stu-id="95a7b-369">Your results should be similar to the following output.</span></span>  <span data-ttu-id="95a7b-370">Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="95a7b-370">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Save model to local file ===============
Model saved: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379
Press any key to continue . . .
```

<span data-ttu-id="95a7b-371">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="95a7b-371">Congratulations!</span></span> <span data-ttu-id="95a7b-372">Teď úspěšně sestavíte model strojového učení pro klasifikace obrázků opětovným použitím předem vytrénovaných `TensorFlow` model ML.NET.</span><span class="sxs-lookup"><span data-stu-id="95a7b-372">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="95a7b-373">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) úložiště.</span><span class="sxs-lookup"><span data-stu-id="95a7b-373">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="95a7b-374">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="95a7b-374">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="95a7b-375">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="95a7b-375">Understand the problem</span></span>
> * <span data-ttu-id="95a7b-376">Opakovaně používat a vyladit předem natrénovaných modelů</span><span class="sxs-lookup"><span data-stu-id="95a7b-376">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="95a7b-377">Klasifikace obrázků s načíst model</span><span class="sxs-lookup"><span data-stu-id="95a7b-377">Classify images with a loaded model</span></span>

<span data-ttu-id="95a7b-378">Projděte si úložišti GitHub s ukázkami Machine Learning a prozkoumejte ukázkový klasifikace rozšířené image.</span><span class="sxs-lookup"><span data-stu-id="95a7b-378">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="95a7b-379">úložiště GitHub DotNet/machinelearning – ukázky</span><span class="sxs-lookup"><span data-stu-id="95a7b-379">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)