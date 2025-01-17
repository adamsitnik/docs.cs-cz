---
title: asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bde6f6e625476712c5af516491ab9dd29b7dea3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052963"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
Pokud se vlákno pokusí zavést asynchronní přerušení do jiného vlákna, aktivuje se pomocník spravovanéholadění(MDA).`asynchronousThreadAbort` Synchronní přerušení vlákna neaktivují modul `asynchronousThreadAbort` MDA.

## <a name="symptoms"></a>Příznaky
 Dojde k selhání aplikace s neošetřenou <xref:System.Threading.ThreadAbortException> při přerušení hlavního vlákna aplikace. Pokud by aplikace pokračovala v provádění, může to být horší než selhání aplikace, což může vést k dalšímu poškození dat.

 Operace, které mají být atomické, byly pravděpodobně přerušeny po částečném dokončení a data aplikace budou ponechána v nepředvídatelném stavu. <xref:System.Threading.ThreadAbortException> Může být vygenerován z zdánlivě náhodných bodů při provádění kódu, často v místech, ze kterých není očekávána výjimka. Kód nemusí být schopen zpracovat takovou výjimku, což vede k poškozenému stavu.

 Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.

## <a name="cause"></a>příčina
 Kód v jednom vlákně, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> který se nazývá metoda v cílovém vláknu k zavedení asynchronního přerušení vlákna. Přerušení vlákna je asynchronní, protože kód, který provádí volání <xref:System.Threading.Thread.Abort%2A> , je spuštěn v jiném vlákně, než je cílem operace Abort. Synchronní přerušení vlákna by neměla způsobovat problém, protože vlákno, které provádí, <xref:System.Threading.Thread.Abort%2A> by mělo být provedeno pouze v bezpečném kontrolním bodu, kde je stav aplikace konzistentní.

 Asynchronní vlákno přerušuje problém, protože jsou zpracovávány v nepředvídatelných bodech v provádění cílového vlákna. Aby k tomu nedocházelo, kód napsaný pro spuštění ve vlákně, který může být přerušen tímto způsobem, by musel <xref:System.Threading.ThreadAbortException> zpracovat téměř každý řádek kódu a přitom zajistit, aby se data aplikace vrátila do konzistentního stavu. Nejedná se o realistickou situaci, kdy očekáváte, že se kód bude zapisovat s tímto problémem, nebo jestli chcete napsat kód, který chrání před všemi možnými okolnostmi.

 Volání do nespravovaného `finally` kódu a bloky nebudou asynchronně přerušeny, ale okamžitě po ukončení jedné z těchto kategorií.

 Příčina může být obtížné určit z důvodu náhodnosti podstaty problému.

## <a name="resolution"></a>Řešení
 Vyhněte se návrhu kódu, který vyžaduje použití asynchronního přerušení vlákna. Existuje několik přístupů, které jsou vhodnější pro přerušení cílového vlákna, které nevyžadují volání <xref:System.Threading.Thread.Abort%2A>. Nejbezpečnější je zavedení mechanismu, jako je například společná vlastnost, která signalizuje cílovému vláknu, aby požadoval přerušení. Cílové vlákno kontroluje signál u určitých bezpečných kontrolních bodů. Pokud si vyžádá, že bylo vyžadováno přerušení, může se řádně vypnout.

## <a name="effect-on-the-runtime"></a>Vliv na modul runtime
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o přerušení asynchronního vlákna.

## <a name="output"></a>Výstup
 MDA hlásí ID vlákna, které provádí přerušení, a ID vlákna, které je cílem přerušení. Nebudou nikdy stejné, protože to je omezeno na asynchronní přerušení.

## <a name="configuration"></a>Konfiguraci

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Příklad
 Aktivace služby <xref:System.Threading.Thread.Abort%2A> MDA vyžaduje pouze volání do samostatného běžícího vlákna. `asynchronousThreadAbort` Zvažte důsledky, pokud je obsah funkce spuštění vlákna množinou složitějších operací, které mohou být přerušeny v libovolném okamžiku přerušení.

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
