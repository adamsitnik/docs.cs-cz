---
title: Porovnání WCF s gRPC-gRPC pro vývojáře WCF
description: Porovnání rozhraní WCF a gRPC pro vytváření distribuovaných aplikací.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c763048d09e7ed5ca0a3d5240f6b3cf5262f897c
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184041"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="73cae-103">Porovnávání WCF s gRPC</span><span class="sxs-lookup"><span data-stu-id="73cae-103">Comparing WCF to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="73cae-104">Předchozí kapitola by měla mít za cíl dobrý pohled na Protobuf a způsob, jakým gRPC zpracovává zprávy.</span><span class="sxs-lookup"><span data-stu-id="73cae-104">The previous chapter should have given you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="73cae-105">Před provedením podrobného převodu z WCF na gRPC je důležité pohlížet na to, jak se rozsah funkcí aktuálně dostupných ve službě WCF zpracovává v gRPC a jaká alternativní řešení můžete použít, když se zdá, že se nejeví jako ekvivalentní gRPC.</span><span class="sxs-lookup"><span data-stu-id="73cae-105">Before working through a detailed conversion from WCF to gRPC, it's important to look at how the range of features currently available in WCF are handled in gRPC and what workarounds you can use when there doesn't appear to be a gRPC equivalent.</span></span> <span data-ttu-id="73cae-106">Konkrétně tato kapitola se zabývá následujícími tématy:</span><span class="sxs-lookup"><span data-stu-id="73cae-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="73cae-107">Operace a metody</span><span class="sxs-lookup"><span data-stu-id="73cae-107">Operations and methods</span></span>
- <span data-ttu-id="73cae-108">Vazby a přenosy</span><span class="sxs-lookup"><span data-stu-id="73cae-108">Bindings and transports</span></span>
- <span data-ttu-id="73cae-109">Typy RPC</span><span class="sxs-lookup"><span data-stu-id="73cae-109">RPC types</span></span>
- <span data-ttu-id="73cae-110">Metadata</span><span class="sxs-lookup"><span data-stu-id="73cae-110">Metadata</span></span>
- <span data-ttu-id="73cae-111">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="73cae-111">Error handling</span></span>
- <span data-ttu-id="73cae-112">\* Protokoly WS</span><span class="sxs-lookup"><span data-stu-id="73cae-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="73cae-113">Příklad gRPC</span><span class="sxs-lookup"><span data-stu-id="73cae-113">gRPC example</span></span>

<span data-ttu-id="73cae-114">Při vytváření nového projektu ASP.NET Core 3,0 gRPC ze sady Visual Studio 2019 nebo příkazového řádku, je pro vás vygenerován ekvivalent gRPC "Hello World".</span><span class="sxs-lookup"><span data-stu-id="73cae-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="73cae-115">Skládá se ze `greeter.proto` souboru, který definuje službu a její zprávy `GreeterService.cs` a soubor s implementací služby.</span><span class="sxs-lookup"><span data-stu-id="73cae-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

<span data-ttu-id="73cae-116">Tato kapitola bude odkazovat na tento ukázkový kód při vysvětlení různých konceptů a funkcí gRPC.</span><span class="sxs-lookup"><span data-stu-id="73cae-116">This chapter will refer to this example code when explaining various concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="73cae-117">[Předchozí](protobuf-maps.md)
>[Další](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="73cae-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>