---
title: Implementace úloh na pozadí v mikroslužbách s IHostedService a BackgroundService třídy
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Zjistěte, nové možnosti použití IHostedService a BackgroundService implementace úloh na pozadí v mikroslužby .NET Core.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: b262f5352f62e74ec184e2e00e8cff3aeecc2f64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760868"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementace úloh na pozadí v mikroslužbách s IHostedService a BackgroundService třídy

Naplánované úlohy a úlohy na pozadí jsou něco, co možná budete muset implementovat, případně v aplikaci na základě mikroslužeb nebo v jakékoliv aplikaci. Rozdíl při použití architektury mikroslužeb je, že můžete implementovat jednu mikroslužbu procesu/kontejner pro hostování tyto úlohy na pozadí, takže je možné ji dolů/nahoru škálovat podle musíte nebo dokonce zajistit, že běží jedna instance, která mikroslužby procesu nebo kontejneru.

Z obecného pohledu, v .NET Core zavolali jsme na těchto typů úkolů *služeb hostovaných v*, protože jsou služby a logiku, která hostujete v rámci vašeho hostitele/aplikace/mikroslužeb. Všimněte si, že v tomto případě hostovanou službu jednoduše znamená, že třída s atributem logiky úloh na pozadí.

Od verze rozhraní .NET Core 2.0, rozhraní poskytuje nové rozhraní s názvem <xref:Microsoft.Extensions.Hosting.IHostedService> vám pomáhá snadno implementovat hostované služby. Základní myšlenka je, že můžete registrovat několika úloh na pozadí (hostované služby), které běží na pozadí při webového hostitele nebo hostiteli běží, jak je znázorněno na obrázku 6-26.

![ASP.NET Core 1.x a 2.x podpora IWebHost pozadí zpracovává ve službě web apps, .NET Core, 2,1 podporuje IHost pro procesy na pozadí s jednoduché konzolové aplikace.](./media/image26.png)

**Obrázek 6-26**. Použití IHostedService v webového hostitele a hostitele

Všimněte si rozdílu mezi `WebHost` a `Host`.

A `WebHost` (základní třídy implementující `IWebHost`) v ASP.NET Core 2.0 je artefaktů infrastruktury vám poskytují HTTP server s funkcí pro váš proces, třeba když implementujete MVC webové aplikace nebo služba webového rozhraní API. Poskytuje všechny nové infrastruktury přesnosti v ASP.NET Core, která vám umožní pomocí vkládání závislostí, vložit middlewares v požadavku kanálu atd a pomocí nich přesně `IHostedServices` pro úlohy na pozadí.

A `Host` (základní třídy implementující `IHost`) byla zavedena v rozhraní .NET Core 2.1. V podstatě `Host` umožňuje mít podobné infrastruktury, než máte s `WebHost` (injektáž závislostí, hostovaných služeb atd.), ale v tomto případě chcete mít jednoduchou a lehčí proces jako hostitele, není nic související s MVC , Webové rozhraní API nebo HTTP funkce serveru.

Proto můžete použít a buď vytvořte specializované hostitelský proces s IHost hostovaným službám a nic jiného, mikroslužby, vytvořená speciálně pro hostování `IHostedServices`, nebo můžete případně rozšířit stávající ASP.NET Core `WebHost` , jako je například existující aplikaci webového rozhraní API ASP.NET Core nebo MVC.

Každý přístup má výhody a nevýhody v závislosti na potřebách vaší firmy a škálovatelnost. Dolní řádek je v podstatě, že pokud vaše úlohy na pozadí nemají co dělat s protokolem HTTP (IWebHost) byste měli použít IHost.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Registrace hostovaných služeb v webového hostitele nebo hostitele

Můžeme přejít na další nižší `IHostedService` rozhraní, protože jeho používání je hodně podobné jako u `WebHost` nebo v `Host`.

SignalR je jeden příklad artefakt pomocí hostovaných služeb, ale můžete ho můžete použít pro jednodušší věci, jako je:

- Dotazování databáze hledá změny úlohy na pozadí.
- Naplánované úlohy pravidelně aktualizuje některé mezipaměti.
- Implementace QueueBackgroundWorkItem umožňující úkol má být proveden na vlákně na pozadí.
- Zpracování zpráv z fronty zpráv z webové aplikace na pozadí při sdílení běžné služby jako například `ILogger`.
- Spustit úlohu na pozadí s `Task.Run()`.

V podstatě můžete přesměrovat některou z těchto akcí pro úlohu na pozadí podle IHostedService.

Způsob, jak přidat jeden nebo více `IHostedServices` do vaší `WebHost` nebo `Host` je tak, že je zaregistrujete si prostřednictvím standardních DI (injektáž závislostí) v ASP.NET Core `WebHost` (nebo `Host` v .NET Core 2.1 a vyšší). V podstatě, je nutné provést registraci hostovaných služeb v rámci známé `ConfigureServices()` metodu `Startup` třídy, jako v následujícím kódu z typických tomuto webovému hostiteli technologie ASP.NET.

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

V tomto kódu `GracePeriodManagerService` hostovanou službu je z mikroslužeb obchodní řazení v aplikaci eShopOnContainers skutečného kódu, ale jiné dva jsou jenom dvě další ukázky.

`IHostedService` Provedení úlohy na pozadí se koordinují s životního cyklu aplikací (hostitele nebo mikroslužeb, k tomuto účelu). Zaregistrujete úlohy při spuštění aplikace a budete mít příležitost provést určitou akci řádné nebo čištění po aplikaci se vypíná.

