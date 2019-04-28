---
title: Implementace doménového modelu mikroslužby pomocí .NET Core
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Získejte podrobnosti implementace orientované na DDD doménový model.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ec56a02e27f4218b3abc5839d1265815e188d2ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760985"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="5887c-103">Implementace doménového modelu mikroslužby pomocí .NET Core</span><span class="sxs-lookup"><span data-stu-id="5887c-103">Implement a microservice domain model with .NET Core</span></span>

<span data-ttu-id="5887c-104">V předchozí části byly vysvětlení principů návrhu základní a vzory pro navrhování modelu domény.</span><span class="sxs-lookup"><span data-stu-id="5887c-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="5887c-105">Teď můžete prozkoumat možnosti, jak implementovat doménový model s využitím .NET Core (plain C\# kódu) a EF Core.</span><span class="sxs-lookup"><span data-stu-id="5887c-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="5887c-106">Všimněte si, že doménový model se skládá pouze z kódu.</span><span class="sxs-lookup"><span data-stu-id="5887c-106">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="5887c-107">Jenom požadavky modelu EF Core, ale ne skutečné závislosti bude mít na EF.</span><span class="sxs-lookup"><span data-stu-id="5887c-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="5887c-108">Pevné závislosti nebo odkazy na EF Core nebo jiných ORM by neměl mít v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="5887c-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="5887c-109">Doménovou strukturu modelu ve vlastní knihovna .NET Standard</span><span class="sxs-lookup"><span data-stu-id="5887c-109">Domain model structure in a custom .NET Standard Library</span></span>

<span data-ttu-id="5887c-110">Složka organizaci použít aplikaci eShopOnContainers referenční aplikace ukazuje DDD modelů pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5887c-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="5887c-111">Můžete zjistit, že organizace jinou složku jasněji komunikuje návrhu volby provedené pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5887c-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="5887c-112">Jak je vidět v obrázek 7 – 10, v pořadí doménový model existují dvě agregace, agregace pořadí a agregace odběratele.</span><span class="sxs-lookup"><span data-stu-id="5887c-112">As you can see in Figure 7-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="5887c-113">Každou agregaci je skupina domény entity a objekty hodnotu, i když jste mohli agregace také skládá z jedné domény entity (agregační kořenové nebo Kořenová entita).</span><span class="sxs-lookup"><span data-stu-id="5887c-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![<span data-ttu-id="5887c-114">Zobrazení Průzkumníka řešení pro projekt Ordering.Domain zobrazující AggregatesModel složku, která obsahuje složky BuyerAggregate a OrderAggregate každé z nich obsahující jeho tříd entit, hodnota objektových souborů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5887c-114">The Solution Explorer view for the Ordering.Domain project, showing the AggregatesModel folder containing the BuyerAggregate and OrderAggregate folders, each one containing it's entity classes, value object files and so on.</span></span> ](./media/image11.png)

