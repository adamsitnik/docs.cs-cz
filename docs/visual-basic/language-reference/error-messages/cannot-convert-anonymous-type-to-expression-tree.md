---
title: Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: ba14c0cd8781b8771ac8b746e3efec29a457294a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701179"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="32d88-102">Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.</span><span class="sxs-lookup"><span data-stu-id="32d88-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="32d88-103">Kompilátor nepřijímá převod anonymního na strom výrazu, pokud je použita jedna vlastnost anonymního typu k inicializaci jiné vlastnosti anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="32d88-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="32d88-104">Například v následujícím kódu je `Prop1` deklarován v inicializačním seznamu a pak použit jako počáteční hodnotu pro `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="32d88-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="32d88-105">**ID chyby:** BC36548</span><span class="sxs-lookup"><span data-stu-id="32d88-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32d88-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="32d88-106">To correct this error</span></span>  
  
- <span data-ttu-id="32d88-107">Přiřaďte počáteční hodnotu pro `Prop1` místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="32d88-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="32d88-108">Přiřaďte tuto proměnnou do obou `Prop1` a `Prop2`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="32d88-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```vb  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="32d88-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32d88-109">See also</span></span>

- [<span data-ttu-id="32d88-110">Anonymní typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d88-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="32d88-111">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d88-111">Expression Trees (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="32d88-112">Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d88-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
