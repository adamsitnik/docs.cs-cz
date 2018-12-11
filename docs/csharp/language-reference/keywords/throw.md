---
title: throw – C# odkaz
ms.custom: seodec18
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f9729a3536a6611ed593f16ba3bc09e7af20a4c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238816"
---
# <a name="throw-c-reference"></a><span data-ttu-id="5a8dd-102">throw (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5a8dd-102">throw (C# Reference)</span></span>

<span data-ttu-id="5a8dd-103">Signály výskyt výjimku při provádění programu.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a8dd-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a8dd-104">Remarks</span></span>

<span data-ttu-id="5a8dd-105">Syntaxe `throw` je:</span><span class="sxs-lookup"><span data-stu-id="5a8dd-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```

<span data-ttu-id="5a8dd-106">kde `e` je instancí třídy odvozené od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a8dd-107">V následujícím příkladu `throw` příkaz throw <xref:System.IndexOutOfRangeException> Pokud argument předaný do metodu s názvem `GetNumber` neodpovídá platný index interní pole.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="5a8dd-108">Pak pomocí metody volající `try-catch` nebo `try-catch-finally` bloku zpracovat vyvolanou výjimku.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="5a8dd-109">V následujícím příkladu zpracovává výjimky vyvolané `GetNumber` metody.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="5a8dd-110">Opětovné vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="5a8dd-110">Re-throwing an exception</span></span>

<span data-ttu-id="5a8dd-111">`throw` Můžete také použít v `catch` pro opětovné vyvolání výjimky zpracovávány v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="5a8dd-112">V takovém případě `throw` nepřijímá operand výjimky.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="5a8dd-113">To je nejužitečnější, když metoda předává na argument z volající do některé jiné metody knihovny a knihovny metoda vyvolá výjimku, která musí být předán volajícímu.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="5a8dd-114">Například v následujícím příkladu je znovu vyvolá <xref:System.NullReferenceException> , která je vyvolána při pokusu o načtení první znak neinicializovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="5a8dd-115">Můžete také použít `throw e` syntaxe v poznámce `catch` bloku pro vytvoření instance novou výjimku, můžete předat volajícího.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="5a8dd-116">V takovém případě původní výjimky, trasování zásobníku, což je k dispozici <xref:System.Exception.StackTrace> vlastností, nejsou uchována.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="5a8dd-117">`throw` Výraz</span><span class="sxs-lookup"><span data-stu-id="5a8dd-117">The `throw` expression</span></span>

<span data-ttu-id="5a8dd-118">Od verze C# 7.0, `throw` lze použít jako výraz, stejně jako příkaz.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="5a8dd-119">To umožňuje výjimka vyvolána v kontextech, které byly dříve nepodporovaný.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="5a8dd-120">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="5a8dd-120">These include:</span></span>

- <span data-ttu-id="5a8dd-121">[podmiňovací operátor](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5a8dd-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="5a8dd-122">Následující příklad používá `throw` výraz throw <xref:System.ArgumentException> metodu je předán prázdný řetězec pole.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="5a8dd-123">Před C# 7.0, by bylo potřeba joinkind tuto logiku `if` / `else` příkazu.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="5a8dd-124">[operátoru nulového sjednocení](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5a8dd-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="5a8dd-125">V následujícím příkladu `throw` použit výraz pomocí operátoru nulového sjednocení vyvolá výjimku, pokud se přiřadí řetězec `Name` vlastnost `null`.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- <span data-ttu-id="5a8dd-126">s výrazem v těle [lambda](../../lambda-expressions.md) nebo metody.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="5a8dd-127">Následující příklad ukazuje metodu s výrazem v těle, která se vyvolá <xref:System.InvalidCastException> protože převod na <xref:System.DateTime> hodnota není podporována.</span><span class="sxs-lookup"><span data-stu-id="5a8dd-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="5a8dd-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a8dd-128">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a8dd-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a8dd-129">See also</span></span>

- [<span data-ttu-id="5a8dd-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a8dd-130">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="5a8dd-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5a8dd-131">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="5a8dd-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="5a8dd-132">try-catch</span></span>](try-catch.md)  
- [<span data-ttu-id="5a8dd-133">Try, catch a throw – příkazy v jazyce C++</span><span class="sxs-lookup"><span data-stu-id="5a8dd-133">The try, catch, and throw Statements in C++</span></span>](try-catch.md)  
- [<span data-ttu-id="5a8dd-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a8dd-134">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="5a8dd-135">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="5a8dd-135">Exception Handling Statements</span></span>](exception-handling-statements.md)  
- [<span data-ttu-id="5a8dd-136">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="5a8dd-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)