<span data-ttu-id="5887c-115">**Obrázek 7 – 10**.</span><span class="sxs-lookup"><span data-stu-id="5887c-115">**Figure 7-10**.</span></span> <span data-ttu-id="5887c-116">Doménovou strukturu modelu pro objednávání mikroslužeb v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="5887c-116">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="5887c-117">Kromě toho zahrnuje vrstvě doménového modelu smlouvy úložiště (rozhraní), které jsou požadavky na infrastrukturu modelu domény.</span><span class="sxs-lookup"><span data-stu-id="5887c-117">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="5887c-118">Jinými slovy tato rozhraní express, jaké úložiště a metod, které musí implementovat vrstvy infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="5887c-118">In other words, these interfaces express what repositories and the methods the infrastructure layer must implement.</span></span> <span data-ttu-id="5887c-119">Je velmi důležité, že implementace úložišť umístit mimo vrstvě doménového modelu, v knihovně infrastruktury vrstvu tak vrstvě doménového modelu není "napadeny" rozhraní API nebo třídy z infrastruktury technologie, jako jsou rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="5887c-119">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="5887c-120">Můžete také zobrazit [SeedWork](https://martinfowler.com/bliki/Seedwork.html) složku, která obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a hodnota objekty, takže není nutné redundantní kód ve třídě objektu každé domény.</span><span class="sxs-lookup"><span data-stu-id="5887c-120">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="5887c-121">Struktura agregace ve vlastní knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="5887c-121">Structure aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="5887c-122">Agregace odkazuje na clusteru objektů domény seskupené dohromady tak, aby odpovídaly transakční konzistence.</span><span class="sxs-lookup"><span data-stu-id="5887c-122">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="5887c-123">Tyto objekty může být instancí entit (z nichž jeden je agregační kořenový server WSUS nebo Kořenová entita) plus všechny objekty další hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5887c-123">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="5887c-124">Transakční konzistence znamená, že agregace je zaručeno, že byly konzistentní a aktuální na konci obchodní akce.</span><span class="sxs-lookup"><span data-stu-id="5887c-124">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="5887c-125">Například pořadí agregace v aplikaci eShopOnContainers řazení doménového modelu mikroslužby se skládá, jak je znázorněno v obrázek 7 – 11.</span><span class="sxs-lookup"><span data-stu-id="5887c-125">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 7-11.</span></span>

![Podrobné zobrazení OrderAggregate složky: Address.cs je hodnota objekt, IOrderRepository je rozhraní úložiště, Order.cs je agregační kořenové, OrderItem.cs je podřízené entity a OrderStatus.cs je třída výčtu.](./media/image12.png)

<span data-ttu-id="5887c-127">**Obrázek 7 – 11**.</span><span class="sxs-lookup"><span data-stu-id="5887c-127">**Figure 7-11**.</span></span> <span data-ttu-id="5887c-128">Pořadí agregace v řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5887c-128">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="5887c-129">Otevřete-li některý ze souborů ve složce aplikace agregace, zobrazí se jak je označen jako vlastní základní třídu nebo rozhraní, jako entity nebo hodnotu objektu, jak je implementován v [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) složky.</span><span class="sxs-lookup"><span data-stu-id="5887c-129">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implement-domain-entities-as-poco-classes"></a><span data-ttu-id="5887c-130">Implementace entity domény jako třídy POCO</span><span class="sxs-lookup"><span data-stu-id="5887c-130">Implement domain entities as POCO classes</span></span>

<span data-ttu-id="5887c-131">Doménový model se implementovat v rozhraní .NET tak, že vytvoříte POCO třídy, které implementují entity domény.</span><span class="sxs-lookup"><span data-stu-id="5887c-131">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="5887c-132">V následujícím příkladu je definována třída pořadí jako entity a také jako kořen agregace.</span><span class="sxs-lookup"><span data-stu-id="5887c-132">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="5887c-133">Protože pořadí třída je odvozena ze základní třídy Entity, můžete znovu použít společný kód související s entitami.</span><span class="sxs-lookup"><span data-stu-id="5887c-133">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="5887c-134">Berte v úvahu, že tyto základní třídy a rozhraní jsou definované uživatelem v projektu s modelem domény, tak, aby byl váš kód, ne infrastruktury kód z ORM jako je EF.</span><span class="sxs-lookup"><span data-stu-id="5887c-134">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName,
                            decimal unitPrice, decimal discount,
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);

        _orderItems.Add(orderItem);

    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="5887c-135">Je důležité si uvědomit, že se entita domény implementován jako třída POCO.</span><span class="sxs-lookup"><span data-stu-id="5887c-135">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="5887c-136">Nemá přímou závislost na Entity Framework Core nebo libovolné jiné architektury infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="5887c-136">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="5887c-137">Tato implementace je jako by měl být v DDD, stačí C\# kód implementace modelu domény.</span><span class="sxs-lookup"><span data-stu-id="5887c-137">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="5887c-138">Kromě toho je třída upravena pomocí rozhraní s názvem IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="5887c-138">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="5887c-139">Toto rozhraní je prázdné rozhraní, říká se jim *rozhraní značky*, která je slouží jenom k označení, že tato třída entity je také agregační kořenové.</span><span class="sxs-lookup"><span data-stu-id="5887c-139">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="5887c-140">Rozhraní značky někdy považovat odolnou proti vzor; je však také čistý způsob, jak označit třídu, zejména v případě, že toto rozhraní může být vyvíjejí.</span><span class="sxs-lookup"><span data-stu-id="5887c-140">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="5887c-141">Atribut může být volba pro značky, ale je rychlejší zobrazíte základní třídy (entita) vedle rozhraní IAggregate namísto vložení hodnoty značku agregační atribut nad třídu.</span><span class="sxs-lookup"><span data-stu-id="5887c-141">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="5887c-142">Je na vás předvolby, v každém případě.</span><span class="sxs-lookup"><span data-stu-id="5887c-142">It is a matter of preferences, in any case.</span></span>

