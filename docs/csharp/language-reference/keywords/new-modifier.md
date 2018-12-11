---
title: New – modifikátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 07986ac0c49387422aa334711b6997b159151e79
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244958"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="ab980-102">New – modifikátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ab980-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="ab980-103">Při použití jako modifikátoru deklarace `new` – klíčové slovo explicitně skryje člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ab980-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="ab980-104">Při skrytí zděděného člena, odvozená verze člena nahradí verzi základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ab980-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="ab980-105">Ačkoli můžete skrýt členy, bez použití `new` modifikátor, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ab980-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="ab980-106">Pokud používáte `new` pro explicitní skrytí člena, potlačí toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="ab980-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="ab980-107">Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu členu a upravte jej pomocí `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ab980-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="ab980-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ab980-108">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="ab980-109">V tomto příkladu `BaseC.Invoke` je skryt `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="ab980-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="ab980-110">Pole `x` nemá vliv, protože není skryté podobným názvem.</span><span class="sxs-lookup"><span data-stu-id="ab980-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="ab980-111">Skrytí názvu prostřednictvím dědičnosti má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="ab980-111">Name hiding through inheritance takes one of the following forms:</span></span>

<span data-ttu-id="ab980-112">Obecně konstanta, pole, vlastnost nebo typ, který se používá ve třídě nebo struktuře skryje všechny členy základní třídy, které sdílejí její název.</span><span class="sxs-lookup"><span data-stu-id="ab980-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="ab980-113">Existují zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="ab980-113">There are special cases.</span></span>  <span data-ttu-id="ab980-114">Například, pokud deklarujete novou položku s názvem `N` mít typ, který není nevyvolatelný a základní typ deklaruje `N` na metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="ab980-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="ab980-115">Zobrazit [specifikace jazyka C# 5.0](https://www.microsoft.com/download/details.aspx?id=7029) podrobnosti (viz oddíl "Člen vyhledávání" v části "Expressions").</span><span class="sxs-lookup"><span data-stu-id="ab980-115">See the [C# 5.0 language specification](https://www.microsoft.com/download/details.aspx?id=7029) for details (see section "Member Lookup" in section "Expressions").</span></span>

<span data-ttu-id="ab980-116">Metody zavedené ve třídě nebo struktuře skryjí vlastnosti polí a typů, které sdílejí tento název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="ab980-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="ab980-117">Skryje také všechny metody základní třídy, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="ab980-117">It also hides all base class methods that have the same signature.</span></span>

<span data-ttu-id="ab980-118">Indexer zavedený ve třídě nebo struktuře skryje všechny základní třídy indexerů, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="ab980-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="ab980-119">Jedná se o chybu, chcete-li použít `new` a [přepsat](override.md) na stejný člen, protože dva Modifikátory mají vzájemně vylučují význam.</span><span class="sxs-lookup"><span data-stu-id="ab980-119">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="ab980-120">`new` Modifikátor vytvoří nový člen se stejným názvem a způsobí, že původní člen bude skrytý.</span><span class="sxs-lookup"><span data-stu-id="ab980-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="ab980-121">`override` Modifikátor rozšiřuje implementaci pro zděděného člena.</span><span class="sxs-lookup"><span data-stu-id="ab980-121">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="ab980-122">Použití `new` modifikátor v deklaraci, která neskryje zděděného člena, vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="ab980-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="ab980-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab980-123">Example</span></span>

<span data-ttu-id="ab980-124">V tomto příkladu základní třída `BaseC`a odvozená třída `DerivedC`, použijte stejný název pole `x`, který skryje hodnotu zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="ab980-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="ab980-125">Tento příklad ukazuje použití `new` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="ab980-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="ab980-126">Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="ab980-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="ab980-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab980-127">Example</span></span>

<span data-ttu-id="ab980-128">V tomto příkladu vnořené třídy skryjí třídu, která má stejný název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="ab980-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="ab980-129">Tento příklad ukazuje, jak používat `new` modifikátor k vyloučení upozornění a jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="ab980-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="ab980-130">Pokud odeberete `new` modifikátor, program bude stále kompilace a spuštění, ale zobrazí se následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="ab980-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="ab980-131">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab980-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ab980-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab980-132">See also</span></span>

- [<span data-ttu-id="ab980-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab980-133">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="ab980-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ab980-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ab980-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab980-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ab980-136">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="ab980-136">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="ab980-137">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="ab980-137">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="ab980-138">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="ab980-138">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="ab980-139">Znalost, kdy použít klíčová slova override a new</span><span class="sxs-lookup"><span data-stu-id="ab980-139">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
