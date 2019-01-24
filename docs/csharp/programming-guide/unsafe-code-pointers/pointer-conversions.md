---
title: Převody ukazatele - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 8fa1c1442d146c9d2fbdb2fa969b2e29d7ef765d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498304"
---
# <a name="pointer-conversions-c-programming-guide"></a>Převody ukazatele (Průvodce programováním v C#)
V následující tabulce jsou předdefinované ukazatel implicitní převody. Implicitní převod může dojít v mnoha situacích, včetně příkazů metody vyvolání a přiřazení.  
  
## <a name="implicit-pointer-conversions"></a>Implicitní ukazatel převody  
  
|From|Chcete-li|  
|----------|--------|  
|Libovolný typ ukazatele|typ void *|  
|null|Libovolný typ ukazatele|  
  
 Převod ukazatele explicitní slouží k provádění převodů, pro které neexistuje žádný implicitní převod, pomocí výrazu přetypování. V následující tabulce jsou uvedeny tyto převody.  
  
## <a name="explicit-pointer-conversions"></a>Převody ukazatele explicitní  
  
|From|Chcete-li|  
|----------|--------|  
|Libovolný typ ukazatele|Jiný typ ukazatele|  
|SByte, byte, short, ushort, int, uint, long nebo ulong|Libovolný typ ukazatele|  
|Libovolný typ ukazatele|SByte, byte, short, ushort, int, uint, long nebo ulong|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, ukazatel na `int` je převeden na ukazatel na `byte`. Všimněte si, že ukazatel odkazuje na nejnižší adresovaný bajtů proměnné. Když postupně zvyšovat výsledek, až do velikosti `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
