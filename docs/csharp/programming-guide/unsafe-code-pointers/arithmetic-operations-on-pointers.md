---
title: Aritmetické operace na ukazatelích - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: b0b75a6aa47cfc169157b229c4386ed7dc1e627b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710193"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Aritmetické operace na ukazatelích (C# Programming Guide)
Toto téma popisuje použití aritmetické operátory `+` a `-` manipulace s ukazateli.  
  
> [!NOTE]
>  Nelze provést všechny aritmetické operace u ukazatelů typu void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Přičítání a odečítání číselné hodnoty do nebo z ukazatele  
 Můžete přidat hodnotu `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) na ukazatel. Pokud `p` je ukazatel typu `pointer-type*`, výsledek `p+n` je ukazatel výsledkem přidání `n * sizeof(pointer-type)` na adresu `p`. Obdobně `p-n` je ukazatel výsledkem odečtením `n * sizeof(pointer-type)` z adresy `p`.  
  
## <a name="subtracting-pointers"></a>Odečtení ukazatele  
 Můžete rovněž odečíst ukazateli stejného typu. Výsledek je vždy typu `long`. Například pokud `p1` a `p2` jsou ukazatele typ `pointer-type*`, pak výraz `p1-p2` výsledkem:  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 Při přetečení aritmetické operace domény ukazatele a výsledek závisí na implementaci, nejsou generovány žádné výjimky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
- [Manipulace s ukazateli](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