<span data-ttu-id="5887c-143">Máte agregační kořenové znamená, že většinu kódu související s konzistence a obchodních pravidel agregaci entit by měla být implementována jako metody ve třídě kořenové agregační pořadí (například AddOrderItem při přidávání objektu OrderItem agregaci) .</span><span class="sxs-lookup"><span data-stu-id="5887c-143">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="5887c-144">By neměl vytvořit nebo aktualizovat objekty OrderItems, nezávisle na sobě nebo přímo. Třída AggregateRoot uchovává ovládacího prvku a konzistence, všechny operace aktualizace s jeho podřízených entit.</span><span class="sxs-lookup"><span data-stu-id="5887c-144">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulate-data-in-the-domain-entities"></a><span data-ttu-id="5887c-145">Zapouzdření dat v entitách domény</span><span class="sxs-lookup"><span data-stu-id="5887c-145">Encapsulate data in the Domain Entities</span></span>

<span data-ttu-id="5887c-146">Běžný problém v modelech entity je, aby zveřejňovaly navigační vlastnosti kolekce jako seznam veřejně přístupné typy.</span><span class="sxs-lookup"><span data-stu-id="5887c-146">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="5887c-147">To umožňuje vývojáři ocení spolupracovníka manipulovat s obsahem těchto kolekci typů, které mohou obejít důležitá obchodní pravidla pro kolekci, možná byste museli opustit objektu v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="5887c-147">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="5887c-148">Řešení, aby to je a vystavovat přístup jen pro čtení k souvisejících kolekcích explicitně poskytující metody, které definují způsoby, ve které klienty můžete s nimi manipulovat.</span><span class="sxs-lookup"><span data-stu-id="5887c-148">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="5887c-149">V předchozím kódu mějte na paměti, že mnoho atributů jsou jen pro čtení nebo privátní a jsou pouze aktualizovatelné metody třídy, takže výstupních obchodní domény podmínek a logiku určenou v rámci metod tříd bere v úvahu žádné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5887c-149">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update considers business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="5887c-150">Například následující vzorů DDD **byste měli *není* takto** z libovolné příkaz rutinu metody nebo aplikace vrstvy třídy (ve skutečnosti, musí být pro vás k tomu):</span><span class="sxs-lookup"><span data-stu-id="5887c-150">For example, following DDD patterns, **you should *not* do the following** from any command handler method or application layer class (actually, it should be impossible for you to do so):</span></span>

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems collection directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

