---
title: Return – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 7f8ec0456576133d37dd19b5c0f8878a7ac57dab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831720"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="ec973-102">Return – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec973-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="ec973-103">Vrátí ovládací prvek kódu, který volá `Function`, `Sub`, `Get`, `Set`, nebo `Operator` postup.</span><span class="sxs-lookup"><span data-stu-id="ec973-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec973-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec973-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="ec973-105">Část</span><span class="sxs-lookup"><span data-stu-id="ec973-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="ec973-106">Vyžaduje `Function`, `Get`, nebo `Operator` postup.</span><span class="sxs-lookup"><span data-stu-id="ec973-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="ec973-107">Výraz, který představuje hodnotu, která má být vrácen volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="ec973-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec973-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec973-108">Remarks</span></span>  
 <span data-ttu-id="ec973-109">V `Sub` nebo `Set` postupu `Return` příkaz je ekvivalentní `Exit Sub` nebo `Exit Property` příkaz, a `expression` nesmí být zadaný.</span><span class="sxs-lookup"><span data-stu-id="ec973-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="ec973-110">V `Function`, `Get`, nebo `Operator` postupu `Return` musí obsahovat příkaz `expression`, a `expression` se musí vyhodnotit na datový typ, který lze převést na typ vrácené hodnoty procedury.</span><span class="sxs-lookup"><span data-stu-id="ec973-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="ec973-111">V `Function` nebo `Get` postup, budete mít taky alternativní přiřazení výraz pro název procedury, která bude sloužit jako návratovou hodnotu a potom provádění `Exit Function` nebo `Exit Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="ec973-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="ec973-112">V `Operator` postup, musíte použít `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="ec973-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="ec973-113">Můžete vytvořit tolik `Return` příkazy podle potřeby ve stejné proceduře.</span><span class="sxs-lookup"><span data-stu-id="ec973-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec973-114">Kód v `Finally` blok se spustí po `Return` příkaz v `Try` nebo `Catch` blok je došlo k chybě, ale před tímto `Return` spuštění příkazů.</span><span class="sxs-lookup"><span data-stu-id="ec973-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="ec973-115">A `Return` nemůže být součástí příkazu `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="ec973-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec973-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec973-116">Example</span></span>  
 <span data-ttu-id="ec973-117">V následujícím příkladu `Return` příkaz několikrát k vrácení volajícímu kódu, když není potřeba dělat nic dalšího postupu.</span><span class="sxs-lookup"><span data-stu-id="ec973-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="ec973-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec973-118">See also</span></span>

- [<span data-ttu-id="ec973-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="ec973-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ec973-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="ec973-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ec973-121">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="ec973-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="ec973-122">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="ec973-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="ec973-123">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="ec973-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="ec973-124">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="ec973-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="ec973-125">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="ec973-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="ec973-126">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="ec973-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
