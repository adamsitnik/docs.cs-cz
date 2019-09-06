---
title: Použití tříd Enumeration místo typů výčtů
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Mazat, jak lze použít třídy výčtu namísto výčtů jako způsob, jak vyřešit některá omezení.
ms.date: 10/08/2018
ms.openlocfilehash: ba687b700d7a6105baf71aa08a0d888afc9a8ec3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70296860"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="cede7-103">Použijte třídy výčtu místo typů Enum.</span><span class="sxs-lookup"><span data-stu-id="cede7-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="cede7-104">[Výčty](../../../csharp/language-reference/keywords/enum.md) (nebo *výčtové typy* pro Short) jsou obálka s dynamickým jazykem kolem integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="cede7-104">[Enumerations](../../../csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="cede7-105">Můžete chtít omezit jejich použití na, pokud ukládáte jednu hodnotu z uzavřené sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="cede7-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="cede7-106">Dobrým příkladem je klasifikace založená na velikostech (malá, střední, Velká).</span><span class="sxs-lookup"><span data-stu-id="cede7-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="cede7-107">Používání výčtů pro tok řízení nebo robustnější abstrakce může být [zápach kódu](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="cede7-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="cede7-108">Tento typ použití vede k křehkému kódu s mnoha příkazy toku řízení, které kontrolují hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="cede7-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="cede7-109">Místo toho můžete vytvořit třídy výčtu, které umožňují všechny bohatě orientované funkce pro objektově orientovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="cede7-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="cede7-110">Nejedná se však o důležité téma a v mnoha případech pro jednoduchost můžete i nadále používat běžné [typy výčtu](../../../csharp/language-reference/keywords/enum.md) , pokud je to vaše preference.</span><span class="sxs-lookup"><span data-stu-id="cede7-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/keywords/enum.md) if that's your preference.</span></span> <span data-ttu-id="cede7-111">Přesto se použití tříd výčtu podrobněji týká konceptů souvisejících s firmou.</span><span class="sxs-lookup"><span data-stu-id="cede7-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="cede7-112">Implementace základní třídy výčtu</span><span class="sxs-lookup"><span data-stu-id="cede7-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="cede7-113">Dořazení mikroslužeb v eShopOnContainers poskytuje ukázkovou implementaci základní třídy výčtu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cede7-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) 
    {
        Id = id; 
        Name = name; 
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | 
                                         BindingFlags.Static | 
                                         BindingFlags.DeclaredOnly); 

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj) 
    {
        var otherValue = obj as Enumeration; 

        if (otherValue == null) 
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id); 

    // Other utility methods ... 
}
```

<span data-ttu-id="cede7-114">Tuto třídu můžete použít jako typ v jakémkoli objektu entity nebo hodnoty, jako u následující `CardType` třídy: `Enumeration`</span><span class="sxs-lookup"><span data-stu-id="cede7-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="cede7-115">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="cede7-115">Additional resources</span></span>

- <span data-ttu-id="cede7-116">**Výčet je Evil – Update** </span><span class="sxs-lookup"><span data-stu-id="cede7-116">**Enum’s are evil—update** </span></span>\
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="cede7-117">**Daniel Jak výčty rozšíří chorobu – a jak ji vyřídit** </span><span class="sxs-lookup"><span data-stu-id="cede7-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** </span></span>\
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="cede7-118">**Jimmy Bogard. Třídy výčtu** </span><span class="sxs-lookup"><span data-stu-id="cede7-118">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="cede7-119">**Steve Smith. Alternativy výčtu vC#**  </span><span class="sxs-lookup"><span data-stu-id="cede7-119">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="cede7-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="cede7-120">**Enumeration.cs.**</span></span> <span data-ttu-id="cede7-121">Základní třída výčtu v eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="cede7-121">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="cede7-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="cede7-122">**CardType.cs**.</span></span> <span data-ttu-id="cede7-123">Ukázková třída výčtu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="cede7-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- <span data-ttu-id="cede7-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="cede7-124">**SmartEnum**.</span></span> <span data-ttu-id="cede7-125">Ardalis – třídy, které vám pomůžou vydávat silné typy inteligentnějších výčtů v .NET.</span><span class="sxs-lookup"><span data-stu-id="cede7-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="cede7-126">[Předchozí](implement-value-objects.md)Další
>[](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="cede7-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
