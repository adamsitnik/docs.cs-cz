---
title: Implementace aplikační vrstvy mikroslužby pomocí webového rozhraní API
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pochopení injektáž závislostí, zprostředkovatel vzory a jejich podrobnosti implementace v aplikační vrstvu webového rozhraní API.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 376b4eca99ed60a54831aa37099108692d8bac6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761234"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="1df32-103">Implementace aplikační vrstvy mikroslužby pomocí webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1df32-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="1df32-104">Pomocí vkládání závislostí injektovat objekty infrastruktury na úrovni aplikační vrstvy</span><span class="sxs-lookup"><span data-stu-id="1df32-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="1df32-105">Jak už bylo zmíněno dříve, aplikační vrstvu je možné implementovat jako součást artefaktu (sestavení), kterou vytváříte, například v projektu webového rozhraní API nebo projektu webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="1df32-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="1df32-106">V případě mikroslužeb vytvořené pomocí ASP.NET Core aplikační vrstvu obvykle bude vaše knihovna webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1df32-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="1df32-107">Pokud chcete oddělit, co se chystá v ASP.NET Core (jeho infrastruktury a řadičích) z uživatelského kódu vrstvy vlastní aplikace, může také umístit úrovni aplikační vrstvy v samostatné knihovně tříd, ale to je volitelné.</span><span class="sxs-lookup"><span data-stu-id="1df32-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="1df32-108">Například kód vrstvy aplikace pořadí mikroslužeb přímo implementují jako součást **Ordering.API** project (projekt webového rozhraní API ASP.NET Core), jako je uvedené v obrázek 7 – 23.</span><span class="sxs-lookup"><span data-stu-id="1df32-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

![Zobrazení Průzkumníka řešení Ordering.API mikroslužeb, zobrazuje podsložky ve složce aplikace: Chování, příkazy, DomainEventHandlers, IntegrationEvents, modely, dotazy a ověření.](./media/image20.png)

<span data-ttu-id="1df32-110">**Obrázek 7 – 23**.</span><span class="sxs-lookup"><span data-stu-id="1df32-110">**Figure 7-23**.</span></span> <span data-ttu-id="1df32-111">Aplikační vrstvy v projektu Ordering.API ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1df32-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="1df32-112">ASP.NET Core zahrnuje jednoduchou [integrované kontejner IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentovaný identifikátorem rozhraní IServiceProvider), který podporuje vkládání konstruktoru ve výchozím nastavení a ASP.NET zpřístupní určité služby prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="1df32-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="1df32-113">ASP.NET Core používá termín *služby* pro všechny typy zaregistrujete, které budou vloženy prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="1df32-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="1df32-114">Konfigurace kontejneru integrovaných služeb v ConfigureServices metody ve třídě spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="1df32-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="1df32-115">Závislosti jsou implementované ve službách, které potřebuje typ a která se zaregistruje v kontejner IoC.</span><span class="sxs-lookup"><span data-stu-id="1df32-115">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="1df32-116">Obvykle je vhodné vložit závislosti, které implementují objekty infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="1df32-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="1df32-117">Velmi typické závislost vkládat je do úložiště.</span><span class="sxs-lookup"><span data-stu-id="1df32-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="1df32-118">Ale může injektovat další infrastrukturu závislosti, které máte uzavřeny.</span><span class="sxs-lookup"><span data-stu-id="1df32-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="1df32-119">Pro jednodušší implementace může injektovat přímo pracovní jednotky vzor objektu (objekt EF DbContext), protože je uvolněn objekt DBContext také implementace objektů trvalosti infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="1df32-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="1df32-120">V následujícím příkladu vidíte, jak je .NET Core vkládá objekty požadované úložiště pomocí konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1df32-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="1df32-121">Třída je obslužná rutina příkazu, což si probereme v další části.</span><span class="sxs-lookup"><span data-stu-id="1df32-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="1df32-122">Třída používá vložený úložiště k provedení transakcí a zachová tak změny stavu.</span><span class="sxs-lookup"><span data-stu-id="1df32-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="1df32-123">Nezáleží, jestli je obslužná rutina příkazu, metodu kontroleru webového rozhraní API ASP.NET Core, třídy nebo [DDD aplikační službu](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="1df32-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="1df32-124">Takže v konečném důsledku je jednoduchou třídu, která používá úložiště, domény entity a další aplikace koordinace způsobem, který je podobný obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="1df32-125">Stejně jako u všech uvedených tříd jako v příkladu pomocí DI podle konstruktoru funguje vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="1df32-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="1df32-126">Registrace závislosti implementace typy a rozhraní nebo odběrů</span><span class="sxs-lookup"><span data-stu-id="1df32-126">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="1df32-127">Než použijete objekty vloženými prostřednictvím konstruktory, musíte vědět, kde k registraci rozhraní a třídy, které vytvářejí objekty vloženy do vaší třídy aplikace prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="1df32-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="1df32-128">(Například DI na základě konstruktoru, jak bylo uvedeno výše.)</span><span class="sxs-lookup"><span data-stu-id="1df32-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="1df32-129">Použít integrované kontejner IoC poskytované ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1df32-129">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="1df32-130">Když použijete integrovanou kontejner IoC poskytované ASP.NET Core, zaregistrujete typy, které chcete vložit v metodě ConfigureServices v souboru Startup.cs, stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1df32-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="1df32-131">Nejběžnější vzor registrace typů v kontejner IoC se zaregistrujte pár typy – rozhraní a jeho souvisejících implementace třídy.</span><span class="sxs-lookup"><span data-stu-id="1df32-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="1df32-132">Pokud požádáte o objektu z kontejner IoC prostřednictvím jakéhokoli konstruktoru, pak požadujete objekt typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1df32-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="1df32-133">Například v předchozím příkladu, poslední řádek uvádí, že když některé z vašich konstruktory jsou závislé na IMyCustomRepository (rozhraní nebo abstraktní), vloží kontejner IoC instance implementace MyCustomSQLServerRepository Třída.</span><span class="sxs-lookup"><span data-stu-id="1df32-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="1df32-134">Použití knihovny Scrutor pro typy automatické registrace</span><span class="sxs-lookup"><span data-stu-id="1df32-134">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="1df32-135">Při použití DI v .NET Core, můžete chtít zkontrolovat sestavení a jeho typy zařízení automaticky zaregistrovalo podle konvence.</span><span class="sxs-lookup"><span data-stu-id="1df32-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="1df32-136">Tato funkce není aktuálně k dispozici v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1df32-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="1df32-137">Můžete však použít [Scrutor](https://github.com/khellang/Scrutor) knihovny, který.</span><span class="sxs-lookup"><span data-stu-id="1df32-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="1df32-138">Tento přístup je vhodné, když máte desítky typy, které musí být zaregistrovaní v kontejnerech IoC.</span><span class="sxs-lookup"><span data-stu-id="1df32-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1df32-139">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1df32-139">Additional resources</span></span>

