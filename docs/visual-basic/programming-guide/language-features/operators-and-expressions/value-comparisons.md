---
title: Porovnání hodnot (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 270b226d0a1aa7d08721e6f9ed36d68492685af3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864388"
---
# <a name="value-comparisons-visual-basic"></a>Porovnání hodnot (Visual Basic)
Operátory porovnání lze použít k vytvoření výrazů, které porovnat hodnoty číselné proměnné. Vrátí tyto výrazy `Boolean` hodnotu podle toho, jestli porovnání hodnota true nebo false. Příklady takový výraz.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 První výraz je vyhodnocen jako `True`, protože je větší než 26 45. Druhý příklad je vyhodnocen jako `False`, protože není větší než 45 26.  
  
 Můžete také porovnat numerických výrazů tímto způsobem. Výrazy, které můžete porovnat mohou být samy složité výrazy, jako v následujícím příkladu.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Předchozí složitých výraz zahrnuje literály, proměnné a volání funkce. Výrazy na obou stranách operátoru porovnání jsou vyhodnoceny a výsledné hodnoty jsou pak porovnány pomocí `>=` operátor porovnání. Pokud je hodnota výrazu na levé straně je větší než nebo rovna hodnotě výraz na pravé straně, celý výraz vyhodnocen jako `True`; v opačném případě je vyhodnocen jako `False`.  
  
 Výrazy, které porovnat hodnoty se běžně používají v `If...Then` konstrukce, jako v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=` Podpis je operátor porovnání, stejně jako operátor přiřazení. Když se použije jako operátor porovnání, vyhodnotí, zda hodnota na levé straně je rovna hodnotě na pravé straně, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Výrazu porovnání lze také použít kdekoli `Boolean` hodnota je potřeba, například jako v `If`, `While`, `Loop`, nebo `ElseIf` příkazu, nebo když přiřadit nebo jejich předání hodnoty `Boolean` proměnné. V následujícím příkladu je přiřazená hodnota vrácená výrazu porovnání `Boolean` proměnné.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Viz také:

- [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operátory a výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Postupy: Výpočet numerických hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
