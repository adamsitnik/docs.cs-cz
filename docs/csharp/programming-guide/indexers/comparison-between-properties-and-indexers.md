---
title: Porovnání mezi vlastnostmi a indexery - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 41b27905edb8a0e00a6af5a4cce38988161326d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537722"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
Indexery jsou stejné jako vlastnosti. S výjimkou rozdílů je znázorněno v následující tabulce všechna pravidla, které jsou definovány pro přistupující objekty vlastnosti platí pro přistupující objekty indexer také.  
  
|Vlastnost|Indexer|  
|--------------|-------------|  
|Povoluje metody, která se má volat, jakoby byly veřejné datové členy.|Umožňuje elementy vnitřní objekt přistupovat pomocí zápisu pole na samotného objektu kolekce.|  
|Je možný přes jednoduchý název.|Přístup pomocí indexu.|  
|Může být statická nebo člena instance.|Musí být člen instance.|  
|A [získat](../../../csharp/language-reference/keywords/get.md) přistupující objekt vlastnosti nemá žádné parametry.|A `get` stejného seznamu formálních parametrů jako indexeru má přistupující objekt indexeru.|  
|A [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametru.|A `set` přistupující objekt indexeru má stejného seznamu formálních parametrů jako indexeru a také [hodnotu](../../../csharp/language-reference/keywords/value.md) parametru.|  
|Podporuje zkrátila syntaxe [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Nepodporuje zkrácený syntaxi.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Indexery](../../../csharp/programming-guide/indexers/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
