---
title: Pole jako objekty - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0bbbf7ecc5eff650f7a2edc73546833afd2be094
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242331"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)

V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelný oblastech souvislé paměti jako v jazyce C a C++. <xref:System.Array> je abstraktní základní typ pro všechny typy polí. Můžete použít vlastnosti a ostatních členů třídy, která <xref:System.Array> má. Příklad tohoto by pomocí <xref:System.Array.Length%2A> vlastnost získat délku pole. Následující kód přiřadí délka `numbers` pole, které je `5`, proměnné s názvem `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, hledání a kopírování polí.  
  
## <a name="example"></a>Příklad

 V tomto příkladu <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
