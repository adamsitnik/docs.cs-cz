---
title: První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: a73a66313e7ca540711838c4d147d6bd163ec8d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625571"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="53b0a-102">První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="53b0a-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="53b0a-103">`If` Výraz může trvat dvě až tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="53b0a-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="53b0a-104">Když posíláte pouze dva argumenty, první argument musí být typu odkaz nebo typ připouštějící hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="53b0a-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="53b0a-105">Pokud je první argument vyhodnocen jako cokoli jiného než `Nothing`, je tato hodnota vrácena.</span><span class="sxs-lookup"><span data-stu-id="53b0a-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="53b0a-106">Pokud je vyhodnocen jako první argument `Nothing`, vyhodnotí a vrátí druhý argument.</span><span class="sxs-lookup"><span data-stu-id="53b0a-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="53b0a-107">Například následující kód obsahuje dva `If` výrazy, jeden s tři argumenty a druhý se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="53b0a-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="53b0a-108">Výrazy vypočítat a vrátit se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="53b0a-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="53b0a-109">Tato chyba je způsobena těchto výrazů:</span><span class="sxs-lookup"><span data-stu-id="53b0a-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="53b0a-110">**ID chyby:** BC33107</span><span class="sxs-lookup"><span data-stu-id="53b0a-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="53b0a-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="53b0a-111">To correct this error</span></span>  
  
- <span data-ttu-id="53b0a-112">Pokud kód nelze změnit tak, aby první argument je typ připouštějící hodnotu null nebo typ odkazu, zvažte převedení na tři argumenty `If` výrazu, nebo `If...Then...Else` příkazu.</span><span class="sxs-lookup"><span data-stu-id="53b0a-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="53b0a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53b0a-113">See also</span></span>

- [<span data-ttu-id="53b0a-114">Operátor If</span><span class="sxs-lookup"><span data-stu-id="53b0a-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="53b0a-115">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="53b0a-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="53b0a-116">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="53b0a-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
