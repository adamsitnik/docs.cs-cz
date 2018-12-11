---
title: '&gt;&gt;= – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: aebc92ffb007db7b4950313874ebc2bf3c40615f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239443"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení posunutí doprava.  
  
## <a name="remarks"></a>Poznámky  
 Výraz ve tvaru  
  
```csharp  
x >>= y  
```  
  
 je vyhodnocen jako  
  
```csharp  
x = x >> y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [>> Operátor](../../../csharp/language-reference/operators/right-shift-operator.md) posune `x` přímo podle zadaného množství určené `y`.  
  
 >> = Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [>> operátor](../../../csharp/language-reference/operators/right-shift-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
