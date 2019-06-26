---
title: C# pro příkaz
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: a0252493ffd251b8d760927345c71e2f5ef55aaa
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401510"
---
# <a name="for-c-reference"></a><span data-ttu-id="0ac48-102">for (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0ac48-102">for (C# reference)</span></span>

<span data-ttu-id="0ac48-103">`for` Příkaz opakuje příkaz nebo blok příkazů během zadaný logický výraz je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="0ac48-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="0ac48-104">Na libovolný bod v rámci `for` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu nebo kroku na následující iteraci ve smyčce pomocí [pokračovat](continue.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="0ac48-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="0ac48-105">Také můžete ukončit `for` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="0ac48-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="0ac48-106">Struktura `for` – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ac48-106">Structure of the `for` statement</span></span>

<span data-ttu-id="0ac48-107">`for` Definuje příkaz *inicializátor*, *podmínku*, a *iterátoru* oddíly:</span><span class="sxs-lookup"><span data-stu-id="0ac48-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="0ac48-108">Všechny tři oddíly jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="0ac48-108">All three sections are optional.</span></span> <span data-ttu-id="0ac48-109">Tělo smyčky je příkaz nebo blok příkazů.</span><span class="sxs-lookup"><span data-stu-id="0ac48-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="0ac48-110">Následující příklad ukazuje `for` všechny oddíly definované příkazem:</span><span class="sxs-lookup"><span data-stu-id="0ac48-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="0ac48-111">*Inicializátor* oddílu</span><span class="sxs-lookup"><span data-stu-id="0ac48-111">The *initializer* section</span></span>

<span data-ttu-id="0ac48-112">Příkazy v *inicializátor* oddílu jsou spouštěny pouze jednou, před vstupem smyčky.</span><span class="sxs-lookup"><span data-stu-id="0ac48-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="0ac48-113">*Inicializátor* oddíl je některý z následujících:</span><span class="sxs-lookup"><span data-stu-id="0ac48-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="0ac48-114">Deklarace a inicializace proměnné místní smyčky, která není přístupná z mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="0ac48-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="0ac48-115">Nula nebo více výrazy příkazu z následujícího seznamu, oddělené čárkami:</span><span class="sxs-lookup"><span data-stu-id="0ac48-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="0ac48-116">[přiřazení](../operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ac48-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="0ac48-117">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="0ac48-117">invocation of a method</span></span>

  - <span data-ttu-id="0ac48-118">Přidání předpony nebo přípony [přírůstek](../operators/arithmetic-operators.md#increment-operator-) výraz, jako například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="0ac48-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="0ac48-119">Přidání předpony nebo přípony [snížení](../operators/arithmetic-operators.md#decrement-operator---) výraz, jako například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="0ac48-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="0ac48-120">Vytvoření objektu pomocí [nové](../operators/new-operator.md) – operátor</span><span class="sxs-lookup"><span data-stu-id="0ac48-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="0ac48-121">[operátor await](await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="0ac48-121">[await](await.md) expression</span></span>

<span data-ttu-id="0ac48-122">*Inicializátor* oddílu ve výše uvedeném příkladu deklaruje a inicializuje proměnnou místní smyčky `i`:</span><span class="sxs-lookup"><span data-stu-id="0ac48-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="0ac48-123">*Podmínku* oddílu</span><span class="sxs-lookup"><span data-stu-id="0ac48-123">The *condition* section</span></span>

<span data-ttu-id="0ac48-124">*Podmínku* část, pokud jsou k dispozici, musí být logický výraz.</span><span class="sxs-lookup"><span data-stu-id="0ac48-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="0ac48-125">Tento výraz je vyhodnocen před každou iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="0ac48-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="0ac48-126">Pokud *podmínku* části není k dispozici nebo je logický výraz vyhodnocen `true`, další iteraci smyčky je provedeno; jinak, je ukončen smyčky.</span><span class="sxs-lookup"><span data-stu-id="0ac48-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="0ac48-127">*Podmínku* oddílu ve výše uvedeném příkladu určuje Pokud smyčku ukončí založena na hodnotě proměnné cyklu místní:</span><span class="sxs-lookup"><span data-stu-id="0ac48-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="0ac48-128">*Iterátoru* oddílu</span><span class="sxs-lookup"><span data-stu-id="0ac48-128">The *iterator* section</span></span>

<span data-ttu-id="0ac48-129">*Iterátoru* oddíl definuje, co se stane po každé iteraci těla smyčky.</span><span class="sxs-lookup"><span data-stu-id="0ac48-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="0ac48-130">*Iterátoru* oddíl obsahuje nula nebo více z následujících výrazy příkazu, oddělené čárkami:</span><span class="sxs-lookup"><span data-stu-id="0ac48-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="0ac48-131">[přiřazení](../operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ac48-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="0ac48-132">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="0ac48-132">invocation of a method</span></span>

- <span data-ttu-id="0ac48-133">Přidání předpony nebo přípony [přírůstek](../operators/arithmetic-operators.md#increment-operator-) výraz, jako například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="0ac48-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="0ac48-134">Přidání předpony nebo přípony [snížení](../operators/arithmetic-operators.md#decrement-operator---) výraz, jako například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="0ac48-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="0ac48-135">Vytvoření objektu pomocí [nové](../operators/new-operator.md) – operátor</span><span class="sxs-lookup"><span data-stu-id="0ac48-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="0ac48-136">[operátor await](await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="0ac48-136">[await](await.md) expression</span></span>

<span data-ttu-id="0ac48-137">*Iterátoru* proměnná místní smyčky zvýší části v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0ac48-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="0ac48-138">Příklady</span><span class="sxs-lookup"><span data-stu-id="0ac48-138">Examples</span></span>

<span data-ttu-id="0ac48-139">Následující příklad ukazuje několik méně běžné použití `for` části příkazu: přiřazení hodnoty proměnné vnější smyčky v *inicializátor* části volání metody v obou  *Inicializátor* a *iterátoru* oddíly a změnou hodnoty dvou proměnných ve *iterátoru* oddílu.</span><span class="sxs-lookup"><span data-stu-id="0ac48-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="0ac48-140">Vyberte **spustit** ke spuštění příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0ac48-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="0ac48-141">Potom můžete upravit kód a potom ho spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="0ac48-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="0ac48-142">Následující příklad definuje nekonečné `for` smyčka:</span><span class="sxs-lookup"><span data-stu-id="0ac48-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="0ac48-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0ac48-143">C# language specification</span></span>

<span data-ttu-id="0ac48-144">Další informace najdete v tématu [pro příkaz](~/_csharplang/spec/statements.md#the-for-statement) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ac48-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ac48-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ac48-145">See also</span></span>

- [<span data-ttu-id="0ac48-146">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0ac48-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0ac48-147">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0ac48-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ac48-148">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0ac48-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0ac48-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="0ac48-149">foreach, in</span></span>](foreach-in.md)
