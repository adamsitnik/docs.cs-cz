---
title: Kontrakty kódu
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e40f93be7f2dad4a80a4f4d23f61f3c93061751
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874936"
---
# <a name="code-contracts"></a><span data-ttu-id="79020-102">Kontrakty kódu</span><span class="sxs-lookup"><span data-stu-id="79020-102">Code Contracts</span></span>

<span data-ttu-id="79020-103">Kontrakty kódu poskytují způsob, jak určit předpoklady, vstupních a výstupních objekt podmínek ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="79020-103">Code contracts provide a way to specify preconditions, postconditions, and object invariants in your code.</span></span> <span data-ttu-id="79020-104">Předběžné podmínky jsou požadavky, které musí být splněny, při zadávání metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="79020-104">Preconditions are requirements that must be met when entering a method or property.</span></span> <span data-ttu-id="79020-105">Vstupních popisují očekávání v době, kdy kód metody nebo vlastnosti se ukončí.</span><span class="sxs-lookup"><span data-stu-id="79020-105">Postconditions describe expectations at the time the method or property code exits.</span></span> <span data-ttu-id="79020-106">Objekt výstupních podmínek popisují očekávaný stav pro třídu, která je v dobrém stavu.</span><span class="sxs-lookup"><span data-stu-id="79020-106">Object invariants describe the expected state for a class that is in a good state.</span></span>

<span data-ttu-id="79020-107">Kontrakty kódu zahrnují třídy pro označení kódu, statické analyzátor pro analýzu v době kompilace a modulu runtime analyzátor.</span><span class="sxs-lookup"><span data-stu-id="79020-107">Code contracts include classes for marking your code, a static analyzer for compile-time analysis, and a runtime analyzer.</span></span> <span data-ttu-id="79020-108">Třídy pro kontrakty kódu najdete v <xref:System.Diagnostics.Contracts> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="79020-108">The classes for code contracts can be found in the <xref:System.Diagnostics.Contracts> namespace.</span></span>

<span data-ttu-id="79020-109">Kontrakty kódu mezi výhody patří následující:</span><span class="sxs-lookup"><span data-stu-id="79020-109">The benefits of code contracts include the following:</span></span>

- <span data-ttu-id="79020-110">Vylepšené testování: Kontrakty kódu poskytovat statické ověření kontraktu, kontrola modulu runtime a generování dokumentace.</span><span class="sxs-lookup"><span data-stu-id="79020-110">Improved testing: Code contracts provide static contract verification, runtime checking, and documentation generation.</span></span>

- <span data-ttu-id="79020-111">Nástroje pro automatické testování: Kontrakty kódu můžete použít ke generování lépe vystihuje testování částí filtrováním význam testu argumenty, které nesplňují podmínky.</span><span class="sxs-lookup"><span data-stu-id="79020-111">Automatic testing tools: You can use code contracts to generate more meaningful unit tests by filtering out meaningless test arguments that do not satisfy preconditions.</span></span>

- <span data-ttu-id="79020-112">Statické ověření: Statické požadovaných součástí se můžete rozhodnout, jestli se porušení smlouvy bez spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="79020-112">Static verification: The static checker can decide whether there are any contract violations without running the program.</span></span> <span data-ttu-id="79020-113">Zkontroluje pro implicitní smlouvy, jako je například null přístupů přes ukazatel a pole hranice a explicitní smluv.</span><span class="sxs-lookup"><span data-stu-id="79020-113">It checks for implicit contracts, such as null dereferences and array bounds, and explicit contracts.</span></span>

