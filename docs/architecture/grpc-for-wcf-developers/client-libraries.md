---
title: Vytváření klientských knihoven gRPC – gRPC pro vývojáře WCF
description: Diskuze za sdílené klientské knihovny/balíčky pro služby gRPC Services.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 44a749c888528ca244f41b5b88354d7ed1db4190
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184587"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="d06ee-103">Vytváření klientských knihoven gRPC</span><span class="sxs-lookup"><span data-stu-id="d06ee-103">Create gRPC client libraries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d06ee-104">Není nutné distribuovat klientské knihovny pro aplikaci gPRC.</span><span class="sxs-lookup"><span data-stu-id="d06ee-104">It isn't necessary to distribute client libraries for a gPRC application.</span></span> <span data-ttu-id="d06ee-105">Můžete vytvořit sdílenou knihovnu `.proto` souborů v rámci vaší organizace a jiné týmy můžou tyto soubory použít k vygenerování kódu klienta ve svých vlastních projektech.</span><span class="sxs-lookup"><span data-stu-id="d06ee-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="d06ee-106">Pokud ale máte soukromé úložiště NuGet a spousta dalších týmů používá .NET Core, vytváření a publikování balíčků NuGet klienta jako součást projektu služby může být dobrým způsobem, jak sdílet a propagovat vaši službu.</span><span class="sxs-lookup"><span data-stu-id="d06ee-106">But if you have a private NuGet repository and many other teams are using .NET Core, creating and publishing client NuGet packages as part of your service project may be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="d06ee-107">Jednou z výhod distribuce klientské knihovny je, že můžete vylepšit vygenerované třídy gRPC a Protobuf s využitím užitečných metod a vlastností "pohodlí".</span><span class="sxs-lookup"><span data-stu-id="d06ee-107">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="d06ee-108">V klientském kódu, jako na serveru, jsou deklarovány všechny třídy, jako `partial` by je bylo možné roztáhnout bez úprav generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d06ee-108">In the client code, as in the server, all the classes are declared as `partial` so you can extend them without editing the generated code.</span></span> <span data-ttu-id="d06ee-109">To znamená, že je snadné přidat konstruktory, metody, počítané vlastnosti a další základní typy.</span><span class="sxs-lookup"><span data-stu-id="d06ee-109">This means it's easy to add constructors, methods, calculated properties, and more to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="d06ee-110">**Neměli byste používat vlastní** kód pro poskytování základních funkcí, protože by to znamenalo, že by byla funkce omezena na týmy .NET pomocí sdílené knihovny, a ne pro týmy, které používají jiné jazyky nebo platformy, jako je Python nebo Java.</span><span class="sxs-lookup"><span data-stu-id="d06ee-110">You should **not** use custom code to provide essential functionality, as this would mean that functionality would be restricted to .NET teams using the shared library, and not to teams using other languages or platforms such as Python or Java.</span></span>

<span data-ttu-id="d06ee-111">V prostředí s více platformami, kde různé týmy často používají různé programovací jazyky a rozhraní nebo kde je vaše rozhraní API externě přístupné, stačí sdílet `.proto` soubory, aby vývojáři mohli vygenerovat své vlastní klienty, je nejlepším způsobem, jak Ujistěte se, že máte přístup ke službě gRPC, abyste měli k dispozici co nejvíce týmů.</span><span class="sxs-lookup"><span data-stu-id="d06ee-111">In a multi-platform environment where different teams frequently use different programming languages and frameworks, or where your API is externally accessible, simply sharing `.proto` files so developers can generate their own clients is the best way to ensure as many teams as possible can access your gRPC service.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="d06ee-112">Užitečná rozšíření</span><span class="sxs-lookup"><span data-stu-id="d06ee-112">Useful extensions</span></span>