Bez použití `IHostedService`, může vždy spustit vlákno na pozadí ke spuštění každého úkolu. Rozdíl je přesně v době vypnutí aplikace, kdy bylo vlákno by jednoduše ukončeny bez nutnosti příležitosti ke spouštění řádné akcí čištění.

## <a name="the-ihostedservice-interface"></a>Rozhraní IHostedService

Když se zaregistrujete `IHostedService`, zavolá .NET Core `StartAsync()` a `StopAsync()` metody vaše `IHostedService` zadejte při spuštění aplikace a zastavit v uvedeném pořadí. Konkrétně start se volá, když server spuštěn a `IApplicationLifetime.ApplicationStarted` se aktivuje.

`IHostedService` Jak jsou definovány v .NET Core, vypadá podobně jako následující.

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```

Jak si dokážete představit, můžete vytvořit více implementací IHostedService a zaregistrujte je v `ConfigureService()` metoda do kontejnerů DI, jak bylo uvedeno výše. Všechny tyto hostované služby se a zastavování spolu s aplikací/mikroslužeb.

Jako vývojář je zodpovědná za zpracování akce zastavení nebo služby při `StopAsync()` metoda aktivuje hostitele.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementace IHostedService pomocí vlastní hostované služby třídu odvozenou z BackgroundService základní třídy

Můžete pokračovat a vytvoření zcela nové třídě vlastní hostovanou službu a implementovat `IHostedService`, jako je třeba provést při použití .NET Core 2.0.

Protože většina úloh na pozadí mají podobné potřeby správy tokeny zrušení a další běžné operace, neexistuje však vhodné abstraktní základní třídu lze odvodit z, s názvem `BackgroundService` (dostupné od verze rozhraní .NET Core 2.1).

Tuto třídu poskytuje hlavní práce potřebné k nastavení úlohy na pozadí.

Následující kód je abstraktní základní třída BackgroundService, jak je implementován v .NET Core.

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

Při odvozování z předchozí abstraktní základní třída, díky zděděná implementace, stačí k implementaci `ExecuteAsync()` metoda ve vlastní hostované třídy služby, viz následující příklad zjednodušená kódu v aplikaci eShopOnContainers, což je interval dotazování databáze a publikování události integrace do sběrnice událostí v případě potřeby.

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        //Constructor’s parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMS / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

V tomto konkrétním případě pro aplikaci eShopOnContainers je prováděna metodu aplikace, který se dotazuje tabulku databáze hledá objednávky se specifickým stavem, a při použití změn, je publikování události integrace přes Service bus událostí (pod tím může být s použitím RabbitMQ nebo Azure Service Bus).

Samozřejmě můžete spustit žádné jiné obchodní úlohy na pozadí, místo toho.

Ve výchozím nastavení, token rušení, který je nastavena s 5 druhý časový limit, i když tuto hodnotu můžete změnit při sestavování vašich `WebHost` pomocí `UseShutdownTimeout` rozšíření `IWebHostBuilder`. To znamená, že naše služby má zrušit v rámci jinak 5 sekund více náhlé ukončení dojde.

Následující kód by změna této doby na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Třída shrnutí diagramu

Následující obrázek ukazuje vizuál přehled tříd a připojený používané při implementaci IHostedServices.

![Diagram tříd: Mnoho služeb, které dědí nastavení z BackgroundService, která implementuje IHostedService můžete hostovat IWebHost a IHost.](./media/image27.png)

**Obrázek 6 – 27**. Diagram tříd zobrazující více tříd a rozhraní související s IHostedService

### <a name="deployment-considerations-and-takeaways"></a>Důležité informace o nasazení a takeaways

Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít vliv na konečné řešení. Například při nasazení vaší `WebHost` na serveru IIS nebo pravidelné službě Azure App Service, může být vypnut hostitele kvůli recyklace fondu aplikací. Ale pokud nasazujete hostitele jako kontejner do orchestrátoru, jako je Kubernetes nebo Service Fabric, můžete řídit pojištěných počet instancí za provozu z hostitele. Kromě toho zvažte další přístupy v cloudu, zejména provedené pro tyto scénáře, jako je Azure Functions. Nakonec pokud potřebujete služby běžet neustále a provádíte nasazení na Windows serveru můžete použít službu Windows.

Ale i pro `WebHost` nasazené do fondu aplikací, jsou scénáře, jako jsou opětovného vyplnění nebo vyprazdňování mezipaměti v paměti aplikace, která bude i nadále použitelná.

`IHostedService` Rozhraní poskytuje pohodlný způsob, jak spustit úlohy na pozadí v ASP.NET Core webovou aplikaci (v .NET Core 2.0) nebo v procesu/hostitele (počínaje verzí .NET Core 2.1 s `IHost`). Jeho hlavní výhodou je příležitost, kterou dostanete s řádné zrušení na kód pro vyčištění vaše úlohy na pozadí, když se vypíná samotného hostitele.

#### <a name="additional-resources"></a>Další zdroje

- **Vytvoření naplánované úlohy v technologii ASP.NET Core/Standard 2.0** <br/>
    <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementace IHostedService v ASP.NET Core 2.0** <br/>
    <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **Ukázka GenericHost pomocí ASP.NET Core 2.1** <br/>
    <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Předchozí](test-aspnet-core-services-web-apps.md)
>[další](implement-api-gateways-with-ocelot.md)