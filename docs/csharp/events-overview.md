---
title: Úvod do událostí
description: Další informace o události v rozhraní .NET Core a naše cíle návrhu jazyk pro události v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: e2944100d648d90e7aa5ea5798a351b8fd382cf7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051939"
---
# <a name="introduction-to-events"></a><span data-ttu-id="6b375-103">Úvod do událostí</span><span class="sxs-lookup"><span data-stu-id="6b375-103">Introduction to Events</span></span>

[<span data-ttu-id="6b375-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="6b375-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="6b375-105">Události jsou podobné delegátů, *pozdní vazby* mechanismus.</span><span class="sxs-lookup"><span data-stu-id="6b375-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="6b375-106">Události ve skutečnosti jsou postavené na podporu jazyka pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="6b375-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="6b375-107">Události jsou způsob, jakým objekt vysílání (pro všechny dotčené součásti v systému), že něco se stalo.</span><span class="sxs-lookup"><span data-stu-id="6b375-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="6b375-108">Jakékoli další součásti můžete přihlásit k odběru události a upozorněni, když je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="6b375-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="6b375-109">Pravděpodobně jste použili události v některé z vašich programování.</span><span class="sxs-lookup"><span data-stu-id="6b375-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="6b375-110">Řada grafických systémů mají model událostí na interakci uživatele sestavy.</span><span class="sxs-lookup"><span data-stu-id="6b375-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="6b375-111">Tyto události zasílat zprávy pohybu myši, stisknutí tlačítek a podobné interakce.</span><span class="sxs-lookup"><span data-stu-id="6b375-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="6b375-112">Který je jedním z nejčastěji používaných, ale určitě ne pouze scénář, kde události se používají.</span><span class="sxs-lookup"><span data-stu-id="6b375-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="6b375-113">Události, které by měla být zvýšena můžete definovat pro své třídy.</span><span class="sxs-lookup"><span data-stu-id="6b375-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="6b375-114">Jedním z důležitých faktorů při práci s událostmi je, že existuje, nemusí být libovolný objekt registrovaný při určité události.</span><span class="sxs-lookup"><span data-stu-id="6b375-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="6b375-115">Psaní kódu tak, aby nevyvolával události, kdy žádný naslouchací procesy jsou nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="6b375-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="6b375-116">Přihlášení k odběru události vytvoří také párování mezi dvěma objekty (zdroj události a jímky událostí).</span><span class="sxs-lookup"><span data-stu-id="6b375-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="6b375-117">Je potřeba zajistit, že ruší registraci stok události ze zdroje události, když už uvažujete o události.</span><span class="sxs-lookup"><span data-stu-id="6b375-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="6b375-118">Cíle návrhu pro podporu událostí</span><span class="sxs-lookup"><span data-stu-id="6b375-118">Design Goals for Event Support</span></span>

<span data-ttu-id="6b375-119">Návrh jazyka pro události, zaměřuje těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="6b375-119">The language design for events targets these goals.</span></span>

<span data-ttu-id="6b375-120">Nejprve povolte minimální párování mezi zdrojem události a jímku událostí.</span><span class="sxs-lookup"><span data-stu-id="6b375-120">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="6b375-121">Tyto dvě součásti nemusí napsané ve stejné organizaci a může aktualizovat i na úplně jiné plány.</span><span class="sxs-lookup"><span data-stu-id="6b375-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="6b375-122">Za druhé měla by být velmi jednoduché přihlásit odběr události a zrušit odběr této stejné události.</span><span class="sxs-lookup"><span data-stu-id="6b375-122">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="6b375-123">A nakonec zdroje událostí by měly podporovat několik předplatitelů události.</span><span class="sxs-lookup"><span data-stu-id="6b375-123">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="6b375-124">Taky by měly podporovat, s žádné odběratelů událostí, které jsou připojené.</span><span class="sxs-lookup"><span data-stu-id="6b375-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="6b375-125">Uvidíte, že cíle pro události jsou velmi podobné cíle pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="6b375-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="6b375-126">To je důvod, proč události jazykovou podporu je postavená na jazykové podpoře delegáta.</span><span class="sxs-lookup"><span data-stu-id="6b375-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="6b375-127">Podpora jazyků pro události</span><span class="sxs-lookup"><span data-stu-id="6b375-127">Language Support for Events</span></span>

<span data-ttu-id="6b375-128">Syntaxe pro definování události a přihlášení k odběru nebo odpovězeno události je rozšířením syntaxe pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="6b375-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="6b375-129">Chcete-li definovat událost použijete `event` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="6b375-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="6b375-130">Typ události (`EventHandler<FileListArgs>` v tomto příkladu) musí být typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="6b375-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="6b375-131">Existuje několik smluv, které byste měli postupovat při deklaraci události.</span><span class="sxs-lookup"><span data-stu-id="6b375-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="6b375-132">Typ delegáta události obvykle má návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="6b375-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="6b375-133">Deklarace událostí by měla být sloveso nebo v operaci frázi.</span><span class="sxs-lookup"><span data-stu-id="6b375-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="6b375-134">Pokud událost ohlásí něco, co se stalo, použijte minulý čas (jako v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="6b375-134">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="6b375-135">Použijte přítomný čas operací (například `Closing`) na něco, co se přiblíží sestavu.</span><span class="sxs-lookup"><span data-stu-id="6b375-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="6b375-136">Pomocí přítomném často, označuje, že vaše třída podporuje nějaký druh přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="6b375-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="6b375-137">Jedním z nejběžnějších scénářů je podporují zrušení.</span><span class="sxs-lookup"><span data-stu-id="6b375-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="6b375-138">Například `Closing` událostí může obsahovat argument, který by označoval, pokud by měla operaci zavření pokračovat, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6b375-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="6b375-139">V jiných scénářích může umožnit tak volajícím k úpravě chování pomocí aktualizace vlastností argumentů události.</span><span class="sxs-lookup"><span data-stu-id="6b375-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="6b375-140">Může vyvolat událost označující navrhované další akci, bude trvat algoritmus.</span><span class="sxs-lookup"><span data-stu-id="6b375-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="6b375-141">Obslužná rutina události může ukládat povinnost různé akce úpravou vlastností argumentu události.</span><span class="sxs-lookup"><span data-stu-id="6b375-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="6b375-142">Pokud chcete vyvolat událost, volání obslužných rutin událostí pomocí syntaxe volání delegáta:</span><span class="sxs-lookup"><span data-stu-id="6b375-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="6b375-143">Jak je popsáno v části na [delegáti](delegates-patterns.md),?.</span><span class="sxs-lookup"><span data-stu-id="6b375-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="6b375-144">operátor usnadňuje Ujistěte se, že nebude pokoušet o vyvolat událost, když nejsou žádná Odběratelé této události.</span><span class="sxs-lookup"><span data-stu-id="6b375-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="6b375-145">Se přihlásíte k odběru události pomocí `+=` operátor:</span><span class="sxs-lookup"><span data-stu-id="6b375-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="6b375-146">Metoda obslužné rutiny obvykle je předpona "Na" za nímž následuje název události, jak je znázorněno výše.</span><span class="sxs-lookup"><span data-stu-id="6b375-146">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="6b375-147">Zrušit pomocí `-=` operátor:</span><span class="sxs-lookup"><span data-stu-id="6b375-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="6b375-148">Je důležité si uvědomit, že mám deklarovat lokální proměnná pro výraz, který představuje obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="6b375-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="6b375-149">Zajistí se tak odebere unsubscribe obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6b375-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="6b375-150">Pokud jste použili hlavní část výrazu lambda, se pokoušíte odebrat obslužnou rutinu, která nikdy byla přiřazena, který nemá žádný účinek.</span><span class="sxs-lookup"><span data-stu-id="6b375-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="6b375-151">V následujícím článku budete Další informace o vzory typické událostí a různých změn v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b375-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="6b375-152">Next</span><span class="sxs-lookup"><span data-stu-id="6b375-152">Next</span></span>](event-pattern.md)