<span data-ttu-id="5887c-151">Metoda Add v tomto případě je čistě operace přidání dat s přímým přístupem do kolekce OrderItems.</span><span class="sxs-lookup"><span data-stu-id="5887c-151">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="5887c-152">Proto se většina logiku domény, pravidla nebo ověření související se, že operace s podřízených entit bude možné rozdělit do aplikační vrstvy (obslužné rutiny příkazů a kontrolerů rozhraní Web API).</span><span class="sxs-lookup"><span data-stu-id="5887c-152">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="5887c-153">Budete-li kolem agregační kořenové, agregační kořenové nemůže zaručit jeho výstupních podmínek, jeho platnost nebo jeho konzistence.</span><span class="sxs-lookup"><span data-stu-id="5887c-153">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="5887c-154">Nakonec je třeba špagety kód nebo kód transakční skriptu.</span><span class="sxs-lookup"><span data-stu-id="5887c-154">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="5887c-155">Pokud chcete postupovat podle vzorů DDD, nesmí mít entity veřejné metody setter v jakékoli vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="5887c-155">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="5887c-156">Změny v entitě by měl vycházet explicitní metody explicitní všudypřítomná jazyk o změny, které provádějí v dané entitě.</span><span class="sxs-lookup"><span data-stu-id="5887c-156">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="5887c-157">Kromě toho kolekce v rámci entity (například položky objednávky) by měl být vlastnosti jen pro čtení (metoda AsReadOnly vysvětleno dále).</span><span class="sxs-lookup"><span data-stu-id="5887c-157">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="5887c-158">Je třeba aktualizovat pouze z v rámci metody agregační kořenové třídy nebo metody podřízené entity.</span><span class="sxs-lookup"><span data-stu-id="5887c-158">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="5887c-159">Jak je vidět v kódu pro kořenový agregační pořadí, všechny metody setter by měla být privátní nebo alespoň oprávnění jen pro čtení externě, tak, aby žádné operace proti entity dat nebo její podřízené entity se provádí prostřednictvím metody ve třídě entity.</span><span class="sxs-lookup"><span data-stu-id="5887c-159">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="5887c-160">To udržuje konzistenci způsobem řízeným a objektově orientované namísto implementace kódu transakční skriptu.</span><span class="sxs-lookup"><span data-stu-id="5887c-160">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="5887c-161">Následující fragment kódu ukazuje správný způsob, jak kód úkolu přidávání objekt OrderItem agregaci pořadí.</span><span class="sxs-lookup"><span data-stu-id="5887c-161">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="5887c-162">V tomto fragmentu kódu, bude většinu ověření nebo logiky týkající se vytvoření objektu OrderItem pod kontrolou agregační kořenové pořadí – v metodě AddOrderItem – zejména ověření a logiku související s další prvky v agregaci.</span><span class="sxs-lookup"><span data-stu-id="5887c-162">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="5887c-163">Například se mohou zobrazovat jako výsledek z více volání AddOrderItem jedné položce produktu.</span><span class="sxs-lookup"><span data-stu-id="5887c-163">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="5887c-164">V této metodě můžete zkontrolovat položky produktu a konsolidovat do jediného objektu OrderItem s více jednotkami stejné položky produktu.</span><span class="sxs-lookup"><span data-stu-id="5887c-164">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="5887c-165">Kromě toho pokud existují jiné slevy objemy, ale ID produktu je stejný, by pravděpodobně použijete vyšší slevy.</span><span class="sxs-lookup"><span data-stu-id="5887c-165">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="5887c-166">Tento princip platí pro další logiku domény OrderItem objektu.</span><span class="sxs-lookup"><span data-stu-id="5887c-166">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="5887c-167">Kromě toho novou operaci OrderItem(params) také být řízený a provádí metoda AddOrderItem z kořene agregační pořadí.</span><span class="sxs-lookup"><span data-stu-id="5887c-167">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="5887c-168">Proto většinu logiku nebo ověření související se, že operace (zejména cokoli, co má vliv na konzistenci mezi ostatní podřízené entity) bude na jednom místě v kořenu agregace.</span><span class="sxs-lookup"><span data-stu-id="5887c-168">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="5887c-169">To je účel ultimate agregační kořenové vzoru.</span><span class="sxs-lookup"><span data-stu-id="5887c-169">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="5887c-170">Pokud používáte Entity Framework Core 1.1 nebo později, DDD entity můžete lépe vyjádřit protože umožňuje [mapování na pole](https://docs.microsoft.com/ef/core/modeling/backing-field) kromě vlastností.</span><span class="sxs-lookup"><span data-stu-id="5887c-170">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="5887c-171">To je užitečné, když chráníte kolekce podřízených entit nebo hodnota objekty.</span><span class="sxs-lookup"><span data-stu-id="5887c-171">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="5887c-172">Toto vylepšení místo vlastnosti můžete použít jednoduchý privátní pole a můžete implementovat jakýmkoli aktualizacím kolekce pole ve veřejné metody a prostřednictvím metody AsReadOnly poskytují přístup jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="5887c-172">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="5887c-173">V DDD, které chcete aktualizovat entitu pouze prostřednictvím metod v entity (nebo konstruktoru), aby bylo možné řídit všechny invariantní a konzistenci dat takže vlastnosti jsou definovány pouze s přistupující objekt get.</span><span class="sxs-lookup"><span data-stu-id="5887c-173">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="5887c-174">Vlastnosti se zálohují na soukromé pole.</span><span class="sxs-lookup"><span data-stu-id="5887c-174">The properties are backed by private fields.</span></span> <span data-ttu-id="5887c-175">Soukromé členy lze přistupovat pouze z v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="5887c-175">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="5887c-176">Nicméně tady jedna výjimka: EF Core je potřeba nastavit také tato pole (takže se může vrátit objekt nahraďte odpovídajícími hodnotami).</span><span class="sxs-lookup"><span data-stu-id="5887c-176">However, there one exception: EF Core needs to set these fields as well (so it can return the object with the proper values).</span></span>

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="5887c-177">Vlastnosti mapy s pouze získat přístupové objekty do polí v tabulce databáze</span><span class="sxs-lookup"><span data-stu-id="5887c-177">Map properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="5887c-178">Mapování vlastnosti na sloupce tabulky databáze není odpovědnost domény, ale součástí infrastruktury a stálost vrstvu.</span><span class="sxs-lookup"><span data-stu-id="5887c-178">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="5887c-179">Jsme zmínili, tento tady jenom, abyste měli přehled o novinkách v EF Core 1.1 nebo novější týkajících se jak lze modelovat entity.</span><span class="sxs-lookup"><span data-stu-id="5887c-179">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="5887c-180">Další podrobnosti o tomto tématu jsou vysvětlené v oblasti infrastruktury a trvalost.</span><span class="sxs-lookup"><span data-stu-id="5887c-180">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="5887c-181">Když pomocí EF Core 1.0 nebo novější, potřebujete v rámci uvolněn objekt DbContext mapy – vlastnosti, které jsou definovány pouze pomocí metody getter skutečné polí v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="5887c-181">When you use EF Core 1.0 or later, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="5887c-182">To se provádí pomocí metody HasField PropertyBuilder třídy.</span><span class="sxs-lookup"><span data-stu-id="5887c-182">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="map-fields-without-properties"></a><span data-ttu-id="5887c-183">Mapování polí bez vlastností</span><span class="sxs-lookup"><span data-stu-id="5887c-183">Map fields without properties</span></span>

<span data-ttu-id="5887c-184">S funkcí v EF Core 1.1 nebo vyšší sloupce mapovat na pole je také možné používat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5887c-184">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="5887c-185">Místo toho můžete namapovat pouze sloupce z tabulky na pole.</span><span class="sxs-lookup"><span data-stu-id="5887c-185">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="5887c-186">Je běžným případem použití pro tento privátní pole pro vnitřní stav, který není potřeba přistupovat z mimo entitu.</span><span class="sxs-lookup"><span data-stu-id="5887c-186">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="5887c-187">Například v předchozím příkladu kódu OrderAggregate existují několik privátní pole, jako je třeba `_paymentMethodId` pole, které mají žádné související vlastnost setter nebo getter.</span><span class="sxs-lookup"><span data-stu-id="5887c-187">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="5887c-188">Toto pole také může vypočítá v rámci obchodní logiku pořadí a použití z metody pořadí, ale je potřeba nastavit jako trvalý, v databázi i.</span><span class="sxs-lookup"><span data-stu-id="5887c-188">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="5887c-189">Takže v EF Core (od verze 1.1) je způsob, jak mapovat pole bez související vlastnost sloupec v databázi.</span><span class="sxs-lookup"><span data-stu-id="5887c-189">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="5887c-190">To je také jsou vysvětlené v [vrstvy infrastruktury](ddd-oriented-microservice.md#the-infrastructure-layer) části této příručky.</span><span class="sxs-lookup"><span data-stu-id="5887c-190">This is also explained in the [Infrastructure layer](ddd-oriented-microservice.md#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5887c-191">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5887c-191">Additional resources</span></span>

- <span data-ttu-id="5887c-192">**Vaughn Vernon. Modelování agregace s DDD a Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="5887c-192">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="5887c-193">Všimněte si, že toto je *není* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="5887c-193">Note that this is *not* Entity Framework Core.</span></span> \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- <span data-ttu-id="5887c-194">**Julie Lerman. Datové body – kódování pro návrhy řízené doménou: Tipy pro vývojáře, zaměřuje dat** \\</span><span class="sxs-lookup"><span data-stu-id="5887c-194">**Julie Lerman. Data Points - Coding for Domain-Driven Design: Tips for Data-Focused Devs** \\</span></span>
  <https://msdn.microsoft.com/magazine/dn342868.aspx>

- <span data-ttu-id="5887c-195">**Udi Dahan. Vytvoření plně zapouzdřené doménových modelů** \\</span><span class="sxs-lookup"><span data-stu-id="5887c-195">**Udi Dahan. How to create fully encapsulated Domain Models** \\</span></span>
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> <span data-ttu-id="5887c-196">[Předchozí](microservice-domain-model.md)
> [další](seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="5887c-196">[Previous](microservice-domain-model.md)
[Next](seedwork-domain-model-base-classes-interfaces.md)</span></span>
