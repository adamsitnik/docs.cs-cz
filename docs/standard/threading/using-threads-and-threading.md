---
title: Použití vláken a dělení na vlákna
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 863fa565f7c107214273912a6d110b7664bffe6b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131502"
---
# <a name="using-threads-and-threading"></a>Použití vláken a dělení na vlákna

Pomocí technologie .NET můžete psát aplikace, které provádějí více operací současně. Operace s potenciálním provozem jiných operací se můžou spouštět v samostatných vláknech, *což je proces* , který se označuje jako *vícevláknové nebo volné podprocesy*.  
  
Aplikace, které používají multithreading, mají větší reakci na uživatelský vstup, protože uživatelské rozhraní zůstává aktivní jako úlohy náročné na procesory spouštěné v samostatných vláknech. Multithreading je také užitečné při vytváření škálovatelných aplikací, protože je možné přidat vlákna při zvýšení zatížení.

> [!NOTE]
> Pokud potřebujete větší kontrolu nad chováním vláken aplikace, můžete spravovat vlákna sami. Počínaje .NET Framework 4 se však vícevláknové programování značně zjednodušilo pomocí tříd <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Paralelní LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md), nové třídy souběžných kolekcí v oboru názvů <xref:System.Collections.Concurrent?displayProperty=nameWithType> a nový programovací model. který je založen na konceptu úkolů, nikoli na vláknech. Další informace naleznete v tématu [paralelní programování](../parallel-programming/index.md) a [Task PARALLEL Library (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Postupy: vytvoření a spuštění nového vlákna

Vytvoříte nové vlákno vytvořením nové instance třídy <xref:System.Threading.Thread?displayProperty=nameWithType> a zadáním názvu metody, kterou chcete spustit v novém vlákně konstruktoru. Chcete-li spustit vytvořené vlákno, zavolejte metodu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Další informace a příklady najdete v článku [vytváření vláken a předávání dat v čase spuštění](creating-threads-and-passing-data-at-start-time.md) a Reference k rozhraní API <xref:System.Threading.Thread>.

## <a name="how-to-stop-a-thread"></a>Postupy: zastavení vlákna

Chcete-li ukončit provádění vlákna, použijte metodu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Tato metoda vyvolává <xref:System.Threading.ThreadAbortException> ve vlákně, ve kterém je vyvolána. Další informace naleznete v tématu [zničení vláken](destroying-threads.md).

Počínaje .NET Framework 4 můžete použít <xref:System.Threading.CancellationToken?displayProperty=nameWithType> k kooperativnímu zrušení vlákna. Další informace naleznete v tématu [zrušení ve spravovaných vláknech](cancellation-in-managed-threads.md).

Použijte metodu <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> k tomu, aby volající vlákno čekalo na ukončení vlákna, ve kterém je metoda vyvolána.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Postupy: pozastavení nebo přerušení vlákna

Použijte metodu <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> k pozastavení aktuálního vlákna po zadanou dobu. Blokované vlákno lze přerušit voláním metody <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>. Další informace najdete v tématu [pozastavení a přerušení vláken](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Vlastnosti vlákna

Následující tabulka uvádí některé vlastnosti <xref:System.Threading.Thread>:  
  
|Vlastnost|Popis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Vrátí `true`, pokud bylo vlákno spuštěno a dosud nebylo ukončeno normálně nebo přerušeno.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Získá nebo nastaví logickou hodnotu, která označuje, zda se jedná o vlákno na pozadí. Vlákna na pozadí jsou jako vlákna na popředí, ale vlákno na pozadí nezabrání procesu v jeho zastavení. Po zastavení všech vláken na popředí, která patří do procesu, ukončí modul CLR (Common Language Runtime) proces voláním metody <xref:System.Threading.Thread.Abort%2A> na vláknech na pozadí, které jsou stále aktivní. Další informace naleznete v tématu [vlákna v popředí a na pozadí](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Získá nebo nastaví název vlákna. Nejčastěji se používá ke zjišťování jednotlivých vláken při ladění.|  
|<xref:System.Threading.Thread.Priority%2A>|Získá nebo nastaví hodnotu <xref:System.Threading.ThreadPriority>, která je používána operačním systémem k určení priorit plánování vláken. Další informace naleznete v tématu [plánování vláken](scheduling-threads.md) a <xref:System.Threading.ThreadPriority> reference.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Získá <xref:System.Threading.ThreadState> hodnotu obsahující aktuální stavy vlákna.|  

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Paralelní programování](../parallel-programming/index.md)
