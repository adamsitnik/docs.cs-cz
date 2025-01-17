---
title: 'Postupy: Kombinování paralelních a sekvenčních LINQ dotazů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 4c04afb23a168a9cff60962bd5a75a65e3ebca4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134184"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Postupy: Kombinování paralelních a sekvenčních LINQ dotazů
Tento příklad ukazuje, jak použít metodu <xref:System.Linq.ParallelEnumerable.AsSequential%2A> k tomu, aby PLINQ zpracovával všechny následné operátory v dotazu sekvenčně. I když je sekvenční zpracování obecně pomalejší než paralelní, někdy je potřeba, abyste naprodukovali správné výsledky.  
  
> [!WARNING]
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jeden scénář, ve kterém je vyžadováno <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, a to proto, aby bylo zachováno řazení, které bylo vytvořeno v předchozí klauzuli dotazu.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li zkompilovat a spustit tento kód, vložte jej do projektu [ukázkového data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) , přidejte řádek pro volání metody z `Main`a stiskněte klávesu F5.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
