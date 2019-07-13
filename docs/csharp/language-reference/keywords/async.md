---
title: Async – C# odkaz
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 346cfccd076866e9c321974aaa8c8ddd367a17ea
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859579"
---
# <a name="async-c-reference"></a><span data-ttu-id="03168-102">async (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="03168-102">async (C# Reference)</span></span>
<span data-ttu-id="03168-103">Použití `async` modifikátor určit, že je metoda, [výraz lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), nebo [anonymní metoda](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="03168-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="03168-104">Pokud použijete tento modifikátor na metodu nebo výraz, to se označuje jako *asynchronní metoda*.</span><span class="sxs-lookup"><span data-stu-id="03168-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="03168-105">Následující příklad definuje asynchronní metodu s názvem `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="03168-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="03168-106">Pokud začínáte s asynchronním programováním nebo není srozumitelný použití asynchronní metody `await` – klíčové slovo provádět potenciálně dlouhotrvající práci bez blokování vlákna volajícího, přečtěte si úvod v kapitole [Asynchronous Programming with Async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="03168-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="03168-107">Následující kód se nachází uvnitř a volá asynchronní metodu <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="03168-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="03168-108">Asynchronní metoda pracuje synchronně, dokud nedosáhne svého prvního `await` výrazu, v tomto okamžiku je metoda pozastavena, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="03168-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="03168-109">Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.</span><span class="sxs-lookup"><span data-stu-id="03168-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="03168-110">Pokud metoda, která `async` upraví – klíčové slovo neobsahuje `await` výraz nebo příkaz, metoda je provedena synchronně.</span><span class="sxs-lookup"><span data-stu-id="03168-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="03168-111">Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují slovo `await` příkazy, protože tato situace může značit chybu.</span><span class="sxs-lookup"><span data-stu-id="03168-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="03168-112">Zobrazit [upozornění kompilátoru (úroveň 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="03168-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="03168-113">`async` – Klíčové slovo je kontextové, v tom, že je klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="03168-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="03168-114">Ve všech ostatních kontextech je interpretováno jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="03168-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03168-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="03168-115">Example</span></span>  
<span data-ttu-id="03168-116">Následující příklad ukazuje strukturu a tok řízení mezi asynchronním ovladačem událostí, `StartButton_Click`a asynchronní metody, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="03168-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="03168-117">Výsledkem asynchronní metody je počet znaků na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="03168-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="03168-118">Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikace Windows Store, který vytvoříte v sadě Visual Studio; Podívejte se v komentářích ke kódu pro nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="03168-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="03168-119">Tento kód lze spustit v sadě Visual Studio jako aplikace Windows Presentation Foundation (WPF) nebo aplikaci Windows Store.</span><span class="sxs-lookup"><span data-stu-id="03168-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="03168-120">Je třeba ovládacího prvku tlačítko s názvem `StartButton` a ovládacího prvku textového pole s názvem `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="03168-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="03168-121">Nezapomeňte nastavit názvy a obslužné rutiny, abyste měli vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="03168-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="03168-122">Chcete-li spustit kód jako aplikaci WPF:</span><span class="sxs-lookup"><span data-stu-id="03168-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="03168-123">Vložte tento kód do `MainWindow` třídy v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="03168-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="03168-124">Přidejte odkaz na System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="03168-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="03168-125">Přidat `using` směrnice pro System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="03168-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="03168-126">Chcete-li spustit kód jako aplikaci Windows Store:</span><span class="sxs-lookup"><span data-stu-id="03168-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="03168-127">Vložte tento kód do `MainPage` třídy v MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="03168-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="03168-128">Přidání direktivy using pro System.Net.Http a System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="03168-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="03168-129">Další informace o úkolech a kódu, který se spustí při čekání na úlohy, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="03168-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="03168-130">Úplný příklad WPF používající podobné prvky, naleznete v tématu [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="03168-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="03168-131">Návratové typy</span><span class="sxs-lookup"><span data-stu-id="03168-131">Return Types</span></span>  
<span data-ttu-id="03168-132">Asynchronní metoda může mít tyto návratové typy:</span><span class="sxs-lookup"><span data-stu-id="03168-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="03168-133">[void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="03168-133">[void](../../../csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="03168-134">`async void` metody se obecně nedoporučují pro kód než obslužné rutiny událostí, protože volající nemůže `await` tyto metody a musí implementovat mechanismus různé zprávy o úspěšném dokončení nebo chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="03168-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="03168-135">Od verze C# 7.0, libovolný typ, který má k dispozici přístup `GetAwaiter` metody.</span><span class="sxs-lookup"><span data-stu-id="03168-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="03168-136">`System.Threading.Tasks.ValueTask<TResult>` Typ je jeden takový implementace.</span><span class="sxs-lookup"><span data-stu-id="03168-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="03168-137">Je k dispozici přidáním balíčku NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="03168-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="03168-138">Asynchronní metoda nemůže deklarovat všechny [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ani použít ji [odkazovat na návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody které mají tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="03168-138">The async method can't declare any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="03168-139">Zadáte `Task<TResult>` jako návratový typ asynchronní metody Pokud [vrátit](../../../csharp/language-reference/keywords/return.md) příkaz metody určuje operand typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="03168-139">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="03168-140">Použijete `Task` Pokud není vrácena žádná smysluplná hodnota po dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="03168-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="03168-141">To znamená, volání metody vrací `Task`, ale když `Task` dokončení jakékoli `await` výraz, který čeká na `Task` vyhodnotí jako `void`.</span><span class="sxs-lookup"><span data-stu-id="03168-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="03168-142">Můžete použít `void` především k definování obslužných rutin událostí, kde je požadován návratový typ.</span><span class="sxs-lookup"><span data-stu-id="03168-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="03168-143">Volající `void`-asynchronní metody vracející ni nemohou čekat a zaznamenat tak výjimky, které metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="03168-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="03168-144">Počínaje C# 7.0, vrátí jiný typ, obvykle hodnota typu, který má `GetAwaiter` metoda minimalizovat přidělení paměti v kritickém pro výkon části kódu.</span><span class="sxs-lookup"><span data-stu-id="03168-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="03168-145">Další informace a příklady najdete v tématu [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="03168-145">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03168-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03168-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="03168-147">await</span><span class="sxs-lookup"><span data-stu-id="03168-147">await</span></span>](../../../csharp/language-reference/keywords/await.md)
- [<span data-ttu-id="03168-148">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="03168-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="03168-149">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="03168-149">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
