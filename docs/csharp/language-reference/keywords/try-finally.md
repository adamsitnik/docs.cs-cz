---
title: try-finally – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 15111a185f73f60e77139d3a7faef7f32f4bf613
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677664"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="8643a-102">try-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8643a-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="8643a-103">Pomocí `finally` blok, můžete vyčistit všechny prostředky, které jsou přiděleny v [zkuste](try-catch.md) blok a kód můžete spustit i v případě, že dojde k výjimce v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="8643a-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="8643a-104">Obvykle, prohlášení o `finally` blok spustit, jakmile opustí ovládací prvek `try` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8643a-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="8643a-105">Přenos řízení může nastat v důsledku normálního provedení, provedení `break`, `continue`, `goto`, nebo `return` příkazu, nebo šíření výjimky z `try` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8643a-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="8643a-106">V rámci zpracování výjimek, přidružené `finally` bloku je zaručen běh.</span><span class="sxs-lookup"><span data-stu-id="8643a-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="8643a-107">Nicméně pokud není výjimka ošetřena, provedení `finally` bloku je závislá na jak operace unwind výjimek se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="8643a-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="8643a-108">Která je dále závislé na nastavení v počítači.</span><span class="sxs-lookup"><span data-stu-id="8643a-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="8643a-109">Obvykle po neošetřené výjimce ukončení aplikaci, která určuje, jestli `finally` spustit blok není důležité.</span><span class="sxs-lookup"><span data-stu-id="8643a-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="8643a-110">Však máte příkazy v `finally` blok, který musí být spuštěn i v této situaci, jedním řešením je přidat `catch` bloku `try` - `finally` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8643a-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="8643a-111">Alternativně můžete zachytit výjimku, která by mohla být vyvolána v `try` bloku `try` - `finally` výše v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="8643a-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="8643a-112">To znamená, můžete zachytit výjimku v metodě, která volá metodu, která obsahuje `try` - `finally` příkazu, nebo v metodě, která volá tuto metodu, nebo v jakékoli metodě v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="8643a-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="8643a-113">Pokud není výjimka zachycena, provádění `finally` bloku závisí na tom, jestli operační systém zvolí pro spuštění výjimky operaci unwind.</span><span class="sxs-lookup"><span data-stu-id="8643a-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="8643a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="8643a-114">Example</span></span>

<span data-ttu-id="8643a-115">V následujícím příkladu způsobuje neplatný výraz převodu `System.InvalidCastException` výjimky.</span><span class="sxs-lookup"><span data-stu-id="8643a-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="8643a-116">Výjimka neošetřená.</span><span class="sxs-lookup"><span data-stu-id="8643a-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="8643a-117">V následujícím příkladu, výjimka `TryCast` metoda je zachycena v metodě hlouběji v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="8643a-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="8643a-118">Další informace o `finally`, naleznete v tématu [konstrukce try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="8643a-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="8643a-119">C# obsahuje také [příkaz using](using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty pomocí pohodlné syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8643a-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8643a-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8643a-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8643a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8643a-121">See also</span></span>

- [<span data-ttu-id="8643a-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8643a-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8643a-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8643a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8643a-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8643a-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8643a-125">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="8643a-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="8643a-126">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="8643a-126">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="8643a-127">throw</span><span class="sxs-lookup"><span data-stu-id="8643a-127">throw</span></span>](throw.md)
- [<span data-ttu-id="8643a-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="8643a-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="8643a-129">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="8643a-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)