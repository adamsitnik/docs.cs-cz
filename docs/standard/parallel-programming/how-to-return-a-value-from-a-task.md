---
title: 'Postupy: Vrácení hodnoty z úlohy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df928ec6494da6da368b3cef1f1d25a84a692aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764527"
---
# <a name="how-to-return-a-value-from-a-task"></a>Postupy: Vrácení hodnoty z úlohy
Tento příklad znázorňuje používání typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> pro vrácení hodnoty z vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A>. Vyžaduje, aby adresář C:\Users\Public\Pictures\Sample Pictures\ existoval a aby obsahoval soubory.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje volající vlákno, dokud úkol neskončí.  
  
 Informace o tom, k předání výsledku jedné vlastnosti <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> úkolu pokračování naleznete v tématu [řetězení úloh pomocí úloh pokračování používání](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
