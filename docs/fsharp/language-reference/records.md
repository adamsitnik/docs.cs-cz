---
title: Záznamy
description: Zjistěte, jak F# záznamy představují jednoduchý agregace pojmenovaných hodnot, volitelně s členy.
ms.date: 05/16/2016
ms.openlocfilehash: a499755383654ddaf76af12776ee93f27834b7b0
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656138"
---
# <a name="records"></a><span data-ttu-id="125b2-103">Záznamy</span><span class="sxs-lookup"><span data-stu-id="125b2-103">Records</span></span>

<span data-ttu-id="125b2-104">Záznamy představují jednoduchý agregace pojmenovaných hodnot, volitelně s členy.</span><span class="sxs-lookup"><span data-stu-id="125b2-104">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="125b2-105">Počínaje F# 4.1, mohou být buď struktury nebo referenční typy.</span><span class="sxs-lookup"><span data-stu-id="125b2-105">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="125b2-106">Jsou odkazové typy ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="125b2-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="125b2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="125b2-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="125b2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="125b2-108">Remarks</span></span>

<span data-ttu-id="125b2-109">V předchozí syntaxi *typename* je název typu záznamu *label1* a *label2* jsou názvy hodnot, označuje jako *popisky*, a *type1* a *type2* typy těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="125b2-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="125b2-110">*seznam členů* je volitelný seznam členů typu.</span><span class="sxs-lookup"><span data-stu-id="125b2-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="125b2-111">Můžete použít `[<Struct>]` atributu k vytvoření záznamu – struktura, nikoli záznam, který je typem odkazu.</span><span class="sxs-lookup"><span data-stu-id="125b2-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="125b2-112">Dále je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="125b2-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="125b2-113">Když každému popisku je na samostatném řádku, středník je volitelné.</span><span class="sxs-lookup"><span data-stu-id="125b2-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="125b2-114">Můžete nastavit hodnoty ve výrazech říká *zaznamenat výrazy*.</span><span class="sxs-lookup"><span data-stu-id="125b2-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="125b2-115">Kompilátor odvodí typ z popisky použít (v případě, že popisky jsou dostatečně liší od těch, které další typy záznamů).</span><span class="sxs-lookup"><span data-stu-id="125b2-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="125b2-116">Složené závorky ({}) uzavřete výrazu záznamu.</span><span class="sxs-lookup"><span data-stu-id="125b2-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="125b2-117">Následující kód ukazuje výraz záznamu, která inicializuje záznam s tři prvky typu float s popisky `x`, `y` a `z`.</span><span class="sxs-lookup"><span data-stu-id="125b2-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="125b2-118">Zkrácený tvar nepoužívejte, pokud může být jiný typ, který má také stejné popisky.</span><span class="sxs-lookup"><span data-stu-id="125b2-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="125b2-119">Popisky nedávno deklarovaného typu přednost dříve deklarovaný typ, tak v předchozím příkladu `mypoint3D` odvozena jako `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="125b2-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="125b2-120">Můžete explicitně určit typ záznamu, stejně jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="125b2-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="125b2-121">Metody lze definovat pro typy záznamů pouze jako typy tříd.</span><span class="sxs-lookup"><span data-stu-id="125b2-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="125b2-122">Vytváření záznamů pomocí výrazů záznamů</span><span class="sxs-lookup"><span data-stu-id="125b2-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="125b2-123">Záznamy můžete inicializovat pomocí popisků, které jsou definovány v záznamu.</span><span class="sxs-lookup"><span data-stu-id="125b2-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="125b2-124">Výraz, který se k tomu se říká *zaznamenat výraz*.</span><span class="sxs-lookup"><span data-stu-id="125b2-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="125b2-125">Použijte složené závorky a uzavřete výrazu záznamu použijte jako oddělovač středník.</span><span class="sxs-lookup"><span data-stu-id="125b2-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="125b2-126">Následující příklad ukazuje, jak vytvořit záznam.</span><span class="sxs-lookup"><span data-stu-id="125b2-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="125b2-127">Středníky po poslední pole ve výrazu záznamu a v definici typu jsou volitelné, bez ohledu na to, jestli jsou tato pole vše na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="125b2-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="125b2-128">Při vytváření záznamu je třeba zadat hodnoty pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="125b2-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="125b2-129">Nelze se odkazovat na hodnoty jiných polí ve výrazu inicializace pro všechna pole.</span><span class="sxs-lookup"><span data-stu-id="125b2-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="125b2-130">V následujícím kódu, typ `myRecord2` je odvozen z názvy polí.</span><span class="sxs-lookup"><span data-stu-id="125b2-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="125b2-131">Volitelně můžete zadat název typu explicitně.</span><span class="sxs-lookup"><span data-stu-id="125b2-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="125b2-132">Jiná forma konstrukce záznamu může být užitečné, když je nutné zkopírovat existující záznam a případně změnit některé z hodnot pole.</span><span class="sxs-lookup"><span data-stu-id="125b2-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="125b2-133">To ukazuje následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="125b2-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="125b2-134">Tato forma výrazu záznamu je volána *kopírování a aktualizace výrazů záznamů*.</span><span class="sxs-lookup"><span data-stu-id="125b2-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="125b2-135">Záznamy jsou neměnné ve výchozím nastavení; změněné záznamy však můžete snadno vytvořit pomocí výrazu kopírování a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="125b2-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="125b2-136">Můžete také explicitně určit proměnlivé pole.</span><span class="sxs-lookup"><span data-stu-id="125b2-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="125b2-137">Nepoužívejte atribut DefaultValue u polí záznamu.</span><span class="sxs-lookup"><span data-stu-id="125b2-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="125b2-138">Lepším řešením je definovat výchozí instance záznamy s poli, které jsou inicializovány na výchozí hodnoty a pak použijte kopii a aktualizovat výrazu záznamu pro nastavení všechna pole, která se liší od výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="125b2-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="125b2-139">Vytvoření vzájemně rekurzivní záznamů</span><span class="sxs-lookup"><span data-stu-id="125b2-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="125b2-140">Nějakou dobu, během vytváření záznamu, můžete na něm závisí na jiný typ, který chcete definovat později.</span><span class="sxs-lookup"><span data-stu-id="125b2-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="125b2-141">Jedná se o chybu kompilace, není-li definovat typy záznamů bude vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="125b2-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="125b2-142">Definování vzájemně rekurzivní záznamy se použije `and` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="125b2-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="125b2-143">Díky tomu můžete propojit typy 2 nebo více záznamů.</span><span class="sxs-lookup"><span data-stu-id="125b2-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="125b2-144">Například následující kód definuje `Person` a `Address` typ jako vzájemně rekurzivní:</span><span class="sxs-lookup"><span data-stu-id="125b2-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string }
```