- <span data-ttu-id="1df32-140">**Matthew King. Registrace služby Scrutor** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-140">**Matthew King. Registering services with Scrutor** \\</span></span>
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="1df32-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="1df32-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="1df32-142">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="1df32-142">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="1df32-143">Použít Autofac jako kontejner IoC</span><span class="sxs-lookup"><span data-stu-id="1df32-143">Use Autofac as an IoC container</span></span>

<span data-ttu-id="1df32-144">Můžete také používat další technologie IoC kontejnery a zapojte do kanálu ASP.NET Core, stejně jako v pořadí mikroslužeb v aplikaci eShopOnContainers, který používá [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="1df32-144">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="1df32-145">Při použití Autofac zaregistrujete obvykle typy prostřednictvím modulů, které umožňují rozdělit typy registrace mezi více souborů v závislosti na tom, kde vaše typy jsou, stejně jako jste mohli distribuovat napříč více knihoven tříd typů aplikací.</span><span class="sxs-lookup"><span data-stu-id="1df32-145">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="1df32-146">Například tady je [modul aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro [Ordering.API webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projekt s typy, které se chcete vložit.</span><span class="sxs-lookup"><span data-stu-id="1df32-146">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="1df32-147">Autofac má také funkce, která [kontrolovat sestavení a zaregistrujte typy podle konvence název](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="1df32-147">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="1df32-148">Proces registrace a Koncepty jsou velmi podobně jako typy můžete zaregistrovat pomocí integrované technologie ASP.NET Core IoC kontejneru, ale syntaxe při použití Autofac je trochu jiná.</span><span class="sxs-lookup"><span data-stu-id="1df32-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="1df32-149">V příkladu kódu je zaregistrovaný abstrakce IOrderRepository spolu s implementací třídy OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="1df32-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="1df32-150">To znamená, že deklarující konstruktor je závislost prostřednictvím abstrakce IOrderRepository nebo rozhraní, kontejner IoC vloží instanci třídy OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="1df32-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="1df32-151">Typ oboru instance určuje způsob sdílení instance mezi požadavky pro stejnou službu nebo závislost.</span><span class="sxs-lookup"><span data-stu-id="1df32-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="1df32-152">Po odeslání žádosti pro závislost na kontejner IoC může vrátit následující:</span><span class="sxs-lookup"><span data-stu-id="1df32-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="1df32-153">Jedna instance pro každý obor životnost (podle kontejner ASP.NET Core IoC jako *obor*).</span><span class="sxs-lookup"><span data-stu-id="1df32-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="1df32-154">Nové instance za závislosti (podle kontejner ASP.NET Core IoC jako *přechodné*).</span><span class="sxs-lookup"><span data-stu-id="1df32-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="1df32-155">Jedna instance sdílené ve všech objektech pomocí kontejner IoC (podle kontejner ASP.NET Core IoC jako *singleton*).</span><span class="sxs-lookup"><span data-stu-id="1df32-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1df32-156">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1df32-156">Additional resources</span></span>

- <span data-ttu-id="1df32-157">**Úvod do injektáž závislostí v ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-157">**Introduction to Dependency Injection in ASP.NET Core** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="1df32-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="1df32-158">**Autofac.**</span></span> <span data-ttu-id="1df32-159">Oficiální dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="1df32-159">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="1df32-160">**Porovnání životnosti služby kontejner ASP.NET Core IoC s obory instance kontejner Autofac IoC - Cesarovi de la Torre.**</span><span class="sxs-lookup"><span data-stu-id="1df32-160">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="1df32-161">Implementace vzorů příkazu a obslužná rutina příkazu</span><span class="sxs-lookup"><span data-stu-id="1df32-161">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="1df32-162">V příkladu DI prostřednictvím konstruktoru je znázorněno v předchozí části se kontejner IoC vkládá úložišť pomocí konstruktoru ve třídě.</span><span class="sxs-lookup"><span data-stu-id="1df32-162">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="1df32-163">Ale přesně ve kterém byly jejich vloží?</span><span class="sxs-lookup"><span data-stu-id="1df32-163">But exactly where were they injected?</span></span> <span data-ttu-id="1df32-164">V jednoduché webové rozhraní API (například mikroslužeb katalogu v aplikaci eShopOnContainers) můžete do něj vložit na úrovni řadiče MVC, v konstruktoru řadič, v rámci kanálu požadavku ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1df32-164">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="1df32-165">Nicméně v počáteční kód v této části ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) třídy ze služby Ordering.API v aplikaci eShopOnContainers), injektáž závislostí se provádí prostřednictvím konstruktoru ke konkrétnímu příkazu. Obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="1df32-165">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="1df32-166">Dejte nám vysvětlují, jaké obslužná rutina příkazu je a proč by měli používat.</span><span class="sxs-lookup"><span data-stu-id="1df32-166">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="1df32-167">Příkaz vzor se týká vnitřně model CQRS, která byla zavedena dříve v tomto průvodci.</span><span class="sxs-lookup"><span data-stu-id="1df32-167">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="1df32-168">CQRS se dvěma stranami.</span><span class="sxs-lookup"><span data-stu-id="1df32-168">CQRS has two sides.</span></span> <span data-ttu-id="1df32-169">V první oblasti je dotazů pomocí zjednodušené dotazy s [Dapperem](https://github.com/StackExchange/dapper-dot-net) micro ORM, které bylo vysvětleno dříve.</span><span class="sxs-lookup"><span data-stu-id="1df32-169">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="1df32-170">Druhé oblasti se příkazy, které jsou výchozím bodem pro transakce a vstupním kanálem z mimo službu.</span><span class="sxs-lookup"><span data-stu-id="1df32-170">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="1df32-171">Jak je znázorněno v obrázek 7 – 24, vzorek je založen na přijímání příkazy ze strany klienta zpracování je na základě pravidel modelu domény a nakonec uchování států s transakcemi.</span><span class="sxs-lookup"><span data-stu-id="1df32-171">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Vyšší úroveň tohoto straně zápisy v modelu CQRS: Uživatelské rozhraní aplikace odešle příkaz prostřednictvím rozhraní API, která získá commandhandler –, který závisí na doménový model a infrastrukturu k aktualizaci databáze.](./media/image21.png)

<span data-ttu-id="1df32-173">**Obrázek 7 – 24**.</span><span class="sxs-lookup"><span data-stu-id="1df32-173">**Figure 7-24**.</span></span> <span data-ttu-id="1df32-174">Souhrnný přehled příkazů nebo "transakcí na straně" ve vzoru modelu CQRS</span><span class="sxs-lookup"><span data-stu-id="1df32-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="1df32-175">Třídy příkazů</span><span class="sxs-lookup"><span data-stu-id="1df32-175">The command class</span></span>

<span data-ttu-id="1df32-176">Příkaz je žádost o systému a provést akci, která změní stav systému.</span><span class="sxs-lookup"><span data-stu-id="1df32-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="1df32-177">Příkazy jsou nezbytnými předpoklady a mají být zpracována právě jednou.</span><span class="sxs-lookup"><span data-stu-id="1df32-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="1df32-178">Protože příkazy jsou požadavky, jsou obvykle pojmenován s operací imperativní náladu (například "vytvořit" nebo "" aktualizace) a jejich může taky obsahovat typ agregace, jako je například CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="1df32-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="1df32-179">Na rozdíl od události není příkaz faktů z minulosti; pouze žádost a proto může být odmítnut.</span><span class="sxs-lookup"><span data-stu-id="1df32-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="1df32-180">Příkazy můžou pocházet z uživatelského rozhraní v důsledku uživatele požadavek na zahájení nebo ze Správce procesu při procesu manager směruje agregace k provedení akce.</span><span class="sxs-lookup"><span data-stu-id="1df32-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="1df32-181">Důležitou vlastnost příkazu je, že ji by měl být zpracovány pouze jednou jednoho příjemce.</span><span class="sxs-lookup"><span data-stu-id="1df32-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="1df32-182">Je to proto, že příkaz je transakce, kterou chcete provést v aplikaci a jednu akci.</span><span class="sxs-lookup"><span data-stu-id="1df32-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="1df32-183">Příklad příkazu pro vytvoření stejné pořadí nemají být zpracovány více než jednou.</span><span class="sxs-lookup"><span data-stu-id="1df32-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="1df32-184">Toto je důležitý rozdíl mezi příkazy a události.</span><span class="sxs-lookup"><span data-stu-id="1df32-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="1df32-185">Události se dají zpracovávat více než jednou, protože velký počet systémů nebo mikroslužeb může zajímat události.</span><span class="sxs-lookup"><span data-stu-id="1df32-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="1df32-186">Kromě toho je důležité, že příkaz zpracovat pouze jednou v případě, že příkaz není idempotentní.</span><span class="sxs-lookup"><span data-stu-id="1df32-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="1df32-187">Příkaz je idempotentní, pokud jej lze spustit více než jednou beze změny výsledek, vzhledem k povaze příkazu nebo kvůli způsobu, jakým systém zpracovává příkaz.</span><span class="sxs-lookup"><span data-stu-id="1df32-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="1df32-188">Je dobrým zvykem, aby vaše příkazy a aktualizuje idempotentní, když má smysl v rámci vaší domény obchodní pravidla a výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="1df32-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="1df32-189">Například pokud chcete použít stejný příklad, pokud z nějakého důvodu (logiku opakování, hacking atd.) stejný příkaz CreateOrder dosáhne váš systém více než jednou, byste měli moct identifikovat a zajištění nevytvářejte více objednávek.</span><span class="sxs-lookup"><span data-stu-id="1df32-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="1df32-190">K tomu potřebujete připojit nějaký druh identity v konzoli operations a zjistit, jestli je příkaz nebo aktualizace již byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="1df32-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="1df32-191">Odeslat příkaz do jednoho příjemce; příkaz není publikována.</span><span class="sxs-lookup"><span data-stu-id="1df32-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="1df32-192">Publikování je pro události, které uvádějí faktu, něco se stalo a může být zajímavé pro přijímače událostí.</span><span class="sxs-lookup"><span data-stu-id="1df32-192">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="1df32-193">V případě události vydavatel nemá žádné obavy, o které příjemce získat události nebo co dělají to.</span><span class="sxs-lookup"><span data-stu-id="1df32-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="1df32-194">Ale domény nebo integrace událostí jsou různé scénáře už zavedené v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="1df32-194">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="1df32-195">Příkaz je implementováno třídou, která obsahuje datová pole nebo kolekce se všechny informace, které je potřeba za účelem provedení tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="1df32-196">Příkaz je zvláštní druh z Data přenosu objektu (DTO), který konkrétně slouží k vyžádání změn nebo transakce.</span><span class="sxs-lookup"><span data-stu-id="1df32-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="1df32-197">Podle přesně, který je nezbytný pro zpracování příkazu a žádné další informace o příkazu samého.</span><span class="sxs-lookup"><span data-stu-id="1df32-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="1df32-198">Následující příklad ukazuje zjednodušený CreateOrderCommand třídy.</span><span class="sxs-lookup"><span data-stu-id="1df32-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="1df32-199">Toto je neměnný příkaz, který se používá v pořadí mikroslužeb v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1df32-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="1df32-200">V podstatě třídu příkazu obsahuje veškerá data, které potřebujete pro provádění obchodní transakce s použitím objektů modelu domény.</span><span class="sxs-lookup"><span data-stu-id="1df32-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="1df32-201">Příkazy jsou proto jednoduše datové struktury, které obsahují data jen pro čtení a žádné chování.</span><span class="sxs-lookup"><span data-stu-id="1df32-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="1df32-202">Název příkazu označuje její účel.</span><span class="sxs-lookup"><span data-stu-id="1df32-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="1df32-203">V mnoha jazycích jako C#, příkazy jsou reprezentovány jako třídy, ale není true třídy ve smyslu reálné objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="1df32-203">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="1df32-204">Jako další vlastnost příkazy jsou neměnné, protože očekávané použití je, že jsou zpracovány přímo pomocí modelu domény.</span><span class="sxs-lookup"><span data-stu-id="1df32-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="1df32-205">Není potřeba změnit během jejich předpokládané životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="1df32-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="1df32-206">V C# třídy, neměnnosti můžete dosáhnout tím, že všechny metody setter nebo jiné metody, které se mění vnitřního stavu.</span><span class="sxs-lookup"><span data-stu-id="1df32-206">In a C# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="1df32-207">Mějte, že pokud určené pro instalaci nebo očekávat příkazy se obejde procesu serializace/deserializing, vlastnosti musí mít privátní metody setter a `[DataMember]` (nebo `[JsonProperty]`) atribut, jinak nebudou moci deserializátor rekonstrukce objektu v cílovém umístění s požadovanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="1df32-207">Bear in mind that if you intend or expect commands will be going through a serializing/deserializing process, the properties must have private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute, otherwise the deserializer will not be able to reconstruct the object at destination with the required values.</span></span>

<span data-ttu-id="1df32-208">Například třída příkaz pro vytvoření objednávky je pravděpodobně podobný z hlediska data pořadí, ve kterém chcete vytvořit, ale pravděpodobně není nutné stejné atributy.</span><span class="sxs-lookup"><span data-stu-id="1df32-208">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="1df32-209">Například CreateOrderCommand nemá ID objednávky, protože ještě nebyl vytvořen pořadí.</span><span class="sxs-lookup"><span data-stu-id="1df32-209">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="1df32-210">Mnoho příkaz třídy mohou být jednoduché, které vyžadují jenom několik polí o některé stavy, které je potřeba změnit.</span><span class="sxs-lookup"><span data-stu-id="1df32-210">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="1df32-211">Který by byl tento případ Pokud měníte pouze stav objednávky z "v procesu" k "placené" nebo "dodán" pomocí příkazu, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="1df32-211">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="1df32-212">Některé vývojář podá žádost objekty uživatelského rozhraní nezávisle na jejich DTO příkaz, ale to je jenom pár předvoleb.</span><span class="sxs-lookup"><span data-stu-id="1df32-212">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="1df32-213">Je únavné oddělení se nevěnuje přidanou hodnotu a objekty jsou téměř přesně stejný tvar.</span><span class="sxs-lookup"><span data-stu-id="1df32-213">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="1df32-214">V aplikaci eShopOnContainers, například některé příkazy pocházejí přímo ze strany klienta.</span><span class="sxs-lookup"><span data-stu-id="1df32-214">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="1df32-215">Třída obslužná rutina příkazu</span><span class="sxs-lookup"><span data-stu-id="1df32-215">The Command Handler class</span></span>

<span data-ttu-id="1df32-216">Měli byste implementovat třídu obslužné rutiny konkrétní příkaz pro každý příkaz.</span><span class="sxs-lookup"><span data-stu-id="1df32-216">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="1df32-217">To je, jak funguje vzor a je, kde budete používat objekt příkazu, doménových objektů a objektů úložiště infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="1df32-217">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="1df32-218">Obslužná rutina příkazu je ve skutečnosti srdce aplikační vrstvu z hlediska modelu CQRS a DDD.</span><span class="sxs-lookup"><span data-stu-id="1df32-218">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="1df32-219">Ale veškerou logiku domény by měly být obsaženy v rámci doménové třídy – v rámci agregace kořeny (kořenové entity), podřízené entity, nebo [služby domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale není v rozsahu obslužnou rutinu příkazu, což je třída z aplikace vrstva.</span><span class="sxs-lookup"><span data-stu-id="1df32-219">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="1df32-220">Třída obslužná rutina příkazu nabízí silné odrazový můstek tak, jak dosáhnout Princip jednoho odpovědnost (SRP) uvedené v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1df32-220">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="1df32-221">Obslužná rutina příkazu přijímá příkazu a získá výsledek z agregace, který se používá.</span><span class="sxs-lookup"><span data-stu-id="1df32-221">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="1df32-222">Výsledek by měl být úspěšné provedení příkazu nebo výjimku.</span><span class="sxs-lookup"><span data-stu-id="1df32-222">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="1df32-223">V případě výjimky by měl být stav systému beze změny.</span><span class="sxs-lookup"><span data-stu-id="1df32-223">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="1df32-224">Obslužná rutina příkazu přijímá obvykle následující kroky:</span><span class="sxs-lookup"><span data-stu-id="1df32-224">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="1df32-225">Přijímá objekt příkazu, jako je objekt DTO (z [zprostředkovatel](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiný objekt infrastruktury).</span><span class="sxs-lookup"><span data-stu-id="1df32-225">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="1df32-226">Ověří, že příkaz je neplatný (Pokud není ověřen zprostředkovatel).</span><span class="sxs-lookup"><span data-stu-id="1df32-226">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="1df32-227">Vytvoření instance agregačních kořenové instanci, která je cílem aktuální příkaz.</span><span class="sxs-lookup"><span data-stu-id="1df32-227">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="1df32-228">Metoda se provede na agregační kořenové instanci, získávání požadovaná data z tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-228">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="1df32-229">Přenese nový stav agregace do jeho související databáze.</span><span class="sxs-lookup"><span data-stu-id="1df32-229">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="1df32-230">Tento poslední operaci je aktuální transakci.</span><span class="sxs-lookup"><span data-stu-id="1df32-230">This last operation is the actual transaction.</span></span>

<span data-ttu-id="1df32-231">Obvykle obslužná rutina příkazu se zabývá jedné agregace využitím agregační kořenem (Kořenová entita).</span><span class="sxs-lookup"><span data-stu-id="1df32-231">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="1df32-232">Pokud více agregace by měly mít vliv příjem jediný příkaz, můžete použít domény události šíření stavy nebo akce napříč více agregací.</span><span class="sxs-lookup"><span data-stu-id="1df32-232">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="1df32-233">Důležitý bod je, že při zpracování příkazu veškerou logiku domény by měl být uvnitř doménový model (agregace), plně zapouzdřený a je připravený k testování částí.</span><span class="sxs-lookup"><span data-stu-id="1df32-233">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="1df32-234">Obslužná rutina příkazu funguje stejně jako způsob, jak získat doménový model z databáze a jako poslední krok, abyste řekněte vrstvě infrastruktury (úložiště) a zachová tak změny po změně modelu.</span><span class="sxs-lookup"><span data-stu-id="1df32-234">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="1df32-235">Výhodou tohoto přístupu je, že jste logiku domény v modelu domény izolované, plně zapouzdřený, bohatě vybaveným a chování Refaktorujte beze změn kódu v aplikaci nebo vrstev infrastruktury, které jsou na úrovni vložení (obslužné rutiny příkazů, webové rozhraní API, úložiště atd.).</span><span class="sxs-lookup"><span data-stu-id="1df32-235">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="1df32-236">Při získání složité a příliš mnoho logiku, která může být pach kód obslužné rutiny příkazů.</span><span class="sxs-lookup"><span data-stu-id="1df32-236">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="1df32-237">Seznamte se s nimi a pokud najdete logiku domény Refaktorujte kód pro přesun tohoto chování domény do metody doménových objektů (agregační kořenové a podřízené entity).</span><span class="sxs-lookup"><span data-stu-id="1df32-237">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="1df32-238">Jako příklad třídy obslužné rutiny příkazu následující kód ukazuje stejné CreateOrderCommandHandler třídy, které jste viděli na začátku této kapitole.</span><span class="sxs-lookup"><span data-stu-id="1df32-238">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="1df32-239">V tomto případě chceme metody zpracování a operace s objekty modelu domény/agregací.</span><span class="sxs-lookup"><span data-stu-id="1df32-239">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="1df32-240">Jedná se obslužná rutina příkazu by měl provést další kroky:</span><span class="sxs-lookup"><span data-stu-id="1df32-240">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="1df32-241">Pomocí příkazu dat můžete pracovat s agregační kořenové metody a chování.</span><span class="sxs-lookup"><span data-stu-id="1df32-241">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="1df32-242">Interně v rámci objektů domény vyvolat události domény provádí transakce, ale je transparentní z hlediska of obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-242">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="1df32-243">Pokud výsledek operace agregace je úspěšné a po dokončení transakce, vyvolat události integrace.</span><span class="sxs-lookup"><span data-stu-id="1df32-243">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="1df32-244">(Toto může být také navýšit tak, že infrastruktura třídy typu úložiště.)</span><span class="sxs-lookup"><span data-stu-id="1df32-244">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1df32-245">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1df32-245">Additional resources</span></span>

- <span data-ttu-id="1df32-246">**Označit Seemann. Za hranice jsou aplikace, ne objektově orientované** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-246">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** \\</span></span>
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="1df32-247">**Příkazy a události** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-247">**Commands and events** \\</span></span>
  <http://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="1df32-248">**Obslužná rutina příkazu k čemu slouží?**</span><span class="sxs-lookup"><span data-stu-id="1df32-248">**What does a command handler do?**</span></span> \
  <http://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="1df32-249">**Jimmy Bogard. Příkaz vzory domény – obslužné rutiny** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-249">**Jimmy Bogard. Domain Command Patterns – Handlers** \\</span></span>
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="1df32-250">**Jimmy Bogard. Příkaz vzory domény – ověření** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-250">**Jimmy Bogard. Domain Command Patterns – Validation** \\</span></span>
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="1df32-251">Proces kanálu příkazu: jak aktivovat obslužná rutina příkazu</span><span class="sxs-lookup"><span data-stu-id="1df32-251">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="1df32-252">Další otázkou je postup vyvolají obslužnou rutinu příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-252">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="1df32-253">Ručně ji lze volat z každého souvisejícími řadiče ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1df32-253">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="1df32-254">Ale, že přístup budou příliš s velkou provázaností a není ideální.</span><span class="sxs-lookup"><span data-stu-id="1df32-254">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="1df32-255">Další dvě hlavní možnosti, které jsou doporučené možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="1df32-255">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="1df32-256">Prostřednictvím vzoru artefakt zprostředkovatel v paměti.</span><span class="sxs-lookup"><span data-stu-id="1df32-256">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="1df32-257">S asynchronní fronty zpráv, mezi řadiče a obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1df32-257">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="1df32-258">Zprostředkovatel model (v paměti) se používá v příkazu kanálu</span><span class="sxs-lookup"><span data-stu-id="1df32-258">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="1df32-259">Jak je znázorněno v obrázek 7 – 25, v přístup modelu CQRS pomocí inteligentních zprostředkovatel, podobně jako na Service bus v paměti, který je dostatečně inteligentní, přesměrovat na obslužnou rutinu správné příkaz na základě typu příkazu nebo objekt DTO přijímají.</span><span class="sxs-lookup"><span data-stu-id="1df32-259">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="1df32-260">Jeden černé šipky mezi komponentami představují závislosti mezi objekty (v mnoha případech se vloží prostřednictvím DI) s jejich související interakce.</span><span class="sxs-lookup"><span data-stu-id="1df32-260">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Přiblížit na předchozím obrázku: kontroler ASP.NET Core odešle příkaz MediatR pro příkaz kanálu, aby dostanou do odpovídajícího popisovače.](./media/image22.png)

<span data-ttu-id="1df32-262">**Obrázek 7 – 25**.</span><span class="sxs-lookup"><span data-stu-id="1df32-262">**Figure 7-25**.</span></span> <span data-ttu-id="1df32-263">Použití vzoru zprostředkovatel v procesu v jedné mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="1df32-263">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="1df32-264">Důvod, proč pomocí vzoru zprostředkovatel dává smysl je, že v oddílu podnikové aplikace, zpracování požadavků dostat složité.</span><span class="sxs-lookup"><span data-stu-id="1df32-264">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="1df32-265">Chcete mít možnost přidávat otevřít počet vyskytující aspekty, jako je protokolování, ověření, auditování a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1df32-265">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="1df32-266">V těchto případech se můžete spolehnout na kanálu zprostředkovatel (naleznete v tématu [zprostředkovatel vzor](https://en.wikipedia.org/wiki/Mediator_pattern)) můžete poskytnout způsob pro tyto dodatečné chování nebo vyskytující aspekty.</span><span class="sxs-lookup"><span data-stu-id="1df32-266">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="1df32-267">Zprostředkovatel je objekt, který zapouzdřuje "jak" tohoto procesu: koordinuje spuštění na základě stavu, je vyvolána obslužná rutina příkazu způsob nebo datové části zadejte do obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1df32-267">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="1df32-268">Pomocí součásti zprostředkovatel můžete použít vyskytující aspekty centralizované a transparentním způsobem použitím dekoratéry (nebo [kanálu chování](https://github.com/jbogard/MediatR/wiki/Behaviors) protože [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="1df32-268">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="1df32-269">Další informace najdete v tématu [Dekoratér vzor](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="1df32-269">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="1df32-270">Dekorátory a chování jsou podobné [aspekt orientované programování (CHOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)pouze u konkrétní proces kanálu spravované komponentou zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="1df32-270">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="1df32-271">V CHOP aspekty, které implementují vyskytující aspekty se používají na základě *aspekt weavers* vložený v době kompilace nebo podle zachycení volání objektu.</span><span class="sxs-lookup"><span data-stu-id="1df32-271">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="1df32-272">Oba přístupy typické CHOP se někdy říká, že fungují "jako magic," protože se nejedná snadno zjistit, jak CHOP provede svou práci.</span><span class="sxs-lookup"><span data-stu-id="1df32-272">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="1df32-273">Při zpracování komplexnějších závažných problémech nebo oznámení chyb, může být obtížné ladit CHOP.</span><span class="sxs-lookup"><span data-stu-id="1df32-273">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="1df32-274">Tyto dekoratéry/chování na druhé straně jsou explicitní a použité pouze v kontextu zprostředkovatel, takže ladění je mnohem více předvídatelný a snadno.</span><span class="sxs-lookup"><span data-stu-id="1df32-274">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="1df32-275">Například v aplikaci eShopOnContainers, řazení mikroslužeb, implementovali jsme dvě ukázkové chování [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) třídy a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) třídy.</span><span class="sxs-lookup"><span data-stu-id="1df32-275">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="1df32-276">Implementace chování je vysvětlené v následující části zobrazující, jak aplikaci eShopOnContainers používá [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [chování](https://github.com/jbogard/MediatR/wiki/Behaviors).</span><span class="sxs-lookup"><span data-stu-id="1df32-276">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="1df32-277">Zpráva fronty (z mimoprocesovou) v kanálu příkazu</span><span class="sxs-lookup"><span data-stu-id="1df32-277">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="1df32-278">Další volbou je použití asynchronních zpráv na základě zprostředkovatele nebo fronty zpráv, jak je znázorněno v obrázek 7 – 26.</span><span class="sxs-lookup"><span data-stu-id="1df32-278">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="1df32-279">Tato možnost může být spojen s součásti zprostředkovatel bezprostředně před obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-279">That option could also be combined with the mediator component right before the command handler.</span></span>

![Kanál příkazu může být zpracována fronty zpráv vysoká dostupnost pro doručení příkazy do odpovídajícího popisovače.](./media/image23.png)

<span data-ttu-id="1df32-281">**Obrázek 7-26**.</span><span class="sxs-lookup"><span data-stu-id="1df32-281">**Figure 7-26**.</span></span> <span data-ttu-id="1df32-282">Pomocí příkazů modelu CQRS fronty zpráv (mimo procesu nebo komunikaci mezi procesy)</span><span class="sxs-lookup"><span data-stu-id="1df32-282">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="1df32-283">Pomocí zpráv fronty potvrďte, že můžete dále příkazy zkomplikovat váš příkaz kanálu, protože budete pravděpodobně muset rozdělit kanál na dva procesy připojené prostřednictvím fronty zpráv externí.</span><span class="sxs-lookup"><span data-stu-id="1df32-283">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="1df32-284">Pořád by měl použít potřebujete mít lepší škálovatelnost a výkon podle asynchronní zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1df32-284">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="1df32-285">Vezměte v úvahu, že v případě obrázek 7-26, kontroler právě odešle příkaz zprávy ve frontě a vrátí.</span><span class="sxs-lookup"><span data-stu-id="1df32-285">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="1df32-286">Potom obslužné rutiny příkazů zpracování zpráv svým vlastním tempem.</span><span class="sxs-lookup"><span data-stu-id="1df32-286">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="1df32-287">To znamená úžasných výhod fronty: Fronta zpráv může fungovat jako vyrovnávací paměť v případech, když hyper škálovatelnost je potřeba, například akcie nebo všechny další scénáře s vysokou objemu příchozích dat.</span><span class="sxs-lookup"><span data-stu-id="1df32-287">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="1df32-288">Ale vzhledem k asynchronní povaze fronty zpráv, musíte vymyslet, jak ke komunikaci s klientskou aplikací o úspěch nebo neúspěch zpracování příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-288">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="1df32-289">Zpravidla nikdy byste neměli používat příkazy "vypal a zapomeň".</span><span class="sxs-lookup"><span data-stu-id="1df32-289">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="1df32-290">Každé obchodní aplikace potřebuje vědět, pokud příkaz byl úspěšně zpracována, nebo aspoň ověří a přijmout.</span><span class="sxs-lookup"><span data-stu-id="1df32-290">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="1df32-291">Díky tomu se nebudou moct reagovat na klienta po ověření zprávou příkazu, která byla odeslána do fronty služby asynchronní zvyšuje složitost k vašemu systému, než příkaz v procesu proces, který vrátí výsledek operace po spuštění transakce.</span><span class="sxs-lookup"><span data-stu-id="1df32-291">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="1df32-292">Použití front, můžete potřebovat k vrácení výsledku procesu příkaz prostřednictvím jiné operace výsledek zprávy, které se bude vyžadovat další součásti a vlastní komunikační ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="1df32-292">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="1df32-293">Kromě toho jsou jednosměrná příkazy, které v mnoha případech nemusí být potřeba, jak je vysvětleno v následující zajímavé exchange mezi Burtsev Alexey a Grega Younga: v asynchronní příkazy [online konverzace](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="1df32-293">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="1df32-294">\[Burtsev Alexey\] můžu najít velké množství kódu, pokud uživatelé používají asynchronní zpracování příkazu nebo jedním ze způsobů zasílání zpráv bez z jakéhokoli důvodu k tomu příkaz (nejedná se některé dlouhá operace, nejsou provádění externí asynchronní kód, jsou i nepřecházejí aplikace předěl, který má být pomocí sběrnice zpráv).</span><span class="sxs-lookup"><span data-stu-id="1df32-294">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="1df32-295">Proč přinášejí tento zbytečné složitosti</span><span class="sxs-lookup"><span data-stu-id="1df32-295">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="1df32-296">A ve skutečnosti, můžu nezaznamenali příklad kódu modelu CQRS se blokování obslužné rutiny příkazů doposud, i když bude správně fungovat ve většině případů.</span><span class="sxs-lookup"><span data-stu-id="1df32-296">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="1df32-297">\[Grega Younga\] \[... \] asynchronní příkaz neexistuje, je ve skutečnosti jiné události.</span><span class="sxs-lookup"><span data-stu-id="1df32-297">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="1df32-298">Pokud musí přijmout, co můžete poslat mi a vyvolat událost v případě nesouhlasím, už nejsou vám sděluje mi něco \[tedy není příkaz\].</span><span class="sxs-lookup"><span data-stu-id="1df32-298">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="1df32-299">Jedná o vás uvádí něco udělat.</span><span class="sxs-lookup"><span data-stu-id="1df32-299">It's you telling me something has been done.</span></span> <span data-ttu-id="1df32-300">Vypadá to, že jako malého rozdílu v první, ale to má vliv na mnoho.</span><span class="sxs-lookup"><span data-stu-id="1df32-300">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="1df32-301">Asynchronní příkazy zvyšuje složitost systému, protože neexistuje jednoduchý způsob k označení selhání.</span><span class="sxs-lookup"><span data-stu-id="1df32-301">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="1df32-302">Proto asynchronní příkazy nedoporučují jiné než potřeby škálování požadavky nebo ve zvláštních případech při komunikaci interní mikroslužeb pomocí zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1df32-302">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="1df32-303">V těchto případech je třeba navrhnout samostatného systému generování sestav a obnovení pro chyby.</span><span class="sxs-lookup"><span data-stu-id="1df32-303">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="1df32-304">V počáteční verzi aplikaci eShopOnContainers jsme se rozhodli použít synchronní příkaz zpracování, spuštěné z požadavků HTTP a využitím vzor zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="1df32-304">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="1df32-305">Který snadno umožňuje vrátit úspěch nebo selhání procesu, jako [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementace.</span><span class="sxs-lookup"><span data-stu-id="1df32-305">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="1df32-306">V každém případě je třeba rozhodnutí podle firemních potřeb vaší aplikace nebo na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="1df32-306">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="1df32-307">Implementujte proces kanálu příkazu se vzorem, který zprostředkovatel (MediatR)</span><span class="sxs-lookup"><span data-stu-id="1df32-307">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="1df32-308">Jako ukázku implementace Tento průvodce navrhuje pomocí kanálu v procesu založena na vzoru zprostředkovatel ingestování příkaz jednotky a směrování příkazů v paměti, obslužné rutiny příkaz right.</span><span class="sxs-lookup"><span data-stu-id="1df32-308">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="1df32-309">V průvodci rovněž navrhuje použití [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) aby bylo možné oddělit vyskytující aspekty.</span><span class="sxs-lookup"><span data-stu-id="1df32-309">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="1df32-310">Pro implementaci v .NET Core jsou více knihoven open-source k dispozici, které implementují vzor zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="1df32-310">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="1df32-311">Knihovny používané v tomto průvodci se [MediatR](https://github.com/jbogard/MediatR) open source knihovny (vytvořené Jimmy Bogard), ale můžete použít jiný přístup.</span><span class="sxs-lookup"><span data-stu-id="1df32-311">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="1df32-312">MediatR je malý a jednoduchý knihovnu, která umožňuje zpracovávat zprávy v paměti jako příkaz, při použití dekoratéry nebo chování.</span><span class="sxs-lookup"><span data-stu-id="1df32-312">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="1df32-313">Pomocí vzoru zprostředkovatel vám pomůže snížit párování a k izolování obavy požadovanou práci, ale automatické připojení k obslužné rutině, který provádí tuto práci – v takovém případě do obslužné rutiny příkazů.</span><span class="sxs-lookup"><span data-stu-id="1df32-313">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="1df32-314">Jiné dobrý důvod, proč použití vzoru zprostředkovatel byl vysvětlené Jimmy Bogard při kontrole tohoto průvodce:</span><span class="sxs-lookup"><span data-stu-id="1df32-314">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="1df32-315">Myslím, že je zde testování za zmínku – obsahuje vylepšení vzhledu konzistentní okno na chování vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="1df32-315">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="1df32-316">V požadavku, odpověď na více instancí. Zjistili jsme tento aspekt poměrně cenné ve vytváření chová konzistentně testy.</span><span class="sxs-lookup"><span data-stu-id="1df32-316">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="1df32-317">Nejprve Podívejme se na řadiče WebAPI ukázky ve skutečnosti použít objekt zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="1df32-317">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="1df32-318">Pokud jste nepoužili zprostředkovatel objektu, je třeba vložit všechny závislosti pro tento kontroler, například objekt protokolovacího nástroje a další.</span><span class="sxs-lookup"><span data-stu-id="1df32-318">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="1df32-319">Konstruktor proto může být poměrně složitá.</span><span class="sxs-lookup"><span data-stu-id="1df32-319">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="1df32-320">Na druhé straně Pokud použijete objekt zprostředkovatel, konstruktor řadiče může být mnohem jednodušší, pomocí jenom pár mdildll velký počet závislostí, pokud jste měli jeden do každého vyskytující operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1df32-320">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="1df32-321">Uvidíte, že zprostředkovatel poskytuje přehledné a Štíhlá konstruktor kontroleru webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1df32-321">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="1df32-322">Kromě toho v metodách kontroleru, je kód odeslat příkaz k objektu zprostředkovatel téměř jeden řádek:</span><span class="sxs-lookup"><span data-stu-id="1df32-322">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="1df32-323">Implementace idempotentní příkazy</span><span class="sxs-lookup"><span data-stu-id="1df32-323">Implement idempotent Commands</span></span>

<span data-ttu-id="1df32-324">V **aplikaci eShopOnContainers**, pokročilejší příklad než výše posílá CreateOrderCommand objekt z mikroslužeb řazení.</span><span class="sxs-lookup"><span data-stu-id="1df32-324">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="1df32-325">Ale protože je o něco složitější obchodní proces objednávání a v našem případě ve skutečnosti spustí v košíku mikroslužeb, tato akce odeslání CreateOrderCommand objektu se provádí z obslužné rutiny události integrace s názvem > UserCheckoutAcceptedIntegrationEvent.cs] (https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) místo jednoduchých řadiče WebAPI volat z klientské aplikace jako v předchozím příkladu jednodušší.</span><span class="sxs-lookup"><span data-stu-id="1df32-325">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="1df32-326">Akce odeslání příkazu MediatR je však poměrně podobné, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1df32-326">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="1df32-327">Tento případ ale také trochu blíže advanced, protože jsme také implementace idempotentní příkazy.</span><span class="sxs-lookup"><span data-stu-id="1df32-327">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="1df32-328">Proces CreateOrderCommand by měly být idempotentní, takže pokud stejná zpráva pochází z důvodu z jakéhokoli důvodu, třeba opakovaných pokusů, duplicitní přes síť, stejné pořadí business se zpracuje jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="1df32-328">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="1df32-329">Toto je implementováno obchodní příkazy zabalit (v tomto případě CreateOrderCommand) a vloží jej do obecného IdentifiedCommand, což je sledován pomocí funkce ID každé zprávy přicházející přes síť, která má být idempotentní.</span><span class="sxs-lookup"><span data-stu-id="1df32-329">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="1df32-330">V následujícím kódu uvidíte, že IdentifiedCommand není nic jiného než objekt DTO se a ID plus zabalenou obchodní objekt příkazu.</span><span class="sxs-lookup"><span data-stu-id="1df32-330">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="1df32-331">Potom commandhandler – pro IdentifiedCommand s názvem [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) bude v podstatě zkontrolujte, jestli ID už jako část zprávy již existuje v tabulce.</span><span class="sxs-lookup"><span data-stu-id="1df32-331">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="1df32-332">Pokud již existuje, příkaz nebude zpracovat znovu, takže se chová jako příkaz idempotentní.</span><span class="sxs-lookup"><span data-stu-id="1df32-332">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="1df32-333">Že kód infrastruktury provádí `_requestManager.ExistAsync` volání metody níže.</span><span class="sxs-lookup"><span data-stu-id="1df32-333">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

<span data-ttu-id="1df32-334">Vzhledem k tomu, že IdentifiedCommand lze chápat jako obchodní příkaz obálky, když firmy příkazu je potřeba zpracovat, protože se nejedná o opakované Id, potom přebírá tento příkaz vnitřní firmy a znovu odešle zprostředkovatel, stejně jako v poslední části kódu uvedeného výše uvedený spuštění `_mediator.Send(message.Command)`, z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="1df32-334">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="1df32-335">Pokud to provedete, se propojit a spustit příkaz obslužnou rutinu obchodní, v tomto případě, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) jak je znázorněno v následujícím kódu, kterou je spuštěna transakce v databázi řazení.</span><span class="sxs-lookup"><span data-stu-id="1df32-335">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="1df32-336">Registrace typů používaných modulem MediatR</span><span class="sxs-lookup"><span data-stu-id="1df32-336">Register the types used by MediatR</span></span>

<span data-ttu-id="1df32-337">Aby MediatR zajímat vaší třídy obslužné rutiny příkazů budete muset zaregistrovat zprostředkovatel třídy a třídy obslužné rutiny příkazů v kontejneru IoC.</span><span class="sxs-lookup"><span data-stu-id="1df32-337">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="1df32-338">Ve výchozím nastavení MediatR používá jako kontejner IoC Autofac, ale můžete použít také předdefinované kontejner ASP.NET Core IoC nebo jiném kontejneru, podporuje MediatR.</span><span class="sxs-lookup"><span data-stu-id="1df32-338">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="1df32-339">Následující kód ukazuje, jak registrovat typy a příkazy pro zprostředkovatel při používání Autofac modulů.</span><span class="sxs-lookup"><span data-stu-id="1df32-339">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="1df32-340">Toto je umístění "všechno děje" s MediatR.</span><span class="sxs-lookup"><span data-stu-id="1df32-340">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="1df32-341">Protože každá obslužná rutina příkazu implementuje obecné `IAsyncRequestHandler<T>` rozhraní, při registraci sestavení, tento kód zaregistruje k `RegisteredAssemblyTypes` všechny typy označeny jako `IAsyncRequestHandler` při vztahující se `CommandHandlers` s jejich `Commands`, Děkujeme na vztah uvedenými v `CommandHandler` třídy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1df32-341">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="1df32-342">To je kód, který souvisí s obslužné rutiny příkazů příkazy.</span><span class="sxs-lookup"><span data-stu-id="1df32-342">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="1df32-343">Obslužná rutina je pouze jednoduchou třídu, ale dědí z `RequestHandler<T>`, kde T je typ příkazu, a zajišťuje MediatR vyvolání správné datová část (příkaz).</span><span class="sxs-lookup"><span data-stu-id="1df32-343">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="1df32-344">Při zpracování příkazů s chováním v MediatR platí vyskytující aspekty</span><span class="sxs-lookup"><span data-stu-id="1df32-344">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="1df32-345">Existuje ještě jedna věc: nebudou moct použít vyskytující aspekty do kanálu zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="1df32-345">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="1df32-346">Můžete také zobrazit na konci kód Autofac registrace modulu jak registruje typ chování, konkrétně, vlastní LoggingBehavior třídy a třídy ValidatorBehavior.</span><span class="sxs-lookup"><span data-stu-id="1df32-346">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="1df32-347">Ale můžete přidat další vlastní chování, příliš.</span><span class="sxs-lookup"><span data-stu-id="1df32-347">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="1df32-348">Že [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) třídy je možné implementovat jako následující kód, který ukládá do protokolu informace o obslužná rutina příkazu prováděný a bez ohledu na to, zda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1df32-348">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="1df32-349">Právě implementací této chování třídy a tak, že zaregistrujete v kanálu (v MediatorModule výše) všechny příkazy, které jsou zpracovány prostřednictvím MediatR protokolování informací o spuštění.</span><span class="sxs-lookup"><span data-stu-id="1df32-349">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="1df32-350">Aplikaci eShopOnContainers řazení mikroslužeb platí také druhý chování pro základní ověření [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) třídu, která se spoléhá na [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovny, jak je znázorněno Následující kód:</span><span class="sxs-lookup"><span data-stu-id="1df32-350">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="1df32-351">Chování zde je vyvolání výjimky, pokud se ověření nezdaří, ale může také vrátit objekt výsledku, obsahující výsledek příkazu, pokud byla úspěšná nebo ověření zprávy v případě, že se nepovedlo.</span><span class="sxs-lookup"><span data-stu-id="1df32-351">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="1df32-352">To by pravděpodobně bylo snazší zobrazit výsledky ověření pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="1df32-352">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="1df32-353">Potom na základě [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovny, jsme vytvořili ověření dat byla dokončena s CreateOrderCommand, stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1df32-353">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="1df32-354">Můžete například vytvořit další ověření.</span><span class="sxs-lookup"><span data-stu-id="1df32-354">You could create additional validations.</span></span> <span data-ttu-id="1df32-355">To je velmi čistá a elegantní způsob, jak implementovat vaše ověření příkaz.</span><span class="sxs-lookup"><span data-stu-id="1df32-355">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="1df32-356">Podobným způsobem je možné implementovat další chování pro další aspekty nebo převeďte společné aspekty, které chcete použít pro příkazy při jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="1df32-356">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1df32-357">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1df32-357">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="1df32-358">Zprostředkovatel vzor</span><span class="sxs-lookup"><span data-stu-id="1df32-358">The mediator pattern</span></span>

- <span data-ttu-id="1df32-359">**Zprostředkovatel vzor** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-359">**Mediator pattern** \\</span></span>
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="1df32-360">Vzor dekoratéru</span><span class="sxs-lookup"><span data-stu-id="1df32-360">The decorator pattern</span></span>

- <span data-ttu-id="1df32-361">**Vzor dekoratéru** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-361">**Decorator pattern** \\</span></span>
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="1df32-362">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="1df32-362">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="1df32-363">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="1df32-363">**MediatR.**</span></span> <span data-ttu-id="1df32-364">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="1df32-364">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="1df32-365">**CQRS s MediatR a AutoMapper** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-365">**CQRS with MediatR and AutoMapper** \\</span></span>
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="1df32-366">**Umístí kontrolerům vyváženosti: Příspěvky a příkazy.**</span><span class="sxs-lookup"><span data-stu-id="1df32-366">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="1df32-367">**Použití vyskytující aspekty s kanálem zprostředkovatel** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-367">**Tackling cross-cutting concerns with a mediator pipeline** \\</span></span>
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="1df32-368">**CQRS a REST: skvěle hodí** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-368">**CQRS and REST: the perfect match** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="1df32-369">**Příklady MediatR kanálu** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-369">**MediatR Pipeline Examples** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="1df32-370">**Svislé řez testovací zařízení pro MediatR a ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-370">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="1df32-371">**Rozšíření MediatR pro vkládání závislostí Microsoft všeobecně dostupné** \\</span><span class="sxs-lookup"><span data-stu-id="1df32-371">**MediatR Extensions for Microsoft Dependency Injection Released** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="1df32-372">Fluent ověření</span><span class="sxs-lookup"><span data-stu-id="1df32-372">Fluent validation</span></span>

- <span data-ttu-id="1df32-373">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="1df32-373">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="1df32-374">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="1df32-374">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="1df32-375">[Předchozí](microservice-application-layer-web-api-design.md)
> [další](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="1df32-375">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
