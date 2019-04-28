---
title: Obecná rozhraní - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 09b8200d19b6f94cab423dbe4001fbeda83aa06f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710651"
---
# <a name="generic-interfaces-c-programming-guide"></a>Obecná rozhraní (Průvodce programováním v C#)
Často je užitečné k definování rozhraní pro obecné kolekce tříd nebo pro obecné třídy, které představují položek v kolekci. Předvolby pro obecné třídy, je pomocí obecných rozhraní, jako <xref:System.IComparable%601> spíše než <xref:System.IComparable>, aby se zabránilo operace zabalení a rozbalení u typů hodnot. Definuje několik obecných rozhraní pro použití s kolekcí tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.  
  
 Pokud je zadána jako omezení pro parametr typu, je možné pouze typy, které implementují rozhraní. Následující příklad kódu ukazuje `SortedList<T>` třídu odvozenou od `GenericList<T>` třídy. Další informace najdete v tématu [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>` Přidá omezení `where T : IComparable<T>`. Díky tomu `BubbleSort` metoda `SortedList<T>` museli používat obecná <xref:System.IComparable%601.CompareTo%2A> metodu na seznamu elementů. V tomto příkladu, prvky seznamu jsou jednoduchá třída `Person`, který implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Několik rozhraní se dá nastavit jako omezení u jednoho typu, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Rozhraní může definovat více než jeden parametr typu, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Pravidla dědičnosti, které se vztahují na třídy platí také pro rozhraní:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Obecná rozhraní může dědit z rozhraní Obecné, pokud obecného rozhraní je kontravariantní, což znamená, že pouze jako návratová hodnota používá jeho typu parametru. V knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable> protože <xref:System.Collections.Generic.IEnumerable%601> využívat jenom takové `T` v návratové hodnotě <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metoda getter vlastnosti.  
  
 Konkrétní třídy mohou implementovat rozhraní uzavřený konstruovaný, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Obecné třídy můžete implementovat obecné rozhraní nebo uzavřený konstruovaný rozhraní za předpokladu, seznam parametrů třídy poskytuje všechny argumenty, které vyžadují rozhraní, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Pravidla, která řídí přetížení metody jsou stejné pro metody v rámci obecných tříd, obecné struktury nebo obecná rozhraní. Další informace najdete v tématu [obecné metody](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [interface](../../../csharp/language-reference/keywords/interface.md)
- [Obecné typy](~/docs/standard/generics/index.md)