<span data-ttu-id="125b2-145">Pokud byste chtěli definovat bez předchozího příkladu `and` – klíčové slovo, pak nebude kompilovat.</span><span class="sxs-lookup"><span data-stu-id="125b2-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="125b2-146">`and` – Klíčové slovo je vyžadován pro vzájemně rekurzivní definice.</span><span class="sxs-lookup"><span data-stu-id="125b2-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="125b2-147">Porovnávání vzorů s záznamů</span><span class="sxs-lookup"><span data-stu-id="125b2-147">Pattern Matching with Records</span></span>

<span data-ttu-id="125b2-148">Záznamy můžete použití s porovnáváním vzorů.</span><span class="sxs-lookup"><span data-stu-id="125b2-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="125b2-149">Můžete explicitně určit některá pole a zadejte proměnné pro další pole, která se přiřadí, když je nalezena shoda.</span><span class="sxs-lookup"><span data-stu-id="125b2-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="125b2-150">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="125b2-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="125b2-151">Výstup tohoto kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="125b2-151">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="125b2-152">Rozdíly mezi třídami a záznamů</span><span class="sxs-lookup"><span data-stu-id="125b2-152">Differences Between Records and Classes</span></span>

<span data-ttu-id="125b2-153">Pole záznamu se liší od tříd jsou automaticky vystaveny jako vlastnosti a jsou použité k vytvoření a zkopírování záznamů.</span><span class="sxs-lookup"><span data-stu-id="125b2-153">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="125b2-154">Konstrukce záznamu se také liší od konstrukci třídy.</span><span class="sxs-lookup"><span data-stu-id="125b2-154">Record construction also differs from class construction.</span></span> <span data-ttu-id="125b2-155">V typu záznamu nelze definovat konstruktor.</span><span class="sxs-lookup"><span data-stu-id="125b2-155">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="125b2-156">Místo toho použije konstrukce zapsána syntaxí popsanou v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="125b2-156">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="125b2-157">Třídy nemají žádný přímý vztah mezi parametry konstruktoru, pole a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="125b2-157">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="125b2-158">Podobně jako typy sjednocení a struktura záznamy mají sémantiku strukturální rovnost.</span><span class="sxs-lookup"><span data-stu-id="125b2-158">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="125b2-159">Třídy mají referenční rovnost sémantiku.</span><span class="sxs-lookup"><span data-stu-id="125b2-159">Classes have reference equality semantics.</span></span> <span data-ttu-id="125b2-160">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="125b2-160">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="125b2-161">Výstup tohoto kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="125b2-161">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="125b2-162">Pokud píšete stejný kód s třídami, objekty dvou tříd by nerovnost, protože tyto dvě hodnoty by představují dva objekty v haldě a by jde porovnat jenom adresy (Pokud není typ třídy přepíše `System.Object.Equals` metoda).</span><span class="sxs-lookup"><span data-stu-id="125b2-162">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="125b2-163">Pokud potřebujete referenční rovnost pro záznamy, přidejte atribut `[<ReferenceEquality>]` výše záznam.</span><span class="sxs-lookup"><span data-stu-id="125b2-163">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="125b2-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="125b2-164">See also</span></span>

- [<span data-ttu-id="125b2-165">Typy F#</span><span class="sxs-lookup"><span data-stu-id="125b2-165">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="125b2-166">Třídy</span><span class="sxs-lookup"><span data-stu-id="125b2-166">Classes</span></span>](classes.md)
- [<span data-ttu-id="125b2-167">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="125b2-167">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="125b2-168">Referenční rovnost</span><span class="sxs-lookup"><span data-stu-id="125b2-168">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="125b2-169">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="125b2-169">Pattern Matching</span></span>](pattern-matching.md)
