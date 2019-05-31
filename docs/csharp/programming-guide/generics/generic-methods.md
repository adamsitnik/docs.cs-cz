---
title: Obecné metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 083fc6ff3dd15252fb6cf2beb27b5be0a6e489f5
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423444"
---
# <a name="generic-methods-c-programming-guide"></a>Obecné metody (Průvodce programováním v C#)
Obecná metoda je metoda, která je deklarována s parametry typu, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Následující příklad kódu ukazuje jeden způsob, jak volat metodu pomocí `int` pro argument typu:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Také můžete vynechat argument typu a kompilátor odvodí. Následující volání `Swap` je ekvivalentem předchozího volání:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Stejná pravidla pro odvození typu platí pro statické metody a metody instance. Kompilátor může odvodit typ parametrů na základě argumentů metody, které můžete předat nelze jej odvodit jenom z omezení parametry typu nebo návratovou hodnotu. Odvození typu proměnné proto nefunguje s metodami, které mají žádné parametry. Odvození typu vyvolá v době kompilace předtím, než kompilátor pokusí přeložit podpisy přetížené metody. Kompilátor použije logiku odvození typu na všechny obecné metody, které mají stejný název. V kroku rozlišení přetížení kompilátor obsahuje pouze tyto obecné metody, na které bylo úspěšné odvození typu proměnné.  
  
 V rámci obecné třídy neobecné metody mají přístup k úrovni třídy typové parametry, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 Při definování obecné metody, která má stejné parametry typu jako obsahující třídu, kompilátor vygeneruje upozornění CS0693, protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argument zadaný pro vnější `T`. Pokud požadujete flexibilitu volání metody obecnou třídu s argumenty typů než ty, pokud byla vytvořena instance třídy, zvažte poskytnutí jiný identifikátor pro typ parametru metody, jak je znázorněno v `GenericList2<T>` následující Příklad.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Umožňuje povolit více specializované operace u parametrů typu v metodách omezení. Tato verze `Swap<T>`teď s názvem `SwapIfGreater<T>`, lze použít pouze s argumenty typů, které implementují <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Obecné metody lze přetížit na několik parametrů typu. Například následující metody můžete všechny nacházet ve stejné třídě:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
