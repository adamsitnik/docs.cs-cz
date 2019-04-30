---
title: 'Výjimky: Try... with – výraz'
description: Další informace o použití F# "try... with" výraz pro zpracování výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: 742e0b595525c69b83a55682c3c8b9b650326ac7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945532"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="cfdf4-103">Výjimky: Try... with – výraz</span><span class="sxs-lookup"><span data-stu-id="cfdf4-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="cfdf4-104">Toto téma popisuje `try...with` výraz, výraz, který se používá pro zpracování výjimek v F# jazyka.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="cfdf4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfdf4-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="cfdf4-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfdf4-106">Remarks</span></span>

<span data-ttu-id="cfdf4-107">`try...with` Výraz je použit pro zpracování výjimek v F#.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="cfdf4-108">Se podobá `try...catch` příkaz v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="cfdf4-109">V předchozí syntaxi, kód v *expression1* může vygenerovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="cfdf4-110">`try...with` Výraz vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="cfdf4-111">Pokud není vyvolána žádná výjimka, celý výraz vrátí hodnotu *expression1*.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="cfdf4-112">Pokud je vyvolána výjimka, každý *vzor* je pak porovnána s výjimkou a pro první odpovídající vzor odpovídající *výraz*, označované jako *obslužnérutinyvýjimek*, je proveden tuto větev a celkové výraz vrací hodnotu výrazu v této obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="cfdf4-113">Pokud žádný vzor odpovídá, výjimka šíří výše v zásobníku volání, dokud není nalezena odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="cfdf4-114">Typy hodnot vrácených z každého výrazu v obslužných rutinách výjimek musí shodovat s typem vrácená z výrazu v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="cfdf4-115">Fakt, že došlo k chybě také často, znamená, že neexistuje platná hodnota vrácená z výrazů v každé obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="cfdf4-116">Časté je typu výrazu možné typ možnosti.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="cfdf4-117">Následující příklad kódu ukazuje tento model.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="cfdf4-118">Výjimky mohou být výjimky .NET, nebo může být F# výjimky.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="cfdf4-119">Můžete definovat F# výjimky pomocí `exception` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="cfdf4-120">Různé vzorce můžete použít k filtrování podle typu výjimky a dalších podmínek; Možnosti jsou shrnuty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="cfdf4-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="cfdf4-121">Pattern</span></span>|<span data-ttu-id="cfdf4-122">Popis</span><span class="sxs-lookup"><span data-stu-id="cfdf4-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="cfdf4-123">:?</span><span class="sxs-lookup"><span data-stu-id="cfdf4-123">:?</span></span> <span data-ttu-id="cfdf4-124">*exception-type*</span><span class="sxs-lookup"><span data-stu-id="cfdf4-124">*exception-type*</span></span>|<span data-ttu-id="cfdf4-125">Neodpovídá zadanému typu výjimky .NET.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="cfdf4-126">:?</span><span class="sxs-lookup"><span data-stu-id="cfdf4-126">:?</span></span> <span data-ttu-id="cfdf4-127">*Typ výjimky* jako *identifikátor*</span><span class="sxs-lookup"><span data-stu-id="cfdf4-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="cfdf4-128">Neodpovídá zadanému typu výjimky .NET, ale dává výjimku pojmenovaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="cfdf4-129">*exception-name*(*arguments*)</span><span class="sxs-lookup"><span data-stu-id="cfdf4-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="cfdf4-130">Shody F# typ výjimky a vytvoří vazbu argumenty.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="cfdf4-131">*identifier*</span><span class="sxs-lookup"><span data-stu-id="cfdf4-131">*identifier*</span></span>|<span data-ttu-id="cfdf4-132">Odpovídá jakékoli výjimce a sváže s názvem objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="cfdf4-133">Ekvivalentní **:? System.Exception jako**_identifikátor_</span><span class="sxs-lookup"><span data-stu-id="cfdf4-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="cfdf4-134">*identifikátor* při *podmínku*</span><span class="sxs-lookup"><span data-stu-id="cfdf4-134">*identifier* when *condition*</span></span>|<span data-ttu-id="cfdf4-135">Odpovídá jakoukoliv výjimku, pokud je podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="cfdf4-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="cfdf4-136">Examples</span></span>

<span data-ttu-id="cfdf4-137">Následující příklady ilustrují použití různých vzorů obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="cfdf4-138">`try...with` Konstruktor je zvláštní výraz z `try...finally` výrazu.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="cfdf4-139">Proto pokud váš kód vyžaduje obě `with` bloku a `finally` bloku, budete muset vnořit dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="cfdf4-140">Můžete použít `try...with` v asynchronních pracovních postupech a jiných výrazech výpočtu, ve kterém malá a velká přizpůsobenou verzi `try...with` výraz je použit.</span><span class="sxs-lookup"><span data-stu-id="cfdf4-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="cfdf4-141">Další informace najdete v tématu [asynchronní pracovní postupy](../asynchronous-workflows.md), a [výrazech výpočtu](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="cfdf4-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfdf4-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfdf4-142">See also</span></span>

- [<span data-ttu-id="cfdf4-143">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="cfdf4-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="cfdf4-144">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="cfdf4-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="cfdf4-145">Výjimky: `try...finally` Výraz</span><span class="sxs-lookup"><span data-stu-id="cfdf4-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)