---
title: 'Postupy: Vyvolávání a zpracovávání událostí'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 256b5ae9ac2145e339136985872dfa5423aca730
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131586"
---
# <a name="how-to-raise-and-consume-events"></a>Postupy: Vyvolávání a zpracovávání událostí
Příklady v tomto tématu ukazují, jak pracovat s událostmi. Obsahují příklady delegáta <xref:System.EventHandler>, <xref:System.EventHandler%601> delegáta a vlastního delegáta pro ilustraci událostí s daty a bez nich.  
  
 Příklady používají koncepty popsané v článku [události](../../../docs/standard/events/index.md) .  
  
## <a name="example"></a>Příklad  
 První příklad ukazuje, jak vyvolat a zpracovat událost, která nemá data. Obsahuje třídu s názvem `Counter`, která má událost s názvem `ThresholdReached`. Tato událost se vyvolá, když je hodnota čítače rovna nebo přesahuje prahovou hodnotu. Delegát <xref:System.EventHandler> je přidružen k události, protože nejsou k dispozici žádná data události.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje, jak vyvolat a zpracovat událost, která poskytuje data. Delegát <xref:System.EventHandler%601> je přidružen k události a je k dispozici instance vlastního datového objektu události.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje, jak deklarovat delegáta pro událost. Delegát má název `ThresholdReachedEventHandler`. Tohle je jenom ilustrace. Obvykle není nutné deklarovat delegáta pro událost, protože můžete použít buď <xref:System.EventHandler>, nebo delegáta <xref:System.EventHandler%601>. Delegáta byste měli deklarovat pouze ve výjimečných případech, jako je například zpřístupnění třídy staršímu kódu, který nemůže používat obecné typy.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Události](../../../docs/standard/events/index.md)
