---
title: Vícerozměrná pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: d5663062815f0c85772aa0e30f5edeac654431b8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242214"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Vícerozměrná pole (Průvodce programováním v C#)

Pole může mít více než jeden rozměr. Například následující deklaraci vytvoří dvourozměrné pole čtyři řádky a dva sloupce.  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 Následující deklarace je vytvořeno pole tří dimenze, 4, 2 a 3.  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Inicializace pole

 Inicializovat pole při deklaraci, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 Také můžete inicializovat pole bez určení pořadí.  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 Pokud se rozhodnete pro deklaraci proměnné pole bez inicializace, je nutné použít `new` operátor přiřazení pole do proměnné. Použití `new` je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 Následující příklad přiřadí hodnotu konkrétního pole elementu.  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 Obdobně následující příklad získá hodnotu prvku konkrétní pole a přiřadí ji k proměnné `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 Následující příklad kódu inicializuje prvky pole, které mají výchozí hodnoty (s výjimkou vícenásobných polí).  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
