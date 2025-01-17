---
title: 'Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137978"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání
Pokud je metoda zablokovaná, zatímco čeká na signál události, nemůže kontrolovat hodnotu tokenu zrušení a včas reagovat. První příklad ukazuje, jak tento problém vyřešit při práci s událostmi, jako je <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, které nativně nepodporují jednotné rozhraní zrušení. Druhý příklad ukazuje jednodušší přístup, který používá <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, který podporuje jednotné zrušení.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEvent> k předvedení odblokování čekacích obslužných rutin, které nepodporují jednotné zrušení.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEventSlim> k demonstrování, jak odblokovat koordinační primitivní prvky, které podporují jednotné zrušení. Stejný přístup lze použít s jinými zjednodušenými primitivními primitivy, například <xref:System.Threading.Semaphore>`Slim` a <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
