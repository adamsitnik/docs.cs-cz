---
title: Potenciální nástrahy PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 85098a0d10b4c05de52cd33d30ec5c4f4bbc594d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140000"
---
# <a name="potential-pitfalls-with-plinq"></a>Potenciální nástrahy PLINQ

V mnoha případech může PLINQ poskytnout významné zlepšení výkonu při sekvenčních dotazech LINQ to Objects. Práce virtuálního provádění dotazů však zavádí složitost, která může vést k problémům, které se v sekvenčním kódu nevyskytují jako běžné nebo nejsou vůbec k dispozici. Toto téma uvádí některé postupy, které se vyhnete při psaní dotazů PLINQ.

## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nepředpokládat, že paralelní je vždycky rychlejší

Paralelismus někdy způsobí, že se PLINQ dotaz spustí pomaleji, než je jeho ekvivalent LINQ to Objects. Základní pravidlo pro palec je, že dotazy, které mají málo zdrojových elementů a rychlé delegáty uživatele, jsou pravděpodobně zrychlení mnohem nepravděpodobné. Vzhledem k tomu, že je v výkonu mnoho faktorů, doporučujeme změřit skutečné výsledky před rozhodnutím, jestli chcete použít PLINQ. Další informace naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápisu do sdílených umístění paměti

V sekvenčním kódu není běžné číst z nebo zapisovat do statických proměnných nebo polí třídy. Kdykoli však více vláken přistupuje k těmto proměnným současně, existuje velký potenciál pro konflikty časování. I když můžete použít zámky k synchronizaci přístupu k proměnné, náklady na synchronizaci můžou snížit výkon. Proto doporučujeme, abyste se vyhnuli nebo alespoň omezili přístup ke sdílenému stavu v dotazu PLINQ co nejvíce.

## <a name="avoid-over-parallelization"></a>Vyhnout se paralelnímu využití

Pomocí operátoru `AsParallel` se účtují režijní náklady na rozdělení zdrojové kolekce a synchronizaci pracovních vláken. Výhody paralelismu jsou dále omezeny počtem procesorů v počítači. Neexistují žádné zrychlení, které by bylo možné vymezit spuštěním více výpočetních vláken vázaných na pouze jeden procesor. Proto musíte mít pozor, abyste paralelizovat dotaz.

Nejběžnější scénář, ve kterém může dojít k paralelnímu navýšení, je ve vnořených dotazech, jak je znázorněno v následujícím fragmentu kódu.

[!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

V takovém případě je nejlepší paralelizovat jenom vnější zdroj dat (Customers), pokud neplatí jedna nebo víc z těchto podmínek:

- Vnitřní zdroj dat (zák. Objednávky) se označují jako velmi dlouhé.

- V každé objednávce provádíte nákladný výpočet. (Operace uvedená v příkladu není nákladná.)

- Pro cílový systém je známo, že má dostatek procesorů pro zpracování počtu vláken, která budou vytvořena virtuálního dotazem na `cust.Orders`.

Ve všech případech je nejlepším způsobem, jak určit optimální obrazec dotazu, testování a měření. Další informace najdete v tématu [Postupy: měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>Nepoužívejte volání metod, které nejsou bezpečné pro přístup z více vláken

Zápis na metody instancí bez bezpečného přístupu z více vláken může vést k poškození dat, které může nebo nemusí být v programu nedetekováno. Může také vést k výjimkám. V následujícím příkladu se více vláken pokusí zavolat metodu `FileStream.Write` současně, což není podporováno třídou.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>Omezení volání metod bezpečných pro přístup z více vláken

Většina statických metod v .NET Framework je bezpečná pro přístup z více vláken a je možné ji volat z více vláken současně. Nicméně i v těchto případech může synchronizace vést k významnému zpomalení dotazu.

> [!NOTE]
> Můžete to otestovat sami vložením některých volání do <xref:System.Console.WriteLine%2A> v dotazech. I když se tato metoda používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v dotazech PLINQ.

## <a name="avoid-unnecessary-ordering-operations"></a>Vyhnout se zbytečným operacím řazení

Když PLINQ spustí dotaz paralelně, rozdělí zdrojovou sekvenci na oddíly, které lze provozovat souběžně ve více vláknech. Ve výchozím nastavení je pořadí, ve kterém jsou oddíly zpracovávány, a výsledky jsou dodány (s výjimkou operátorů, jako je například `OrderBy`). Můžete určit, aby PLINQ zachoval řazení libovolné zdrojové sekvence, ale má negativní vliv na výkon. Nejlepší postup, kdykoli je to možné, je strukturování dotazů, které nespoléhají na zachování pořadí. Další informace naleznete v tématu [pořadí zachování v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Preferovat ForAll na ForEach, pokud je to možné

I když PLINQ spustí dotaz ve více vláknech, pokud použijete výsledky ve smyčce `foreach` (`For Each` ve Visual Basic), musí být výsledky dotazu sloučeny zpět do jednoho vlákna a budou se k němu přihlížet sériovým enumerátorem. V některých případech to není nevyhnutelné; kdykoli je to možné, použijte metodu `ForAll`, abyste každému vláknu umožnili výstup vlastních výsledků, například zapsáním do kolekce bezpečné pro přístup z více vláken, jako je například <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.

Stejný problém se týká <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jinými slovy, `source.AsParallel().Where().ForAll(...)` by měl být důrazně upřednostňován na

`Parallel.ForEach(source.AsParallel().Where(), ...)`.

## <a name="be-aware-of-thread-affinity-issues"></a>Informace o problémech spřažení vláken

Některé technologie, například interoperabilita modelu COM pro součásti s jedním vláknem (STA), model Windows Forms a Windows Presentation Foundation (WPF), ukládají omezení spřažení vláken, která vyžadují spouštění kódu v konkrétním vlákně. Například v model Windows Forms i WPF může být ovládací prvek k dispozici pouze ve vlákně, ve kterém byl vytvořen. Pokud se pokusíte o přístup ke sdílenému stavu ovládacího prvku model Windows Forms v PLINQ dotazu, je vyvolána výjimka, pokud je spuštěn v ladicím programu. (Toto nastavení se dá vypnout.) Nicméně pokud je váš dotaz použit ve vlákně uživatelského rozhraní, pak můžete získat přístup k ovládacímu prvku z `foreach`ové smyčky, která vytvoří výčet výsledků dotazu, protože tento kód se spouští pouze v jednom vlákně.

## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládáme, že iterace ForEach, for a ForAll vždy provádějí paralelně

Je důležité pamatovat na to, že jednotlivé iterace v <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčka nemusí být spouštěny paralelně. Proto byste se měli vyhnout psaní kódu, který závisí na správnosti paralelního provádění iterací nebo při provádění iterací v jakémkoli konkrétním pořadí.

Například tento kód může zablokovat:

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

V tomto příkladu jedna iterace nastaví událost a všechny ostatní iterace na událost čekají. Žádná z čekacích iterací nemůže být dokončena, dokud se nedokončí iterace nastavení události. Je však možné, že čekající iterace zablokují všechna vlákna, která se používají ke spuštění paralelní smyčky, před tím, než bude iterace nastavení událostí vykonána. Výsledkem je zablokování – iterace nastavení události se nikdy nespustí a čekací iterace se nikdy neprobudí.

Konkrétně jedna iterace paralelní smyčky by nikdy neměla čekat na další iteraci smyčky, aby bylo možné postupovat. Pokud se paralelní smyčka rozhodne naplánovat iterace sekvenčně, ale v opačném pořadí, dojde k zablokování.

## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
