---
title: Sub – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 2330b410f54b54d8f6cb7d8ad6f9b39a3f4d31bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701340"
---
# <a name="sub-expression-visual-basic"></a>Sub – výraz (Visual Basic)
Deklaruje parametry a kód definující výraz subrutiny lambda.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`parameterlist`|Volitelné. Seznam místních názvů proměnných, které reprezentují parametry procedury. Závorky musí být přítomny i v případě, že je seznam prázdný. Další informace najdete v tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Požadováno. Jediný příkaz.|  
|`statements`|Požadováno. Seznam příkazů.|  
  
## <a name="remarks"></a>Poznámky  
 *Výraz lambda* je podprogram, který nemá název a který provádí jeden nebo více příkazů. Můžete použít výraz lambda kdekoli, kde můžete použít typ delegáta, s výjimkou argumentu pro `RemoveHandler`. Další informace o delegátech a použití výrazů lambda s delegáty naleznete v tématu [příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) a [odlehčený převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda  
 Syntaxe výrazu lambda se podobá standardní podrutině. Rozdíly jsou následující:  
  
- Výraz lambda nemá název.  
  
- Výraz lambda nemůže obsahovat modifikátor, například `Overloads` nebo `Overrides`.  
  
- Tělo výrazu lambda s jedním řádkem musí být příkaz, nikoli výraz. Tělo může být tvořeno voláním procedury Sub, ale nikoli voláním procedury funkce.  
  
- Ve výrazu lambda musí mít buď všechny parametry zadané datové typy, nebo musí být všechny parametry odvozeny.  
  
- Volitelné parametry a parametry `ParamArray` nejsou ve výrazech lambda povoleny.  
  
- Obecné parametry nejsou ve výrazech lambda povoleny.  
  
## <a name="example"></a>Příklad  
 Následuje příklad výrazu lambda, který zapisuje hodnotu do konzoly. V příkladu se zobrazuje jak jednoduchá, tak víceřádková syntaxe výrazu lambda pro podprogram. Další příklady naleznete v tématu [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
