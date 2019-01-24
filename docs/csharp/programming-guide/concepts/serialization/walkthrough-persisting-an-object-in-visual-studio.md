---
title: 'Průvodce: Uchování objektu pomocíC#'
ms.date: 04/26/2018
ms.openlocfilehash: 61e7496b39bcbc42b0ebb2642fcb1ad1d32696af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512447"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="0eda9-102">Návod: uchování objektu pomocí jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0eda9-102">Walkthrough: persisting an object using C#</span></span> #

<span data-ttu-id="0eda9-103">Serializace můžete použít k uchování dat objektu mezi instancemi, které vám umožní uložení hodnot a načíst je další čas, který je vytvořena instance objektu.</span><span class="sxs-lookup"><span data-stu-id="0eda9-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="0eda9-104">V tomto návodu vytvoříte základní `Loan` objektu a zachovat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="0eda9-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="0eda9-105">Když znovu vytvoříte objekt se budou ze souboru načítat data.</span><span class="sxs-lookup"><span data-stu-id="0eda9-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0eda9-106">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="0eda9-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="0eda9-107">Pokud aplikace musí vytvořit soubor, musí mít tuto aplikaci `Create` oprávnění pro složku.</span><span class="sxs-lookup"><span data-stu-id="0eda9-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="0eda9-108">Oprávnění jsou nastavená pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="0eda9-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="0eda9-109">Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="0eda9-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="0eda9-110">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` oprávnění do jednoho souboru (místo vytvořit oprávnění pro složku).</span><span class="sxs-lookup"><span data-stu-id="0eda9-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="0eda9-111">Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo ve složce Program Files.</span><span class="sxs-lookup"><span data-stu-id="0eda9-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0eda9-112">V tomto příkladu ukládá data v binárním formátu souboru.</span><span class="sxs-lookup"><span data-stu-id="0eda9-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="0eda9-113">Tyto formáty by neměla používat pro citlivá data, jako jsou hesla nebo informace o platební kartě.</span><span class="sxs-lookup"><span data-stu-id="0eda9-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0eda9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0eda9-114">Prerequisites</span></span>

* <span data-ttu-id="0eda9-115">Sestavte a spusťte, nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="0eda9-115">To build and run, install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="0eda9-116">Pokud jste tak dosud neučinili, nainstalujte váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="0eda9-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="0eda9-117">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="0eda9-117">Need to install a code editor?</span></span> <span data-ttu-id="0eda9-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="0eda9-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

* <span data-ttu-id="0eda9-119">V příkladu vyžaduje C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="0eda9-119">The example requires C# 7.3.</span></span> <span data-ttu-id="0eda9-120">Zobrazit [vyberte verzi jazyka C#](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="0eda9-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span> 

<span data-ttu-id="0eda9-121">Můžete prozkoumat ukázkový kód online [v úložišti GitHub s ukázkami .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="0eda9-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="0eda9-122">Vytvoření objektu půjčky</span><span class="sxs-lookup"><span data-stu-id="0eda9-122">Creating the loan object</span></span>

<span data-ttu-id="0eda9-123">Prvním krokem je vytvoření `Loan` třídy a Konzolová aplikace, která používá třídu:</span><span class="sxs-lookup"><span data-stu-id="0eda9-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="0eda9-124">Vytvořte novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0eda9-124">Create a new application.</span></span> <span data-ttu-id="0eda9-125">Typ `dotnet new console -o serialization` vytvořte novou konzolovou aplikaci v podadresáři s názvem `serialization`.</span><span class="sxs-lookup"><span data-stu-id="0eda9-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="0eda9-126">Otevřete aplikaci ve svém editoru a přidejte novou třídu s názvem `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="0eda9-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="0eda9-127">Přidejte následující kód, který vaše `Loan` třídy:</span><span class="sxs-lookup"><span data-stu-id="0eda9-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="0eda9-128">Budete také muset vytvořit aplikaci, která se používá `Loan` třídy.</span><span class="sxs-lookup"><span data-stu-id="0eda9-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="0eda9-129">Serializace objektu půjčky</span><span class="sxs-lookup"><span data-stu-id="0eda9-129">Serialize the loan object</span></span>

