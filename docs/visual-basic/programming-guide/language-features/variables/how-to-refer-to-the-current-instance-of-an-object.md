---
title: 'Postupy: Odkazování na aktuální instanci objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: d166ce62a2bb0522d1ca7011aeff7afe076c2d8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542194"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Postupy: Odkazování na aktuální instanci objektu (Visual Basic)
*Aktuální instance* objektu je instance, ve kterém právě spouští kód.  
  
 Můžete použít `Me` – klíčové slovo k odkazování na aktuální instanci.  
  
### <a name="to-refer-to-the-current-instance"></a>K odkazování na aktuální instanci  
  
-   Použít `Me` – klíčové slovo, které běžně používáte název proměnné objektu.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     I když `Me` se chová stejně jako objekt proměnné, nelze ji deklarovat ani nic jí přiřadit. `Me` vždy odkazuje na aktuální instanci.  
  
## <a name="see-also"></a>Viz také:
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