<span data-ttu-id="d06ee-113">V rozhraní .NET existují dvě běžně používaná rozhraní pro práci s datovými proudy objektů <xref:System.Collections.Generic.IEnumerable%601> : <xref:System.IObservable%601>a.</span><span class="sxs-lookup"><span data-stu-id="d06ee-113">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="d06ee-114">Počínaje .NET Core 3,0 a C# 8,0 je k dispozici <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní pro asynchronní zpracování datových proudů a `await foreach` syntaxi pro použití rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d06ee-114">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="d06ee-115">V této části najdete opakovaně použitelný kód pro použití těchto rozhraní pro gRPC streamy.</span><span class="sxs-lookup"><span data-stu-id="d06ee-115">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="d06ee-116">S klientskými knihovnami .NET Core gRPC existuje `ReadAllAsync` metoda rozšíření pro `IAsyncStreamReader<T>` , která vytvoří `IAsyncEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="d06ee-116">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>`.</span></span> <span data-ttu-id="d06ee-117">Pro vývojáře, kteří používají reaktivní programování, `IObservable<T>` může to vypadat stejně jako metoda rozšíření, která by mohla vypadat.</span><span class="sxs-lookup"><span data-stu-id="d06ee-117">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` might look like this.</span></span>

### <a name="iobservable"></a><span data-ttu-id="d06ee-118">IObservable</span><span class="sxs-lookup"><span data-stu-id="d06ee-118">IObservable</span></span>

<span data-ttu-id="d06ee-119">Rozhraní je "reaktivní" `IEnumerable<T>`inverzní. `IObservable<T>`</span><span class="sxs-lookup"><span data-stu-id="d06ee-119">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="d06ee-120">Místo přijímání položek z datového proudu umožňuje reaktivní přístup streamování nabízených položek odběrateli.</span><span class="sxs-lookup"><span data-stu-id="d06ee-120">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="d06ee-121">To je velmi podobné datovým proudům gRPC a snadno se zalomí `IObservable<T>` `IAsyncStreamReader<T>`kolem.</span><span class="sxs-lookup"><span data-stu-id="d06ee-121">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` around an `IAsyncStreamReader<T>`.</span></span>

<span data-ttu-id="d06ee-122">Tento kód je delší než `IAsyncEnumerable<T>` kód, protože C# nemá integrovanou podporu pro práci s observables, takže třídu implementace je třeba vytvořit ručně.</span><span class="sxs-lookup"><span data-stu-id="d06ee-122">This code is longer than the `IAsyncEnumerable<T>` code because C# doesn't have built-in support for working with observables, so the implementation class has to be created manually.</span></span> <span data-ttu-id="d06ee-123">Je to ale obecná třída, takže jediná implementace bude fungovat napříč všemi typy.</span><span class="sxs-lookup"><span data-stu-id="d06ee-123">It's a generic class, though, so a single implementation will work across all types.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public Observable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="d06ee-124">Tato možná implementace umožňuje `Subscribe` pouze volání metody pouze jednou, protože více odběratelů, kteří se pokoušejí o čtení z datového proudu, by způsobilo chaos.</span><span class="sxs-lookup"><span data-stu-id="d06ee-124">This observable implementation only allows the `Subscribe` method to be called once, as having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="d06ee-125">Existují operátory, jako je `Replay` například v [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq) , které umožňují ukládání do vyrovnávací paměti a opakované sdílení observables, které lze použít s touto implementací.</span><span class="sxs-lookup"><span data-stu-id="d06ee-125">There are operators such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="d06ee-126">Třída zpracovává výčet `IAsyncStreamReader`. `GrpcStreamSubscription`</span><span class="sxs-lookup"><span data-stu-id="d06ee-126">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`.</span></span>

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public Subscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

<span data-ttu-id="d06ee-127">Vše, co je potřeba, je teď jednoduchá rozšiřující metoda, která umožňuje vytvořit pozorovatelnou z čtecího modulu streamu.</span><span class="sxs-lookup"><span data-stu-id="d06ee-127">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a><span data-ttu-id="d06ee-128">Souhrn</span><span class="sxs-lookup"><span data-stu-id="d06ee-128">Summary</span></span>

<span data-ttu-id="d06ee-129">Modely `IAsyncEnumerable` a`IObservable` jsou dobře podporované a dobře dokumentované způsoby práce s asynchronními datovými proudy dat v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d06ee-129">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="d06ee-130">gRPC datové proudy jsou dobře namapované na obě paradigma, nabízí těsnou integraci s moderními rozhraními .NET Core a reaktivními nebo asynchronními programovacími styly.</span><span class="sxs-lookup"><span data-stu-id="d06ee-130">gRPC streams map well to both paradigms, offering close integration with the modern .NET Core framework and reactive/asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d06ee-131">[Předchozí](streaming-versus-repeated.md)
>[Další](security.md)</span><span class="sxs-lookup"><span data-stu-id="d06ee-131">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>