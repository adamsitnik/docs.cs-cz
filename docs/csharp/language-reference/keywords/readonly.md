---
title: ReadOnly – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: c7f3b1b1525277bf948070c9121d151f9f520127
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660850"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="0e457-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0e457-102">readonly (C# Reference)</span></span>

<span data-ttu-id="0e457-103">`readonly` – Klíčové slovo je modifikátor, který je možné ve třech kontextech:</span><span class="sxs-lookup"><span data-stu-id="0e457-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="0e457-104">V [pole deklarace](#readonly-field-example), `readonly` označuje, že přiřazení pro pole může probíhat jenom jako součást deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="0e457-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span>
- <span data-ttu-id="0e457-105">V [ `readonly struct` definice](#readonly-struct-example), `readonly` znamená, že `struct` je neměnný.</span><span class="sxs-lookup"><span data-stu-id="0e457-105">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="0e457-106">V [ `ref readonly` metoda návratový](#ref-readonly-return-example), `readonly` modifikátor označuje, že metoda vrátí odkaz a zápisu nejsou povoleny na tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="0e457-106">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="0e457-107">Poslední dvě kontexty byly přidány v jazyce C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="0e457-107">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="0e457-108">Pole určené jen pro čtení, například</span><span class="sxs-lookup"><span data-stu-id="0e457-108">Readonly field example</span></span>

<span data-ttu-id="0e457-109">V tomto příkladu je hodnota pole `year` nelze změnit v metodě `ChangeYear`, i když je k ní přiřadí hodnota v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="0e457-109">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="0e457-110">Můžete přiřadit hodnoty k `readonly` pouze v následujících kontextů:</span><span class="sxs-lookup"><span data-stu-id="0e457-110">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="0e457-111">Pokud je proměnná inicializována v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="0e457-111">When the variable is initialized in the declaration, for example:</span></span>

```csharp
public readonly int y = 5;
```

- <span data-ttu-id="0e457-112">V konstruktoru instance třídy, která obsahuje deklaraci pole instance.</span><span class="sxs-lookup"><span data-stu-id="0e457-112">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="0e457-113">V statický konstruktor třídy, která obsahuje deklaraci statického pole.</span><span class="sxs-lookup"><span data-stu-id="0e457-113">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="0e457-114">Kontexty konstruktoru jsou také pouze kontextech, ve kterých je možné předat `readonly` jako pole [si](out-parameter-modifier.md) nebo [ref](ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="0e457-114">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="0e457-115">`readonly` – Klíčové slovo se liší od [const](const.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0e457-115">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="0e457-116">A `const` pole mohou být inicializovány pouze v deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="0e457-116">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="0e457-117">A `readonly` pole je možné přiřadit více než jednou v deklaraci pole a jakéhokoli konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0e457-117">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="0e457-118">Proto `readonly` pole může mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0e457-118">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="0e457-119">Také, zatímco `const` pole je konstantu kompilace `readonly` pole lze použít pro konstanty runtime jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0e457-119">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="0e457-120">V předchozím příkladu, pokud použijete příkaz jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0e457-120">In the preceding example, if you use a statement like the following example:</span></span>

`p2.y = 66;        // Error`

<span data-ttu-id="0e457-121">Zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="0e457-121">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="0e457-122">Příklad struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0e457-122">Readonly struct example</span></span>

<span data-ttu-id="0e457-123">`readonly` Modifikátor `struct` definice deklaruje, že struktura **neměnné**.</span><span class="sxs-lookup"><span data-stu-id="0e457-123">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="0e457-124">Každé pole instance `struct` musí být označen `readonly`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0e457-124">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="0e457-125">V předchozím příkladu [automatické vlastnosti jen pro čtení](../../properties.md#read-only) k deklaraci jeho úložiště.</span><span class="sxs-lookup"><span data-stu-id="0e457-125">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="0e457-126">Který dává pokyn kompilátoru k vytvoření `readonly` pomocná pole pro tyto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0e457-126">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="0e457-127">Můžete také deklarovat `readonly` přímo pole:</span><span class="sxs-lookup"><span data-stu-id="0e457-127">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="0e457-128">Přidání pole nejsou označeny `readonly` vygeneruje Chyba kompilátoru `CS8340`: "Pole instancí struktur jen pro čtení musí být jen pro čtení."</span><span class="sxs-lookup"><span data-stu-id="0e457-128">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="0e457-129">Příklad vrácené REF jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0e457-129">Ref readonly return example</span></span>

<span data-ttu-id="0e457-130">`readonly` Modifikátor `ref return` označuje, že výsledný odkaz nelze upravit.</span><span class="sxs-lookup"><span data-stu-id="0e457-130">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="0e457-131">Následující příklad vrátí odkaz na počátku.</span><span class="sxs-lookup"><span data-stu-id="0e457-131">The following example returns a reference to the origin.</span></span> <span data-ttu-id="0e457-132">Používá `readonly` modifikátor označuje, že volající nelze měnit původu:</span><span class="sxs-lookup"><span data-stu-id="0e457-132">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="0e457-133">Typ vrácený nemusí být `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="0e457-133">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="0e457-134">Libovolný typ, který může být vrácen `ref` může být vrácen `ref readonly`</span><span class="sxs-lookup"><span data-stu-id="0e457-134">Any type that can be returned by `ref` can be returned by `ref readonly`</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0e457-135">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0e457-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0e457-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e457-136">See also</span></span>

- [<span data-ttu-id="0e457-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0e457-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0e457-138">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0e457-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0e457-139">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0e457-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0e457-140">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="0e457-140">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="0e457-141">const</span><span class="sxs-lookup"><span data-stu-id="0e457-141">const</span></span>](const.md)
- [<span data-ttu-id="0e457-142">Pole</span><span class="sxs-lookup"><span data-stu-id="0e457-142">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