1. <span data-ttu-id="0eda9-130">Otevřít `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="0eda9-130">Open `Program.cs`.</span></span> <span data-ttu-id="0eda9-131">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0eda9-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="0eda9-132">Přidat obslužnou rutinu události pro `PropertyChanged` událost a několik řádků změnit `Loan` objektu a zobrazte změny.</span><span class="sxs-lookup"><span data-stu-id="0eda9-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="0eda9-133">Můžete zobrazit dodatky v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0eda9-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="0eda9-134">V tomto okamžiku můžete spuštění kódu a zobrazit aktuální výstup:</span><span class="sxs-lookup"><span data-stu-id="0eda9-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="0eda9-135">Spuštění této aplikace opakovaně vždy zapíše stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0eda9-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="0eda9-136">Pokaždé, když program spustíte, je vytvořen nový objekt půjčky.</span><span class="sxs-lookup"><span data-stu-id="0eda9-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="0eda9-137">V praxi úrokové sazby změnit pravidelně, ale ne nutně pokaždé, když je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="0eda9-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="0eda9-138">Serializační kód znamená, že zachovat nejnovější úrokové sazby mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="0eda9-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="0eda9-139">V dalším kroku se přesně to provést přidáním serializace do třídy půjčky.</span><span class="sxs-lookup"><span data-stu-id="0eda9-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="0eda9-140">Pomocí serializace k uchování objektu</span><span class="sxs-lookup"><span data-stu-id="0eda9-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="0eda9-141">Aby bylo možné zachovat hodnoty pro třídu půjček, musíte nejprve označte třídu `Serializable` atribut.</span><span class="sxs-lookup"><span data-stu-id="0eda9-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="0eda9-142">Přidejte následující kód, výše půjčky definice třídy:</span><span class="sxs-lookup"><span data-stu-id="0eda9-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="0eda9-143"><xref:System.SerializableAttribute> Sděluje kompilátoru, že všechno, co ve třídě, můžete nastavit jako trvalý, do souboru.</span><span class="sxs-lookup"><span data-stu-id="0eda9-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="0eda9-144">Vzhledem k tomu, `PropertyChanged` události nepředstavuje součástí graf objektu, který by měla být uložena, nesmí být serializován.</span><span class="sxs-lookup"><span data-stu-id="0eda9-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="0eda9-145">Mohlo by serializaci všechny objekty, které jsou připojené k této události.</span><span class="sxs-lookup"><span data-stu-id="0eda9-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="0eda9-146">Můžete přidat <xref:System.NonSerializedAttribute> deklarace pole pro `PropertyChanged` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0eda9-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="0eda9-147">Od verze C# 7.3, můžete připojit atributy na pomocné pole automaticky implementované vlastnosti pomocí `field` cílovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0eda9-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="0eda9-148">Následující kód přidává `TimeLastLoaded` vlastnost a označí je jako nelze serializovat:</span><span class="sxs-lookup"><span data-stu-id="0eda9-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="0eda9-149">Dalším krokem je přidání Serializační kód do aplikace LoanApp.</span><span class="sxs-lookup"><span data-stu-id="0eda9-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="0eda9-150">Aby bylo možné serializovat třídu a zápis do souboru, je použít <xref:System.IO> a <xref:System.Runtime.Serialization.Formatters.Binary> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="0eda9-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="0eda9-151">Abyste nemuseli zadávat plně kvalifikované názvy, můžete přidat odkazy na obory názvů nezbytné, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0eda9-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="0eda9-152">Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="0eda9-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="0eda9-153">Přidejte konstanty do třídy pro název souboru serializovaná data, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0eda9-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="0eda9-154">V dalším kroku přidejte následující kód po řádek, který vytvoří `TestLoan` objektu:</span><span class="sxs-lookup"><span data-stu-id="0eda9-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="0eda9-155">Nejdřív musíte zkontrolovat, zda soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="0eda9-155">You first must check that the file exists.</span></span> <span data-ttu-id="0eda9-156">Pokud existuje, vytvořit <xref:System.IO.Stream> třídy ke čtení binárního souboru a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídy pro převod souboru.</span><span class="sxs-lookup"><span data-stu-id="0eda9-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="0eda9-157">Také je potřeba převést z typu datový proud na typ objektu půjčky.</span><span class="sxs-lookup"><span data-stu-id="0eda9-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="0eda9-158">Dále je nutné přidat kód k serializaci třídy do souboru.</span><span class="sxs-lookup"><span data-stu-id="0eda9-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="0eda9-159">Přidejte následující kód za existující kód ve třídě `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="0eda9-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="0eda9-160">V tomto okamžiku můžete znovu sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0eda9-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="0eda9-161">Při prvním spuštění, Všimněte si, že začíná 7.5 úrokové sazby a poté změní na 7.1.</span><span class="sxs-lookup"><span data-stu-id="0eda9-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="0eda9-162">Ukončete aplikaci a znovu jej spusťte.</span><span class="sxs-lookup"><span data-stu-id="0eda9-162">Close the application and then run it again.</span></span> <span data-ttu-id="0eda9-163">Teď se aplikace zobrazí zprávu, aby četl uloženého souboru a úrokové sazby 7.1 ještě před kód, který změní.</span><span class="sxs-lookup"><span data-stu-id="0eda9-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="0eda9-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0eda9-164">See also</span></span>

- [<span data-ttu-id="0eda9-165">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="0eda9-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="0eda9-166">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0eda9-166">C# Programming Guide</span></span>](../..//index.md)
