---
title: Anonymní metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: d7823611df5e02040fd8735e1fa6ea7841298836
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595052"
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="40bcb-102">Anonymní metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="40bcb-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="40bcb-103">Ve verzích jazyka C# před 2.0, je možné deklarovat jedině [delegovat](../../../csharp/language-reference/keywords/delegate.md) pomocí [s názvem metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="40bcb-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="40bcb-104">2.0 C# zavedl anonymní metody a v C# 3.0 nebo novější, výrazy lambda jako upřednostňovaný způsob, jak napsat kód vloženého mají přednost před anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="40bcb-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="40bcb-105">Ale informace o anonymní metody v tomto tématu platí taky pro výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="40bcb-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="40bcb-106">Existuje jeden případ, ve kterém anonymní metoda poskytuje funkce, nebyl nalezen v lambda výrazech.</span><span class="sxs-lookup"><span data-stu-id="40bcb-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="40bcb-107">Anonymní metody umožňují vynechat seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="40bcb-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="40bcb-108">To znamená, že na delegáty s různými podpisy lze převést anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="40bcb-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="40bcb-109">To není možné s výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="40bcb-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="40bcb-110">Další informace konkrétně o výrazech lambda naleznete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="40bcb-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="40bcb-111">Vytvoření anonymní metody je v podstatě způsob, jak předat bloku kódu jako parametr delegátu.</span><span class="sxs-lookup"><span data-stu-id="40bcb-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="40bcb-112">Tady jsou dva příklady:</span><span class="sxs-lookup"><span data-stu-id="40bcb-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 <span data-ttu-id="40bcb-113">S použitím anonymní metody, snížit režii kódování v vytvoření instance delegátů, protože není nutné vytvářet samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="40bcb-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="40bcb-114">Například zadání bloku kódu namísto delegát může být užitečné v situaci, pokud by bylo nutné vytvořit metodu zdát, že zbytečnou režii.</span><span class="sxs-lookup"><span data-stu-id="40bcb-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="40bcb-115">Dobrým příkladem může být při spuštění nového vlákna.</span><span class="sxs-lookup"><span data-stu-id="40bcb-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="40bcb-116">Tato třída vytvoří vlákno a také obsahuje kód, který se vlákna spustí bez vytváření další metoda pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="40bcb-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a><span data-ttu-id="40bcb-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40bcb-117">Remarks</span></span>  
 <span data-ttu-id="40bcb-118">Rozsah parametry anonymní metodu *anonymní metoda bloku*.</span><span class="sxs-lookup"><span data-stu-id="40bcb-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="40bcb-119">Jedná se o chybu, jako mít příkaz skoku [goto](../../../csharp/language-reference/keywords/goto.md), [přerušení](../../../csharp/language-reference/keywords/break.md), nebo [pokračovat](../../../csharp/language-reference/keywords/continue.md), uvnitř blok anonymní metody, pokud je cílem mimo blok.</span><span class="sxs-lookup"><span data-stu-id="40bcb-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="40bcb-120">Je také chybou mít příkaz skoku, jako například `goto`, `break`, nebo `continue`, mimo blok anonymní metody, pokud je cíl uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="40bcb-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="40bcb-121">Místní proměnné a parametry, jejichž rozsah obsahuje deklaraci anonymní metody jsou volány *vnější* proměnné anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="40bcb-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="40bcb-122">Například v následující segment kódu `n` je vnější proměnné:</span><span class="sxs-lookup"><span data-stu-id="40bcb-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 <span data-ttu-id="40bcb-123">Odkaz na proměnnou vnějšího `n` je označen jako *zachycené* při vytvoření delegáta.</span><span class="sxs-lookup"><span data-stu-id="40bcb-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="40bcb-124">Na rozdíl od místních proměnných dobu života zachycené proměnné rozšiřuje dokud delegáty, které odkazují na anonymní metody, které jsou způsobilé pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40bcb-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="40bcb-125">Nelze získat přístup k anonymní metodu [v](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry vnějším oboru.</span><span class="sxs-lookup"><span data-stu-id="40bcb-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="40bcb-126">Žádné nebezpečný kód může přistupovat v rámci *anonymní metoda bloku*.</span><span class="sxs-lookup"><span data-stu-id="40bcb-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="40bcb-127">Anonymní metody nejsou povoleny na levé straně [je](../../../csharp/language-reference/keywords/is.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="40bcb-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40bcb-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="40bcb-128">Example</span></span>  
 <span data-ttu-id="40bcb-129">Následující příklad ukazuje dva způsoby vytvoření instance delegáta:</span><span class="sxs-lookup"><span data-stu-id="40bcb-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
- <span data-ttu-id="40bcb-130">Přidružíte delegáta s anonymní metodou.</span><span class="sxs-lookup"><span data-stu-id="40bcb-130">Associating the delegate with an anonymous method.</span></span>  
  
- <span data-ttu-id="40bcb-131">Přidružení pojmenované metody delegáta (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="40bcb-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="40bcb-132">V obou případech se zobrazí zpráva, když je vyvolán delegát.</span><span class="sxs-lookup"><span data-stu-id="40bcb-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="40bcb-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40bcb-133">See also</span></span>

- [<span data-ttu-id="40bcb-134">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40bcb-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="40bcb-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="40bcb-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="40bcb-136">Delegáti</span><span class="sxs-lookup"><span data-stu-id="40bcb-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="40bcb-137">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="40bcb-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="40bcb-138">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="40bcb-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="40bcb-139">Metody</span><span class="sxs-lookup"><span data-stu-id="40bcb-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="40bcb-140">Delegáti s pojmenovanými vs. anonymními metodami</span><span class="sxs-lookup"><span data-stu-id="40bcb-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
