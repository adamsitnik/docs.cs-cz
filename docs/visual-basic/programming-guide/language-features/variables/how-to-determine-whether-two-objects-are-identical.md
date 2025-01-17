---
title: 'Postupy: Určení, zda dva objekty jsou identické (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: aae053ae0473ed6ced0f28da3d5e5afc0be629df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769080"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Postupy: Určení, zda dva objekty jsou identické (Visual Basic)
V jazyce Visual Basic odkazy na dvě proměnné jsou považovány za shodné, pokud jejich ukazatele jsou stejné, to znamená, pokud obě proměnné odkazovat na stejnou instanci třídy v paměti. Například v aplikaci Windows Forms, můžete chtít provést porovnání k určení, zda aktuální instance (`Me`) je stejný jako konkrétní instance, jako například `Form2`.  
  
 Visual Basic poskytuje dva operátory porovnání ukazatele. [Je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) vrátí `True` Pokud objekty jsou identické a [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) vrátí `True` Pokud tomu tak není.  
  
## <a name="determining-if-two-objects-are-identical"></a>Určení, zda dva objekty jsou identické  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Chcete-li zjistit, zda dva objekty jsou identické  
  
1. Nastavení `Boolean` výrazem, který testuje dva objekty.  
  
2. Ve výrazu testování, použijte `Is` se tyto dva objekty jako operandy operátoru.  
  
     `Is` Vrátí `True` Pokud objekty odkazovat na stejnou instanci třídy.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Určení, pokud dva objekty nejsou stejné  
 Někdy chcete provést akci, pokud dva objekty nejsou stejné, a může být nevhodnou zkombinovat `Not` a `Is`, například `If Not obj1 Is obj2`. V takovém případě můžete použít `IsNot` operátor.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Chcete-li zjistit, pokud dva objekty nejsou stejné  
  
1. Nastavení `Boolean` výrazem, který testuje dva objekty.  
  
2. Ve výrazu testování, použijte `IsNot` se tyto dva objekty jako operandy operátoru.  
  
     `IsNot` Vrátí `True` Pokud objekty neodkazují na stejnou instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad testuje dvojice `Object` proměnné zobrazíte, pokud ukazují na stejnou instanci třídy.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 V předchozím příkladu se zobrazí následující výstup.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Viz také:

- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Operátor Is](../../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Postupy: Určení, zda dva objekty souvisejí](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
