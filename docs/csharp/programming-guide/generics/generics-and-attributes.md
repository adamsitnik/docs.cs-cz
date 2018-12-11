---
title: Obecné typy a atributy - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 35244ce33902760c2a0d3d8bda3181097f7ca38e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245178"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Obecné typy a atributy (Průvodce programováním v C#)
Atributy lze použít na obecných typech stejným způsobem jako obecné typy. Další informace o použití atributů naleznete v tématu [atributy](../../../csharp/programming-guide/concepts/attributes/index.md).  
  
 Vlastní atributy jsou povolené jenom tak, aby odkazovaly otevřených obecných typů, které jsou obecné typy, pro kterou žádný typ jsou zadané argumenty a uzavřený konstruovaný obecné typy, které zadat argumenty pro všechny parametry typu.  
  
 Následující příklady používají tento vlastní atribut:  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 Otevřený obecný typ. může odkazovat na atribut:  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Zadejte více parametrů typu pomocí příslušného počtu čárkami. V tomto příkladu `GenericClass2` má dva parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Uzavřený Konstruovaný obecný typ může odkazovat na atribut:  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Atribut, který odkazuje na parametr obecného typu způsobí chybu kompilace:  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Obecný typ nelze dědit z <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Pokud chcete získat informace o obecném typu nebo parametr typu v době běhu, můžete použít metody <xref:System.Reflection>. Další informace najdete v tématu [obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
- [Atributy](../../../../docs/standard/attributes/index.md)
