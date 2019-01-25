---
title: 'Postupy: Zpracování výjimek v paralelních smyčkách'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ef883f37587948871b222ca03a4032bea2109bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711418"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Postupy: Zpracování výjimek v paralelních smyčkách
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> přetížení nemají žádný zvláštní mechanismus zpracování výjimek, které mohou být vyvolány. V tomto ohledu se podobají pravidelně `for` a `foreach` smyčky (`For` a `For Each` v jazyce Visual Basic); neošetřené výjimky způsobí, že smyčku ukončit okamžitě.  
  
 Když přidáte vlastní logiku zpracování výjimek pro paralelní smyčky, zpracovávat tento případ, ve kterém může být podobné výjimky vyvolána z více vláken současně a tento případ, ve kterém výjimce v jednom vlákně způsobí, že další výjimku, která je vyvolána na jiném vlákno. Obou případech může zpracovávat všechny výjimky ze smyčky v zabalení <xref:System.AggregateException?displayProperty=nameWithType>. Následující příklad ukazuje jednu z možných způsobů.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, který je znázorněn v následujícím příkladu. Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou všechny výjimky zachycena a potom zabalené v <xref:System.AggregateException?displayProperty=nameWithType> která je vyvolána výjimka. Volající může rozhodnout, které výjimky pro zpracování.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
