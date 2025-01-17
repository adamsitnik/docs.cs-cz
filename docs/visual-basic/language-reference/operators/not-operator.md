---
title: Not – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 5ebc5f9dbf674a9a6560bd96b3e8c9edcae08a81
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701078"
---
# <a name="not-operator-visual-basic"></a>Not – operátor (Visual Basic)
Provede logickou negaci pro výraz @no__t 0 nebo bitovou negaci číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
 `expression`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 U výrazů `Boolean` ukazuje následující tabulka, jak se určuje `result`.  
  
|Pokud `expression` je|Hodnota `result` je|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 U numerických výrazů operátor `Not` Invertuje bitové hodnoty libovolného číselného výrazu a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|If bit v `expression` je|Bit v `result` je|  
|-------------------------------|----------------------------|  
|první|0,8|  
|0,8|první|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
## <a name="data-types"></a>Datové typy  
 Pro logickou negaci je datový typ výsledku `Boolean`. Pro bitovou negaci je výsledný datový typ stejný jako u `expression`. Pokud je však výraz `Decimal`, výsledek je `Long`.  
  
## <a name="overloading"></a>Přetížení  
 Operátor `Not` může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Not` k provedení logické negace na výrazu `Boolean`. Výsledkem je hodnota @no__t 0, která představuje opačnou hodnotu výrazu.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Předchozí příklad vytvoří výsledky `False` a `True` v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Not` k provedení logické negace jednotlivých bitů číselného výrazu. Bit ve vzorci výsledků je nastaven na zpětný výsledek odpovídajícího bitu ve vzoru operandu, včetně bitu znaménka.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Předchozí příklad vytvoří výsledky – 11, – 9 a – 7 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
