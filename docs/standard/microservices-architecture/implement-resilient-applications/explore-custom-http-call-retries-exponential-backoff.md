---
title: Prozkoumejte vlastních opakování volání HTTP pomocí exponenciálního omezení rychlosti
description: Zjistěte, jak je možné implementovat opakování volání HTTP pomocí exponenciálního omezení rychlosti, od začátku pro zpracování možných scénářů chyby protokolu HTTP.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: fdbc09cddde34cb8897e1d5b105cb15c863b59ce
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362246"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Prozkoumejte vlastních opakování volání HTTP pomocí exponenciálního omezení rychlosti

K vytvoření odolné mikroslužeb, potřebujete zpracovávat možných scénářů chyby protokolu HTTP. Jedním ze způsobů zpracování těchto chyb, však není doporučena, je vytvořit vlastní implementace opakování pomocí exponenciálního omezení rychlosti.

**Důležitá poznámka:** Tato část popisuje, jak můžete vytvořit vlastní kód pro implementaci opakování volání HTTP. Však není doporučený postup na vlastní ale určený výkonnější a spolehlivé, zatímco je jednodušší použít mechanismy, jako například `HttpClientFactory` pomocí knihovny Polly dostupné od verze rozhraní .NET Core 2.1. Tyto doporučené postupy jsou vysvětlené v následujících částech.

Jako počáteční zkoumání, je možné implementovat vlastního kódu s využitím třídy nástrojů pro exponenciálního omezení rychlosti jako v [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus kód jako následující.

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

Pomocí tohoto kódu v klientovi C\# aplikace (jiného webového rozhraní API klienta mikroslužeb, aplikaci ASP.NET MVC nebo dokonce C\# aplikace Xamarin) je jednoduché. Následující příklad ukazuje, jak pomocí třídy HttpClient.

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

Mějte na paměti, že tento kód je vhodný pouze jako testování konceptu. Další části popisují, jak používat složitější přístupy, zatímco je jednodušší, pomocí HttpClientFactory. HttpClientFactory je k dispozici od verze rozhraní .NET Core 2.1 s knihovnami osvědčené odolnost proti chybám, jako je Polly.

>[!div class="step-by-step"]
>[Předchozí](implement-resilient-entity-framework-core-sql-connections.md)
>[další](use-httpclientfactory-to-implement-resilient-http-requests.md)