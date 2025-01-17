---
title: Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 06dc6f1532fecefba4e507bd0cc24aadc936d137
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524369"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.

Proměnná deklarovaná jako Nullable byla porovnána s výrazem jiným než `Nothing` pomocí operátoru `IsNot`.

**ID chyby:** BC32128

## <a name="to-correct-this-error"></a>Oprava této chyby

Chcete-li porovnat typ s možnou hodnotou null na jiný výraz než `Nothing` pomocí operátoru `IsNot`, zavolejte metodu `GetType` pro typ s možnou hodnotou null a porovnejte výsledek s výrazem, jak je znázorněno v následujícím příkladu.

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>Viz také:

- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
