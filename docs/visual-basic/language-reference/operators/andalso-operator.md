---
title: AndAlso – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835230"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso – operátor (Visual Basic)
Provede krátkodobé rozvodu logického spojení na dvou výrazech.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`result`|Požadováno. Libovolný výraz `Boolean`. Výsledkem je `Boolean` výsledek porovnání dvou výrazů.|  
|`expression1`|Požadováno. Libovolný výraz `Boolean`.|  
|`expression2`|Požadováno. Libovolný výraz `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 Logická operace je označována jako *krátká* , pokud zkompilovaný kód může obejít vyhodnocení jednoho výrazu v závislosti na výsledku jiného výrazu. Pokud výsledek prvního vyhodnoceného výrazu určí konečný výsledek operace, není nutné vyhodnotit druhý výraz, protože nemůže změnit konečný výsledek. Krátkodobé okruhy mohou zvýšit výkon, pokud je výraz obcházení složitý, nebo pokud zahrnuje volání procedur.  
  
 Pokud jsou oba výrazy vyhodnoceny jako `True`, `result` je `True`. Následující tabulka ukazuje, jak je určena `result`.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(nehodnoceno)|`False`|  
  
## <a name="data-types"></a>Datové typy  
 Operátor `AndAlso` je definován pouze pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic převede každý operand podle potřeby, aby `Boolean` před vyhodnocením výrazu. Pokud přiřadíte výsledek číselnému typu, Visual Basic jej převede z `Boolean` na tento typ tak, aby `False` se staly `0` a `True` se `-1`.
Další informace naleznete v tématu [převody logických typů](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Přetížení  
 [Operátor and](../../../visual-basic/language-reference/operators/and-operator.md) a operátor s hodnotou [false](../../../visual-basic/language-reference/operators/isfalse-operator.md) mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, je-li operand typu této třídy nebo struktury. Přetížení operátorů `And` a `IsFalse` má vliv na chování operátoru `AndAlso`. Pokud váš kód používá `AndAlso` u třídy nebo struktury, která přetěžuje `And` a `IsFalse`, ujistěte se, že rozumíte jejich předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `AndAlso` k provedení logického spojení se dvěma výrazy. Výsledkem je hodnota @no__t 0, která představuje, zda je úplný výraz JOIN pravdivý. Pokud je první výraz `False`, druhý se nevyhodnotí.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Předchozí příklad vytvoří výsledky `True`, `False` a `False` v uvedeném pořadí. Při výpočtu `secondCheck` není druhý výraz vyhodnocen, protože první je již `False`. Nicméně druhý výraz je vyhodnocen při výpočtu `thirdCheck`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje postup @no__t 0, který vyhledá danou hodnotu mezi prvky pole. Pokud je pole prázdné nebo pokud byla překročena délka pole, příkaz `While` netestuje prvek pole proti hledané hodnotě.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor And](../../../visual-basic/language-reference/operators/and-operator.md)
- [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