- <span data-ttu-id="79020-114">Referenční dokumentace: Dokumentace ke službě generátor argumentech existující soubory dokumentace XML s informacemi o smlouvě.</span><span class="sxs-lookup"><span data-stu-id="79020-114">Reference documentation: The documentation generator augments existing XML documentation files with contract information.</span></span> <span data-ttu-id="79020-115">Existují také šablony stylů, které lze použít s [Sandcastle](https://github.com/EWSoftware/SHFB) tak, aby stránky dokumentace generovaného kontraktu oddíly.</span><span class="sxs-lookup"><span data-stu-id="79020-115">There are also style sheets that can be used with [Sandcastle](https://github.com/EWSoftware/SHFB) so that the generated documentation pages have contract sections.</span></span>

<span data-ttu-id="79020-116">Všechny jazyky rozhraní .NET Framework mohou okamžitě využívat smluv; nemusíte psát speciální analyzátoru nebo kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="79020-116">All .NET Framework languages can immediately take advantage of contracts; you do not have to write a special parser or compiler.</span></span> <span data-ttu-id="79020-117">Doplněk sady Visual Studio vám umožní určit úroveň smlouvy analýzy kódu mají být provedeny.</span><span class="sxs-lookup"><span data-stu-id="79020-117">A Visual Studio add-in lets you specify the level of code contract analysis to be performed.</span></span> <span data-ttu-id="79020-118">Analyzátory můžou ověřte, zda smlouvách ve správném formátu (kontrolu typu a překlad názvů) a může vytvářet kompilovaný formy smluv ve formátu Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="79020-118">The analyzers can confirm that the contracts are well-formed (type checking and name resolution) and can produce a compiled form of the contracts in Microsoft intermediate language (MSIL) format.</span></span> <span data-ttu-id="79020-119">Vytváření kontraktů v sadě Visual Studio vám umožní využít standardní informace IntelliSense poskytované nástrojem.</span><span class="sxs-lookup"><span data-stu-id="79020-119">Authoring contracts in Visual Studio lets you take advantage of the standard IntelliSense provided by the tool.</span></span>

<span data-ttu-id="79020-120">Většina metod ve třídě smlouvy jsou podmíněně kompilována; To znamená, kompilátor vydává volání těchto metod pouze v případě, že definujete pomocí speciální symbol CONTRACTS_FULL, `#define` směrnice.</span><span class="sxs-lookup"><span data-stu-id="79020-120">Most methods in the contract class are conditionally compiled; that is, the compiler emits calls to these methods only when  you define a special symbol, CONTRACTS_FULL, by using the `#define` directive.</span></span> <span data-ttu-id="79020-121">CONTRACTS_FULL umožňuje zapisovat smlouvy v kódu bez použití `#ifdef` direktivy; můžete vytvářet různé verze, některé u kontraktů a některé bez.</span><span class="sxs-lookup"><span data-stu-id="79020-121">CONTRACTS_FULL lets you write contracts in your code without using `#ifdef` directives; you can produce different builds, some with contracts, and some without.</span></span>

<span data-ttu-id="79020-122">Nástroje a podrobné pokyny k používání kontrakty kódu najdete v tématu [kontrakty kódu](https://go.microsoft.com/fwlink/?LinkId=152461) na webu MSDN devlabs s názvem.</span><span class="sxs-lookup"><span data-stu-id="79020-122">For tools and detailed instructions for using code contracts, see [Code Contracts](https://go.microsoft.com/fwlink/?LinkId=152461) on the MSDN DevLabs Web site.</span></span>

## <a name="preconditions"></a><span data-ttu-id="79020-123">Předběžné podmínky</span><span class="sxs-lookup"><span data-stu-id="79020-123">Preconditions</span></span>

<span data-ttu-id="79020-124">Předběžné podmínky můžete vyjádřit pomocí <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79020-124">You can express preconditions by using the <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79020-125">Předběžné podmínky určete stav při vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="79020-125">Preconditions specify state when a method is invoked.</span></span> <span data-ttu-id="79020-126">Obvykle se používají k určení platné hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="79020-126">They are generally used to specify valid parameter values.</span></span> <span data-ttu-id="79020-127">Všechny členy, které jsou uvedené v předběžných podmínkách musí být přinejmenším stejně dostupná jako metodu. v opačném případě nemusí být předpoklad srozumitelné všichni volající metody.</span><span class="sxs-lookup"><span data-stu-id="79020-127">All members that are mentioned in preconditions must be at least as accessible as the method itself; otherwise, the precondition might not be understood by all callers of a method.</span></span> <span data-ttu-id="79020-128">Podmínka musí mít žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="79020-128">The condition must have no side-effects.</span></span> <span data-ttu-id="79020-129">Analyzátor modul runtime určuje chování za běhu selhání předběžné podmínky.</span><span class="sxs-lookup"><span data-stu-id="79020-129">The run-time behavior of failed preconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="79020-130">Například následující předpoklad vyjadřuje tento parametr `x` musí mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="79020-130">For example, the following precondition expresses that parameter `x` must be non-null.</span></span>

```csharp
Contract.Requires(x != null);
```

<span data-ttu-id="79020-131">Pokud váš kód musí vyvolat zvláštní výjimku při selhání předběžné podmínky, můžete použít obecné přetížení <xref:System.Diagnostics.Contracts.Contract.Requires%2A> následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="79020-131">If your code must throw a particular exception on failure of a precondition, you can use the generic overload of <xref:System.Diagnostics.Contracts.Contract.Requires%2A> as follows.</span></span>

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a><span data-ttu-id="79020-132">Starší verze #requires.</span><span class="sxs-lookup"><span data-stu-id="79020-132">Legacy Requires Statements</span></span>

<span data-ttu-id="79020-133">Většinu kódu obsahuje nějaké ověření parametru v podobě `if` - `then` - `throw` kódu.</span><span class="sxs-lookup"><span data-stu-id="79020-133">Most code contains some parameter validation in the form of `if`-`then`-`throw` code.</span></span> <span data-ttu-id="79020-134">Nástroje pro kontrakt rozpoznat tyto příkazy jako předpoklady v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="79020-134">The contract tools recognize these statements as preconditions in the following cases:</span></span>

- <span data-ttu-id="79020-135">Příkazy nacházet před všechny ostatní příkazy v metodě.</span><span class="sxs-lookup"><span data-stu-id="79020-135">The statements appear before any other statements in a method.</span></span>

- <span data-ttu-id="79020-136">Celá sada těchto příkazů je následována explicitní <xref:System.Diagnostics.Contracts.Contract> volání metody, jako je například volání <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, nebo <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="79020-136">The entire set of such statements is followed by an explicit <xref:System.Diagnostics.Contracts.Contract> method call, such as a call to the <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, or <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> method.</span></span>

<span data-ttu-id="79020-137">Když `if` - `then` - `throw` příkazy se zobrazí v tomto formuláři nástroje rozpoznat jako starší verze `requires` příkazy.</span><span class="sxs-lookup"><span data-stu-id="79020-137">When `if`-`then`-`throw` statements appear in this form, the tools recognize them as legacy `requires` statements.</span></span> <span data-ttu-id="79020-138">Pokud žádné jiné smlouvy, postupujte podle `if` - `then` - `throw` pořadí, -end kód <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="79020-138">If no other contracts follow the `if`-`then`-`throw` sequence, end the code with the <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> method.</span></span>

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

<span data-ttu-id="79020-139">Všimněte si, že je podmínka v předchozím testu negovaným čítačem předběžné podmínky.</span><span class="sxs-lookup"><span data-stu-id="79020-139">Note that the condition in the preceding test is a negated precondition.</span></span> <span data-ttu-id="79020-140">(Skutečné Předběžná podmínka by `x != null`.) Předpokladem negovaným čítačem je vysoce omezenou: Musí být napsaná, jak je znázorněno v předchozím příkladu; To znamená, měl by obsahovat žádné `else` klauzule a text `then` klauzule musí být jediný `throw` příkazu.</span><span class="sxs-lookup"><span data-stu-id="79020-140">(The actual precondition would be `x != null`.) A negated precondition is highly restricted: It must be written as shown in the previous example; that is, it should contain no `else` clauses, and the body of the `then` clause must be a single `throw` statement.</span></span> <span data-ttu-id="79020-141">`if` Test je v souladu s čistoty a viditelnost pravidla (naleznete v tématu [pokyny k používání](#usage_guidelines)), ale `throw` výraz se vztahuje pouze na čistotě pravidla.</span><span class="sxs-lookup"><span data-stu-id="79020-141">The `if` test is subject to both purity and visibility rules (see [Usage Guidelines](#usage_guidelines)), but the `throw` expression is subject only to purity rules.</span></span> <span data-ttu-id="79020-142">Typ výjimky vyvolané však musí být jako viditelný jako způsob, ve kterém dochází kontrakt.</span><span class="sxs-lookup"><span data-stu-id="79020-142">However, the type of the exception thrown must be as visible as the method in which the contract occurs.</span></span>

## <a name="postconditions"></a><span data-ttu-id="79020-143">Vstupních</span><span class="sxs-lookup"><span data-stu-id="79020-143">Postconditions</span></span>

<span data-ttu-id="79020-144">Vstupních jsou kontrakty pro stav metody při jeho ukončení.</span><span class="sxs-lookup"><span data-stu-id="79020-144">Postconditions are contracts for the state of a method when it terminates.</span></span> <span data-ttu-id="79020-145">Neplatná následná se kontroluje jenom před ukončením metody.</span><span class="sxs-lookup"><span data-stu-id="79020-145">The postcondition is checked just before exiting a method.</span></span> <span data-ttu-id="79020-146">Chování za běhu se nezdařilo vstupních určuje analyzátor modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="79020-146">The run-time behavior of failed postconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="79020-147">Na rozdíl od předběžné podmínky může následným podmínkám odkazovat na členy s méně viditelnost.</span><span class="sxs-lookup"><span data-stu-id="79020-147">Unlike preconditions, postconditions may reference members with less visibility.</span></span> <span data-ttu-id="79020-148">Klient nemusí být schopen porozumět nebo učiňte použít některé informace vyjádřené neplatná následná používání soukromý stav, ale to nemá vliv na schopnost klienta pomocí metody správně.</span><span class="sxs-lookup"><span data-stu-id="79020-148">A client may not be able to understand or make use of some of the information expressed by a postcondition using private state, but this does not affect the client's ability to use the method correctly.</span></span>

### <a name="standard-postconditions"></a><span data-ttu-id="79020-149">Standardní vstupních</span><span class="sxs-lookup"><span data-stu-id="79020-149">Standard Postconditions</span></span>

<span data-ttu-id="79020-150">Standardní vstupních můžete vyjádřit pomocí <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="79020-150">You can express standard postconditions by using the <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> method.</span></span> <span data-ttu-id="79020-151">Vstupních express podmínku, která musí být `true` při normálním ukončení metody.</span><span class="sxs-lookup"><span data-stu-id="79020-151">Postconditions express a condition that must be `true` upon normal termination of the method.</span></span>

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a><span data-ttu-id="79020-152">Mimořádné vstupních</span><span class="sxs-lookup"><span data-stu-id="79020-152">Exceptional Postconditions</span></span>

<span data-ttu-id="79020-153">Mimořádné vstupních jsou následným podmínkám, které by měly být `true` při konkrétní výjimka je vyvolána metoda.</span><span class="sxs-lookup"><span data-stu-id="79020-153">Exceptional postconditions are postconditions that should be `true` when a particular exception is thrown by a method.</span></span> <span data-ttu-id="79020-154">Určíte tyto vstupních pomocí <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> metody, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79020-154">You can specify these postconditions by using the <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> method, as the following example shows.</span></span>

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

<span data-ttu-id="79020-155">Argument je podmínka, která musí být `true` pokaždé, když výjimka, která je podtypem typu `T` je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="79020-155">The argument is the condition that must be `true` whenever an exception that is a subtype of `T` is thrown.</span></span>

<span data-ttu-id="79020-156">Existují některé typy výjimek, které je obtížné pro použití v výjimečných neplatná následná.</span><span class="sxs-lookup"><span data-stu-id="79020-156">There are some exception types that are difficult to use in an exceptional postcondition.</span></span> <span data-ttu-id="79020-157">Například pomocí typu <xref:System.Exception> pro `T` vyžaduje metodu zajistit podmínku bez ohledu na typ výjimky, která je vyvolána, i když je přetečení zásobníku nebo jinou výjimku nemožné řízení.</span><span class="sxs-lookup"><span data-stu-id="79020-157">For example, using the type <xref:System.Exception> for `T` requires the method to guarantee the condition regardless of the type of exception that is thrown, even if it is a stack overflow or other impossible-to-control exception.</span></span> <span data-ttu-id="79020-158">Mimořádné vstupních byste měli použít pouze pro konkrétní výjimky, které by mohla být vyvolána při člen volání, například když <xref:System.InvalidTimeZoneException> , je vyvolána <xref:System.TimeZoneInfo> volání metody.</span><span class="sxs-lookup"><span data-stu-id="79020-158">You should use exceptional postconditions only for specific exceptions that might be thrown when a member is called, for example, when an <xref:System.InvalidTimeZoneException> is thrown for a <xref:System.TimeZoneInfo> method call.</span></span>

### <a name="special-postconditions"></a><span data-ttu-id="79020-159">Speciální vstupních</span><span class="sxs-lookup"><span data-stu-id="79020-159">Special Postconditions</span></span>

<span data-ttu-id="79020-160">Pouze v rámci vstupních lze použít následující metody:</span><span class="sxs-lookup"><span data-stu-id="79020-160">The following methods may be used only within postconditions:</span></span>

- <span data-ttu-id="79020-161">Mohou odkazovat na návratové hodnoty metod ve vstupních pomocí výrazu `Contract.Result<T>()`, kde `T` nahrazuje návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="79020-161">You can refer to method return values in postconditions by using the expression `Contract.Result<T>()`, where `T` is replaced by the return type of the method.</span></span> <span data-ttu-id="79020-162">Pokud kompilátor nemůže odvodit typ, je nutné ho zadat explicitně.</span><span class="sxs-lookup"><span data-stu-id="79020-162">When the compiler is unable to infer the type, you must explicitly provide it.</span></span> <span data-ttu-id="79020-163">Například C# se kompilátor nemůže odvodit typy pro metody, které nepřebírají žádné argumenty, takže vyžaduje následující neplatná následná: `Contract.Ensures(0 <Contract.Result<int>())` Metody s návratovým typem `void` nemůže odkazovat na `Contract.Result<T>()` v jejich následným podmínkám.</span><span class="sxs-lookup"><span data-stu-id="79020-163">For example, the C# compiler is unable to infer types for methods that do not take any arguments, so it requires the following postcondition: `Contract.Ensures(0 <Contract.Result<int>())` Methods with a return type of `void` cannot refer to `Contract.Result<T>()` in their postconditions.</span></span>

- <span data-ttu-id="79020-164">Hodnotu prestate neplatná následná odkazuje na hodnotu výrazu na začátku metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="79020-164">A prestate value in a postcondition refers to the value of an expression at the start of a method or property.</span></span> <span data-ttu-id="79020-165">Používá výraz `Contract.OldValue<T>(e)`, kde `T` je typ `e`.</span><span class="sxs-lookup"><span data-stu-id="79020-165">It uses the expression `Contract.OldValue<T>(e)`, where `T` is the type of `e`.</span></span> <span data-ttu-id="79020-166">Pokaždé, když je kompilátor může odvodit typ, můžete vynechat argument obecného typu.</span><span class="sxs-lookup"><span data-stu-id="79020-166">You can omit the generic type argument whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="79020-167">(Například kompilátor jazyka C# vždy odvodí typ protože přebírá argument.) Existuje několik omezení na co může dojít v `e` a kontext, ve kterých může zobrazit staré výrazu.</span><span class="sxs-lookup"><span data-stu-id="79020-167">(For example, the C# compiler always infers the type because it takes an argument.) There are several restrictions on what can occur in `e` and the contexts in which an old expression may appear.</span></span> <span data-ttu-id="79020-168">Původní výraz nemůže obsahovat jiný výraz staré.</span><span class="sxs-lookup"><span data-stu-id="79020-168">An old expression cannot contain another old expression.</span></span> <span data-ttu-id="79020-169">Co je nejdůležitější staré výrazu musí odkazovat na hodnotu, která byla uložena ve stavu Předběžná podmínka metody.</span><span class="sxs-lookup"><span data-stu-id="79020-169">Most importantly, an old expression must refer to a value that existed in the method's precondition state.</span></span> <span data-ttu-id="79020-170">Jinými slovy, musí být výraz, který může být vyhodnocen, dokud je předběžná podmínka metody `true`.</span><span class="sxs-lookup"><span data-stu-id="79020-170">In other words, it must be an expression that can be evaluated as long as the method's precondition is `true`.</span></span> <span data-ttu-id="79020-171">Tady je několik instancí tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="79020-171">Here are several instances of that rule.</span></span>

  - <span data-ttu-id="79020-172">Hodnota musí existovat ve stavu Předběžná podmínka metody.</span><span class="sxs-lookup"><span data-stu-id="79020-172">The value must exist in the method's precondition state.</span></span> <span data-ttu-id="79020-173">Aby bylo možné odkazovat pole v objektu, předběžné podmínky musí zaručit, že objekt je vždy nenulový.</span><span class="sxs-lookup"><span data-stu-id="79020-173">In order to reference a field on an object, the preconditions must guarantee that the object is always non-null.</span></span>

  - <span data-ttu-id="79020-174">Nelze se odkazovat na návratovou hodnotu metody v původní výraz:</span><span class="sxs-lookup"><span data-stu-id="79020-174">You cannot refer to the method's return value in an old expression:</span></span>

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - <span data-ttu-id="79020-175">Nelze se odkazovat na `out` parametry ve výrazu staré.</span><span class="sxs-lookup"><span data-stu-id="79020-175">You cannot refer to `out` parameters in an old expression.</span></span>

  - <span data-ttu-id="79020-176">Původní výraz nemůže záviset na vazby proměnné kvantifikátor rozsah kvantifikátor závislých na návratovou hodnotu metody:</span><span class="sxs-lookup"><span data-stu-id="79020-176">An old expression cannot depend on the bound variable of a quantifier if the range of the quantifier depends on the return value of the method:</span></span>

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - <span data-ttu-id="79020-177">Původní výraz nemůže odkazovat na parametr anonymního delegáta v <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A> volat, pokud se používá jako indexer nebo argument volání metody:</span><span class="sxs-lookup"><span data-stu-id="79020-177">An old expression cannot refer to the parameter of the anonymous delegate in a <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> call unless it is used as an indexer or argument to a method call:</span></span>

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - <span data-ttu-id="79020-178">Původní výraz nelze provést, v těle anonymního delegáta hodnotou staré výrazu závislých na některý z parametrů anonymního delegáta, pokud anonymního delegáta je argument <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="79020-178">An old expression cannot occur in the body of an anonymous delegate if the value of the old expression depends on any of the parameters of the anonymous delegate, unless the anonymous delegate is an argument to the <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> method:</span></span>

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - <span data-ttu-id="79020-179">`Out` Parametry představovat problém, protože kontrakty předcházet tělo metody a většina kompilátorů nejsou povoleny odkazy na `out` ve vstupních parametrů.</span><span class="sxs-lookup"><span data-stu-id="79020-179">`Out` parameters present a problem because contracts appear before the body of the method, and most compilers do not allow references to `out` parameters in postconditions.</span></span> <span data-ttu-id="79020-180">Pro vyřešení tohoto problému <xref:System.Diagnostics.Contracts.Contract> třída poskytuje <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> metodu, která umožňuje neplatná následná na základě `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="79020-180">To solve this problem, the <xref:System.Diagnostics.Contracts.Contract> class provides the <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method, which allows a postcondition based on an `out` parameter.</span></span>

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      <span data-ttu-id="79020-181">Stejně jako u <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> metodu, můžete vynechat parametr obecného typu pokaždé, když je kompilátor může odvodit typ.</span><span class="sxs-lookup"><span data-stu-id="79020-181">As with the <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> method, you can omit the generic type parameter whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="79020-182">Kontrakt RW nahradí volání metody s hodnotou `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="79020-182">The contract rewriter replaces the method call with the value of the `out` parameter.</span></span> <span data-ttu-id="79020-183"><xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Metoda může vyskytovat jenom ve vstupních.</span><span class="sxs-lookup"><span data-stu-id="79020-183">The <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method may appear only in postconditions.</span></span> <span data-ttu-id="79020-184">Argument metody musí být `out` parametru nebo pole struktury `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="79020-184">The argument to the method must be an `out` parameter or a field of a structure `out` parameter.</span></span> <span data-ttu-id="79020-185">Je také užitečná při odkazu na pole v neplatná následná struktura konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="79020-185">The latter is also useful when referring to fields in the postcondition of a structure constructor.</span></span>

      > [!NOTE]
      > <span data-ttu-id="79020-186">V současné době nástrojů pro analýzu kódu kontraktu nekontrolují, zda `out` parametry jsou inicializovány správně a jejich uvedením v neplatná následná ignorovat.</span><span class="sxs-lookup"><span data-stu-id="79020-186">Currently, the code contract analysis tools do not check whether `out` parameters are initialized properly and disregard their mention in the postcondition.</span></span> <span data-ttu-id="79020-187">Proto v předchozím příkladu, pokud řádku po kontrakt použili hodnotu `x` namísto celého čísla přiřazení k němu, kompilátor by vystavovat správné chyby.</span><span class="sxs-lookup"><span data-stu-id="79020-187">Therefore, in the previous example, if the line after the contract had used the value of `x` instead of assigning an integer to it, a compiler would not issue the correct error.</span></span> <span data-ttu-id="79020-188">Ale na sestavení, ve kterém je preprocesoru symbol CONTRACTS_FULL není definována (takové asa sestavení pro vydání), kompilátor vygeneruje chybu.</span><span class="sxs-lookup"><span data-stu-id="79020-188">However, on a build where the CONTRACTS_FULL preprocessor symbol is not defined (such asa release build), the compiler will issue an error.</span></span>

## <a name="invariants"></a><span data-ttu-id="79020-189">Výstupních podmínek</span><span class="sxs-lookup"><span data-stu-id="79020-189">Invariants</span></span>

<span data-ttu-id="79020-190">Objekt výstupních podmínek jsou podmínky, které by měl mít hodnotu true pro každou instanci třídy pokaždé, když je viditelné pro klienta.</span><span class="sxs-lookup"><span data-stu-id="79020-190">Object invariants are conditions that should be true for each instance of a class whenever that object is visible to a client.</span></span> <span data-ttu-id="79020-191">Vyjadřují podmínky, za kterých objekt se považuje za správné.</span><span class="sxs-lookup"><span data-stu-id="79020-191">They express the conditions under which the object is considered to be correct.</span></span>

<span data-ttu-id="79020-192">Invariantní metody jsou označeny se označené <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="79020-192">The invariant methods are identified by being marked with the <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> attribute.</span></span> <span data-ttu-id="79020-193">Invariantní metody musejí obsahovat žádný kód s výjimkou pořadí volání <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> metoda jednotlivé invariantní, z nichž každý určuje, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79020-193">The invariant methods must contain no code except for a sequence of calls to the <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> method, each of which specifies an individual invariant, as shown in the following example.</span></span>

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

<span data-ttu-id="79020-194">Výstupních podmínek jsou definovány podmíněně preprocesoru symbol CONTRACTS_FULL.</span><span class="sxs-lookup"><span data-stu-id="79020-194">Invariants are conditionally defined by the CONTRACTS_FULL preprocessor symbol.</span></span> <span data-ttu-id="79020-195">Během kontroly za běhu, jsou kontrolovány výstupních podmínek na konci každé veřejné metody.</span><span class="sxs-lookup"><span data-stu-id="79020-195">During run-time checking, invariants are checked at the end of each public method.</span></span> <span data-ttu-id="79020-196">Pokud invariantní uvádí veřejnou metodu ve stejné třídě, je zakázané invariantní zkontrolujte, jestli by normálně mohlo dojít na konci této veřejné metody.</span><span class="sxs-lookup"><span data-stu-id="79020-196">If an invariant mentions a public method in the same class, the invariant check that would normally happen at the end of that public method is disabled.</span></span> <span data-ttu-id="79020-197">Místo toho kontrola probíhá pouze na konci volání vnější metody dané třídy.</span><span class="sxs-lookup"><span data-stu-id="79020-197">Instead, the check occurs only at the end of the outermost method call to that class.</span></span> <span data-ttu-id="79020-198">Také se to stane, když je třída opětovný vstup z důvodu volání metody na jinou třídu.</span><span class="sxs-lookup"><span data-stu-id="79020-198">This also happens if the class is re-entered because of a call to a method on another class.</span></span> <span data-ttu-id="79020-199">Výstupních podmínek se kontroluje finalizační metodu objektu a <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace.</span><span class="sxs-lookup"><span data-stu-id="79020-199">Invariants are not checked for an object finalizer and an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span>

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a><span data-ttu-id="79020-200">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="79020-200">Usage Guidelines</span></span>

### <a name="contract-ordering"></a><span data-ttu-id="79020-201">Kontrakt řazení</span><span class="sxs-lookup"><span data-stu-id="79020-201">Contract Ordering</span></span>

<span data-ttu-id="79020-202">V následující tabulce jsou uvedeny pořadí prvků, které byste měli použít při zápisu kontrakty – metoda.</span><span class="sxs-lookup"><span data-stu-id="79020-202">The following table shows the order of elements you should use when you write method contracts.</span></span>

|`If-then-throw statements`|<span data-ttu-id="79020-203">Zpětně kompatibilní veřejné předběžné podmínky</span><span class="sxs-lookup"><span data-stu-id="79020-203">Backward-compatible public preconditions</span></span>|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|<span data-ttu-id="79020-204">Všechny veřejné předběžné podmínky.</span><span class="sxs-lookup"><span data-stu-id="79020-204">All public preconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="79020-205">Všechny veřejné vstupních (normální).</span><span class="sxs-lookup"><span data-stu-id="79020-205">All public (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="79020-206">Všechny veřejné výjimečných následným podmínkám.</span><span class="sxs-lookup"><span data-stu-id="79020-206">All public exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="79020-207">Všechny privátní nebo interní vstupních (normální).</span><span class="sxs-lookup"><span data-stu-id="79020-207">All private/internal (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="79020-208">Privátní nebo interní výjimečných vstupních.</span><span class="sxs-lookup"><span data-stu-id="79020-208">All private/internal exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|<span data-ttu-id="79020-209">Pokud používáte `if` - `then` - `throw` stylu předběžné podmínky bez jiných smluv, umístěte volání <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> označuje, že všechny předchozí, pokud jsou předběžné podmínky kontroly.</span><span class="sxs-lookup"><span data-stu-id="79020-209">If using `if`-`then`-`throw` style preconditions without any other contracts, place a call to <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> to indicate that all previous if checks are preconditions.</span></span>|

<a name="purity"></a>

### <a name="purity"></a><span data-ttu-id="79020-210">Čistota</span><span class="sxs-lookup"><span data-stu-id="79020-210">Purity</span></span>

<span data-ttu-id="79020-211">Všechny metody, které jsou volány v rámci smlouvy musí být čistě; To znamená se nesmí aktualizovat žádné stávající stav.</span><span class="sxs-lookup"><span data-stu-id="79020-211">All methods that are called within a contract must be pure; that is, they must not update any preexisting state.</span></span> <span data-ttu-id="79020-212">Čistě metoda může upravit objekty, které byly vytvořeny po vstupu do čistého metody.</span><span class="sxs-lookup"><span data-stu-id="79020-212">A pure method is allowed to modify objects that have been created after entry into the pure method.</span></span>

<span data-ttu-id="79020-213">Kód kontraktu nástroje aktuálně předpokládají, že jsou čistě následujících prvků kódu:</span><span class="sxs-lookup"><span data-stu-id="79020-213">Code contract tools currently assume that the following code elements are pure:</span></span>

- <span data-ttu-id="79020-214">Metody, které jsou označené <xref:System.Diagnostics.Contracts.PureAttribute>.</span><span class="sxs-lookup"><span data-stu-id="79020-214">Methods that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span>

- <span data-ttu-id="79020-215">Typy, které jsou označené <xref:System.Diagnostics.Contracts.PureAttribute> (atribut platí pro všechny typy metod).</span><span class="sxs-lookup"><span data-stu-id="79020-215">Types that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute> (the attribute applies to all the type's methods).</span></span>

- <span data-ttu-id="79020-216">Přístupové objekty get vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="79020-216">Property get accessors.</span></span>

- <span data-ttu-id="79020-217">Operátory (statické metody, jejichž názvy začínají písmenem "op" a že máte jeden nebo dva parametry a návratový typ jiný než void).</span><span class="sxs-lookup"><span data-stu-id="79020-217">Operators (static methods whose names start with "op", and that have one or two parameters and a non-void return type).</span></span>

- <span data-ttu-id="79020-218">Jakoukoli metodu, jejíž plně kvalifikovaný název začíná řetězcem "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" nebo "System.Type".</span><span class="sxs-lookup"><span data-stu-id="79020-218">Any method whose fully qualified name begins with "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path", or "System.Type".</span></span>

- <span data-ttu-id="79020-219">Některé vyvolání delegáta, za předpokladu, že má atribut samotného typu delegáta <xref:System.Diagnostics.Contracts.PureAttribute>.</span><span class="sxs-lookup"><span data-stu-id="79020-219">Any invoked delegate, provided that the delegate type itself is attributed with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span> <span data-ttu-id="79020-220">Typy delegátů <xref:System.Predicate%601?displayProperty=nameWithType> a <xref:System.Comparison%601?displayProperty=nameWithType> jsou považovány za čistě.</span><span class="sxs-lookup"><span data-stu-id="79020-220">The delegate types <xref:System.Predicate%601?displayProperty=nameWithType> and <xref:System.Comparison%601?displayProperty=nameWithType> are considered pure.</span></span>

<a name="visibility"></a>

### <a name="visibility"></a><span data-ttu-id="79020-221">Viditelnost</span><span class="sxs-lookup"><span data-stu-id="79020-221">Visibility</span></span>

<span data-ttu-id="79020-222">Všechny členy, které jsou uvedené ve smlouvě musí být minimálně viditelná jako způsob, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="79020-222">All members mentioned in a contract must be at least as visible as the method in which they appear.</span></span> <span data-ttu-id="79020-223">Například soukromé pole nelze uvést v předběžné podmínce pro veřejnou metodu; klienty nelze ověřit takovou smlouvu před volají metodu.</span><span class="sxs-lookup"><span data-stu-id="79020-223">For example, a private field cannot be mentioned in a precondition for a public method; clients cannot validate such a contract before they call the method.</span></span> <span data-ttu-id="79020-224">Ale pokud pole je označeno <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, se vyjímá z těchto pravidel.</span><span class="sxs-lookup"><span data-stu-id="79020-224">However, if the field is marked with the <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, it is exempt from these rules.</span></span>

## <a name="example"></a><span data-ttu-id="79020-225">Příklad</span><span class="sxs-lookup"><span data-stu-id="79020-225">Example</span></span>

<span data-ttu-id="79020-226">Následující příklad ukazuje použití kontrakty kódu.</span><span class="sxs-lookup"><span data-stu-id="79020-226">The following example shows the use of code contracts.</span></span>

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
