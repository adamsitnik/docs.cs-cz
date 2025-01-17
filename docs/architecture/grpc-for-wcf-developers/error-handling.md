---
title: Zpracování chyb – gRPC pro vývojáře WCF
description: BUDE URČENO K ZÁPISU
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 91f5789d8ed0f01f3ce2f3f9a6c6ccf14f245290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094225"
---
# <a name="error-handling"></a>Zpracování chyb

WCF používá `FaultException<T>` a `FaultContract` k poskytnutí podrobných informací o chybách, včetně podpory standardu SOAP chyb.

Aktuální verze gRPC bohužel neobsahuje sofistikovanější nalezené ve službě WCF a má pouze omezené integrované zpracování chyb na základě jednoduchých stavových kódů a metadat. V následující tabulce je Stručná příručka k nejčastěji používaným stavovým kódům:

| Stavový kód | Problém |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Metoda nebyla zapsána. |
| `GRPC_STATUS_UNAVAILABLE` | Problém s celou službou. |
| `GRPC_STATUS_UNKNOWN` | Neplatná odpověď. |
| `GRPC_STATUS_INTERNAL` | Problém s kódováním/dekódováním. |
| `GRPC_STATUS_UNAUTHENTICATED` | Ověřování se nezdařilo. |
| `GRPC_STATUS_PERMISSION_DENIED` | Autorizace se nezdařila. |
| `GRPC_STATUS_CANCELLED` | Volání bylo zrušeno, obvykle volající. |

## <a name="raising-errors-in-aspnet-core-grpc"></a>Vyvolávání chyb v ASP.NET Core gRPC

Služba ASP.NET Core gRPC může odeslat chybovou odpověď vyvoláním `RpcException`, kterou může klient zachytit, jako kdyby byl ve stejném procesu. `RpcException` musí zahrnovat stavový kód a popis a může volitelně zahrnovat metadata a delší zprávu o výjimce. Metadata lze použít k odesílání podpůrných dat, podobně jako `FaultContract` objekty mohou mít další data pro chyby WCF.

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catching-errors-in-grpc-clients"></a>Zachycení chyb v klientech gRPC

Stejně jako klienti WCF můžou zachytit chyby <xref:System.ServiceModel.FaultException%601>, klient gRPC může zachytit `RpcException` a zpracovávat chyby. Vzhledem k tomu, že `RpcException` není obecný typ, nemůžete zachytávání různých typů chyb v různých blocích C#, ale můžete použít funkci *filtrů výjimek* pro deklaraci samostatných`catch`ch bloků pro různé stavové kódy, jak je znázorněno v následujícím příkladu:

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException)
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> Když zadáte další metadata pro chyby, nezapomeňte zdokumentovat příslušné klíče a hodnoty v dokumentaci k rozhraní API nebo v komentářích v souboru `.proto`.

## <a name="grpc-richer-error-model"></a>Model gRPC bohatých chyb

Těšíme se na to, že Google vyvinul [model s](https://cloud.google.com/apis/design/errors#error_model) větším množstvím chyb, jako je například [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale C# ještě není podporován. V současné době je dostupná jenom pro jazyky for, Java, Python C++a, ale očekává C# se, že se bude příští rok přicházet k podpoře.

>[!div class="step-by-step"]
>[Předchozí](metadata.md)
>[Další](ws-protocols.md)
