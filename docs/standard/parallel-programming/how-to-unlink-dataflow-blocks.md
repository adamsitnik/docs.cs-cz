---
title: 'Postupy: Zrušení propojení bloků toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 989220141e4af5d64c3994479949547136843ff5
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591992"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Postupy: Zrušení propojení bloků toku dat
Tento dokument popisuje, jak zrušit propojení cílový blok toku dat z jeho zdroje.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekty, každý z který volá `TrySolution` metodu za účelem výpočtu hodnoty. Tento příklad vyžaduje pouze výsledky z prvního volání `TrySolution` na dokončení.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Pro příjem hodnoty z prvního <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> definuje objekt, který je dokončen, v tomto příkladu `ReceiveFromAny(T)` metoda. `ReceiveFromAny(T)` Metoda přijímá pole <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektů a každý z těchto objektů do odkazů <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu. Při použití <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metoda odkaz bloku toku dat zdrojového na cílový blok, zdroj šíří zprávy na cíl, jak budou data k dispozici. Protože <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> třídy přijímá pouze první zprávu, která je k dispozici, `ReceiveFromAny(T)` metoda vytváří výsledek voláním <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody. Tímto se vytvoří první zprávu, která je nabízena <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda je přetížené verze, která přebírá <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> objektu <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> vlastnost, když je nastaveno na `1`, dává pokyn zdrojový blok se zrušit propojení z cíle, až cílový obdrží jednu zprávu ze zdroje . Je důležité pro <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu, který chcete odpojit ze zdrojů, protože vztah mezi poli zdrojů a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt se už nevyžaduje po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt přijme zprávu.  
  
 Povolit zbývající volání `TrySolution` k ukončení po jeden z nich vypočítá hodnotu, `TrySolution` přijímá metodu <xref:System.Threading.CancellationToken> objekt, který je zrušen po volání `ReceiveFromAny(T)` vrátí. <xref:System.Threading.SpinWait.SpinUntil%2A> Metoda vrátí, když to <xref:System.Threading.CancellationToken> objektu se zruší.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
