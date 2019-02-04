---
title: Delegáti - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 1c272dd9ab4f810a0eb1a1064b4c7731873d2c80
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675371"
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="6dd8c-102">Delegáti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6dd8c-102">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="6dd8c-103">A [delegovat](../../../csharp/language-reference/keywords/delegate.md) je typ, který představuje odkazy na metody se seznamem konkrétních parametrů a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="6dd8c-104">Pokud vytvoříte instanci delegátu, můžete příslušnou instanci přidružit s jakoukoli metodou s kompatibilním podpisem a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-104">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="6dd8c-105">Metodu můžete vyvolat (nebo volat) prostřednictvím instance delegátu.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-105">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="6dd8c-106">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-106">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="6dd8c-107">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-107">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="6dd8c-108">Můžete vytvořit vlastní metodu a konkrétní třída, jako je ovládací prvek Windows, může volat vaši metodu, pokud dojde k určité události.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-108">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="6dd8c-109">Následující příklad znázorňuje deklaraci delegátu.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-109">The following example shows a delegate declaration:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="6dd8c-110">Delegátu lze přiřadit jakoukoli metodu z jakékoli přístupné třídy nebo struktury odpovídající typu delegátu.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-110">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="6dd8c-111">Metoda může být buď statická, anebo se jedná o metodu instance.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-111">The method can be either static or an instance method.</span></span> <span data-ttu-id="6dd8c-112">Díky tomu je možné programově změnit volání metody a vložit nový kód do stávajících tříd.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-112">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6dd8c-113">V kontextu přetížení metody nezahrnuje podpis metody návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-113">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="6dd8c-114">V kontextu delegátů však podpis zahrnuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-114">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="6dd8c-115">Jinými slovy to znamená, že metoda musí mít stejný návratový typ jako delegát.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-115">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="6dd8c-116">Díky této možnosti odkazovat na metodu jako parametr jsou delegáty ideální pro definování metod zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-116">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="6dd8c-117">Například odkaz na metodu, která srovnává dva objekty, lze jako argument předat algoritmu řazení.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-117">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="6dd8c-118">Vzhledem k tomu, že srovnávací kód je součástí samostatné procedury, lze algoritmus řazení napsat obecnějším způsobem.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-118">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="6dd8c-119">Přehled delegátů</span><span class="sxs-lookup"><span data-stu-id="6dd8c-119">Delegates Overview</span></span>  
 <span data-ttu-id="6dd8c-120">Delegáty mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="6dd8c-120">Delegates have the following properties:</span></span>  
  
-   <span data-ttu-id="6dd8c-121">Delegáti jsou podobné na ukazatele funkcí jazyka C++, ale delegáti jsou plně objektově orientované a na rozdíl od C++ ukazatelů na členské funkce, delegáti zapouzdřit instance objektu a metody.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-121">Delegates are similar to C++ function pointers, but delegates are fully object-oriented, and unlike C++ pointers to member functions, delegates encapsulate both an object instance and a method.</span></span>
  
-   <span data-ttu-id="6dd8c-122">Delegáty umožňují předávání metod jako parametrů.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-122">Delegates allow methods to be passed as parameters.</span></span>  
  
-   <span data-ttu-id="6dd8c-123">Delegáty lze použít pro definování metod zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-123">Delegates can be used to define callback methods.</span></span>  
  
-   <span data-ttu-id="6dd8c-124">Delegáty lze zřetězit; například je možné volat větší počet metod v rámci jediné události.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-124">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
-   <span data-ttu-id="6dd8c-125">Metody nemusí přesně odpovídat typu delegátu.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-125">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="6dd8c-126">Další informace najdete v tématu [použití odchylky v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6dd8c-126">For more information, see [Using Variance in Delegates](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
-   <span data-ttu-id="6dd8c-127">C# verze 2.0 byl zaveden koncept [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), které umožňují bloky kódu mají být předány jako parametrů, namísto samostatně definované metody.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-127">C# version 2.0 introduced the concept of [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="6dd8c-128">Verze 3.0 jazyka C# představila výrazy lambda jako přesnější způsob psaní bloků vloženého kódu.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-128">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="6dd8c-129">Anonymní metody i výrazy lambda (v určitých kontextech) se kompilují na typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-129">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="6dd8c-130">Tyto funkce se souhrnně označují jako anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-130">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="6dd8c-131">Další informace o výrazech lambda naleznete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6dd8c-131">For more information about lambda expressions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6dd8c-132">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6dd8c-132">In This Section</span></span>  
  
-   [<span data-ttu-id="6dd8c-133">Použití delegátů</span><span class="sxs-lookup"><span data-stu-id="6dd8c-133">Using Delegates</span></span>](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   <span data-ttu-id="6dd8c-134">[Použití delegátů namísto rozhraní (C# Programming Guide)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6dd8c-134">[When to Use Delegates Instead of Interfaces (C# Programming Guide)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span></span>  
  
-   [<span data-ttu-id="6dd8c-135">Delegáti s pojmenovanými vs. anonymními metodami</span><span class="sxs-lookup"><span data-stu-id="6dd8c-135">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [<span data-ttu-id="6dd8c-136">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="6dd8c-136">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [<span data-ttu-id="6dd8c-137">Použití odchylek v delegátech</span><span class="sxs-lookup"><span data-stu-id="6dd8c-137">Using Variance in Delegates</span></span>](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [<span data-ttu-id="6dd8c-138">Postupy: Kombinování delegátů (vícesměroví delegáti)</span><span class="sxs-lookup"><span data-stu-id="6dd8c-138">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [<span data-ttu-id="6dd8c-139">Postupy: Deklarování, vytváření instancí a použití delegáta</span><span class="sxs-lookup"><span data-stu-id="6dd8c-139">How to: Declare, Instantiate, and Use a Delegate</span></span>](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
  
## <a name="c-language-specification"></a><span data-ttu-id="6dd8c-140">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6dd8c-140">C# Language Specification</span></span>  

<span data-ttu-id="6dd8c-141">Další informace najdete v tématu [delegáti](~/_csharplang/spec/delegates.md) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6dd8c-141">For more information, see [Delegates](~/_csharplang/spec/delegates.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="6dd8c-142">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6dd8c-142">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="6dd8c-143">Doporučené kapitoly knihy</span><span class="sxs-lookup"><span data-stu-id="6dd8c-143">Featured Book Chapters</span></span>  
 <span data-ttu-id="6dd8c-144">[Delegáty, události a výrazy Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3.0 Cookbook, Third Edition: Víc než 250 řešení pro C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="6dd8c-144">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="6dd8c-145">[Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) v [učení C# 3.0: Hlavní základní informace o C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="6dd8c-145">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd8c-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6dd8c-146">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="6dd8c-147">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6dd8c-147">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6dd8c-148">Události</span><span class="sxs-lookup"><span data-stu-id="6dd8c-148">Events</span></span>](../../../csharp/programming-guide/events/index.md)
