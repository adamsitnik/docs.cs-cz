---
title: Typy chyb (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831563"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="7626d-102">Typy chyb (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7626d-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="7626d-103">V jazyce Visual Basic, chyby (také nazývané *výjimky*) spadají do jedné ze tří kategorií: chyby syntaxe, chyby za běhu a chyby logiky.</span><span class="sxs-lookup"><span data-stu-id="7626d-103">In Visual Basic, errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="7626d-104">Chyby syntaxe</span><span class="sxs-lookup"><span data-stu-id="7626d-104">Syntax Errors</span></span>  
 <span data-ttu-id="7626d-105">*Chyby syntaxe* jsou ty, které se zobrazí při psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="7626d-105">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="7626d-106">Visual Basic zkontroluje váš kód během psaní v **Editor kódu** okno a upozorní vás, pokud uděláte chybu, jako je například Chyba v pravopisu slova nebo nesprávně pomocí prvku jazyka.</span><span class="sxs-lookup"><span data-stu-id="7626d-106">Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="7626d-107">Chyby syntaxe jsou nejběžnějším typem chyby.</span><span class="sxs-lookup"><span data-stu-id="7626d-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="7626d-108">Je lze opravit snadno v kódování prostředí Jakmile k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="7626d-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7626d-109">`Option Explicit` Příkaz je jeden způsob jak se vyhnout chyby syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7626d-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="7626d-110">Vynutí předem deklarovat všechny proměnné, který se má použít v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7626d-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="7626d-111">Proto při těchto proměnných se používá v kódu, jsou zachyceny okamžitě typografické chyby a lze napravit.</span><span class="sxs-lookup"><span data-stu-id="7626d-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="7626d-112">Chyby za běhu</span><span class="sxs-lookup"><span data-stu-id="7626d-112">Run-Time Errors</span></span>  
 <span data-ttu-id="7626d-113">*Chyby za běhu* jsou ty, které se zobrazí pouze po kompilaci a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="7626d-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="7626d-114">To zahrnuje kód, který se zdá být správná, nemá žádné chyby syntaxe, ale nelze jej provést.</span><span class="sxs-lookup"><span data-stu-id="7626d-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="7626d-115">Například můžete například napsat správně psát kód pro otevření souboru.</span><span class="sxs-lookup"><span data-stu-id="7626d-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="7626d-116">Pokud soubor je poškozený, aplikace nelze provést, ale `Open` funkce a zastaví se.</span><span class="sxs-lookup"><span data-stu-id="7626d-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="7626d-117">Většina chyb za běhu můžete vyřešit přepsání chybného kódu zkompilováním a spuštěním.</span><span class="sxs-lookup"><span data-stu-id="7626d-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="7626d-118">Logické chyby</span><span class="sxs-lookup"><span data-stu-id="7626d-118">Logic Errors</span></span>  
 <span data-ttu-id="7626d-119">*Logické chyby* jsou ty, které se zobrazí, až se aplikace nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7626d-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="7626d-120">Jsou to většina často nežádoucí nebo neočekávané výsledky v reakci na akce uživatele.</span><span class="sxs-lookup"><span data-stu-id="7626d-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="7626d-121">Chybným zadáním klíče nebo jiných mimo vliv například může způsobit, že aplikace přestane fungovat během očekávané parametry, nebo úplně se vynechá.</span><span class="sxs-lookup"><span data-stu-id="7626d-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="7626d-122">Logické chyby jsou obvykle nejtěžší typ k vyřešení, protože není vždy jasné kde pocházejí.</span><span class="sxs-lookup"><span data-stu-id="7626d-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7626d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7626d-123">See also</span></span>

- [<span data-ttu-id="7626d-124">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="7626d-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="7626d-125">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="7626d-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
