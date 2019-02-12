---
title: Rozšíření typů
description: Zjistěte, jak F# rozšíření typu umožňují přidat nové členy do dříve definovaného objektu typu.
ms.date: 02/08/2019
ms.openlocfilehash: 69fb3b771b5334c5771f2ac75341b38c1dad5b90
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092472"
---
# <a name="type-extensions"></a><span data-ttu-id="246dc-103">Rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="246dc-103">Type extensions</span></span>

<span data-ttu-id="246dc-104">Rozšíření typů (také nazývané _rozšíření_) jsou řadu funkcí, které umožňují přidat nové členy dříve definovaného typu objektu.</span><span class="sxs-lookup"><span data-stu-id="246dc-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="246dc-105">Jsou tři funkce:</span><span class="sxs-lookup"><span data-stu-id="246dc-105">The three features are:</span></span>

* <span data-ttu-id="246dc-106">Rozšíření pro vnitřní typ</span><span class="sxs-lookup"><span data-stu-id="246dc-106">Intrinsic type extensions</span></span>
* <span data-ttu-id="246dc-107">Volitelná rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="246dc-107">Optional type extensions</span></span>
* <span data-ttu-id="246dc-108">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="246dc-108">Extension methods</span></span>

<span data-ttu-id="246dc-109">Každá lze použít v různých scénářích a má různé kompromisy.</span><span class="sxs-lookup"><span data-stu-id="246dc-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="246dc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="246dc-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="246dc-111">Rozšíření pro vnitřní typ</span><span class="sxs-lookup"><span data-stu-id="246dc-111">Intrinsic type extensions</span></span>

<span data-ttu-id="246dc-112">Rozšíření vnitřního typu je typ rozšíření, která rozšiřuje uživatelem definovaného typu.</span><span class="sxs-lookup"><span data-stu-id="246dc-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="246dc-113">Rozšíření vnitřního typu musí být definován ve stejném souboru **a** ve stejném oboru názvů nebo modulu jako typ se rozšíření.</span><span class="sxs-lookup"><span data-stu-id="246dc-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="246dc-114">Libovolná definice nebudou se [volitelná rozšíření typů](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="246dc-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="246dc-115">Rozšíření vnitřního typu jsou někdy čistší způsob, jak oddělit od deklarace typu funkce.</span><span class="sxs-lookup"><span data-stu-id="246dc-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="246dc-116">Následující příklad ukazuje, jak definovat rozšíření vnitřního typu:</span><span class="sxs-lookup"><span data-stu-id="246dc-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="246dc-117">Použití rozšíření typu umožňuje oddělit každou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="246dc-117">Using a type extension allows you to separate each of the following:</span></span>

* <span data-ttu-id="246dc-118">Deklarace `Variant` typu</span><span class="sxs-lookup"><span data-stu-id="246dc-118">The declaration of a `Variant` type</span></span>
* <span data-ttu-id="246dc-119">Funkce pro tisk `Variant` třídy v závislosti na jeho "tvar"</span><span class="sxs-lookup"><span data-stu-id="246dc-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
* <span data-ttu-id="246dc-120">Přístup k funkci tisku stylem objekt `.`– zápis</span><span class="sxs-lookup"><span data-stu-id="246dc-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="246dc-121">Jedná se o alternativu k definování vše jako člen na `Variant`.</span><span class="sxs-lookup"><span data-stu-id="246dc-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="246dc-122">Ačkoli to není ze své podstaty lepším řešením, může být čisticí reprezentace funkce v některých situacích.</span><span class="sxs-lookup"><span data-stu-id="246dc-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="246dc-123">Rozšíření vnitřního typu jsou kompilovány jako členy typu, rozšíření a zobrazí u typu, když je typ zkontrolován pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="246dc-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="246dc-124">Volitelná rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="246dc-124">Optional type extensions</span></span>

<span data-ttu-id="246dc-125">Rozšíření volitelného typu je rozšíření, které se objeví mimo původní modul, obor názvů a sestavení rozšiřovaného typu.</span><span class="sxs-lookup"><span data-stu-id="246dc-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="246dc-126">Volitelná rozšíření typů jsou užitečné pro rozšíření typu, který ještě nebyl definován sami.</span><span class="sxs-lookup"><span data-stu-id="246dc-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="246dc-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="246dc-127">For example:</span></span>

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

<span data-ttu-id="246dc-128">Teď umožňuje přistupovat k `RepeatElements` , pokud je člen <xref:System.Collections.Generic.IEnumerable%601> tak dlouho, dokud `Extensions` modulu je otevřen v oboru, který se k práci používáte.</span><span class="sxs-lookup"><span data-stu-id="246dc-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="246dc-129">Volitelná rozšíření nejsou zobrazeny na rozšířený typ při zkontrolován pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="246dc-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="246dc-130">Musí být volitelné rozšíření v modulech a jsou to jenom v oboru modulu, který obsahuje rozšíření je otevřená nebo je jinak v oboru.</span><span class="sxs-lookup"><span data-stu-id="246dc-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="246dc-131">Volitelní Členové rozšíření jsou kompilováni do statických členů, pro které je implicitně předána instance objektu jako první parametr.</span><span class="sxs-lookup"><span data-stu-id="246dc-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="246dc-132">Působí však jako v případě, že jsou členy instance nebo statickými členy podle toho, jak jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="246dc-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="246dc-133">Volitelní Členové rozšíření nejsou také viditelné C# nebo VB spotřebitele.</span><span class="sxs-lookup"><span data-stu-id="246dc-133">Optional extension members are also not visible to C# or VB consumers.</span></span> <span data-ttu-id="246dc-134">Mohou být pouze využívány v ostatních F# kódu.</span><span class="sxs-lookup"><span data-stu-id="246dc-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="246dc-135">Obecná omezení rozšíření pro vnitřní objekty a jsou volitelné typ</span><span class="sxs-lookup"><span data-stu-id="246dc-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="246dc-136">Je možné deklarovat typ rozšíření u obecného typu, kde je proměnná typu omezen.</span><span class="sxs-lookup"><span data-stu-id="246dc-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="246dc-137">Požadavek je, že omezení deklaraci rozšíření shoduje s jiným omezením deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="246dc-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="246dc-138">Ale i v případě, že omezení se shoda mezi deklarovaného typu a rozšíření typu, je možné, omezení a odvodit subjektem rozšířený člen, který má jiný požadavek na parametr typu než deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="246dc-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="246dc-139">Příklad:</span><span class="sxs-lookup"><span data-stu-id="246dc-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="246dc-140">Neexistuje žádný způsob, jak získat tento kód pro práci s rozšíření volitelného typu:</span><span class="sxs-lookup"><span data-stu-id="246dc-140">There is no way to get this code to work with an optional type extension:</span></span>

* <span data-ttu-id="246dc-141">Je, `Sum` člen má jiné omezení `'T` (`static member get_Zero` a `static member (+)`) než co definuje typ rozšíření.</span><span class="sxs-lookup"><span data-stu-id="246dc-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
* <span data-ttu-id="246dc-142">Úprava rozšíření typu mít stejné omezení jako `Sum` už nebude odpovídat definované omezení na `IEnumerable<'T>`.</span><span class="sxs-lookup"><span data-stu-id="246dc-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
* <span data-ttu-id="246dc-143">Změna `member this.Sum` k `member inline this.Sum` vám poskytne chybu, že se neshodují omezení typu.</span><span class="sxs-lookup"><span data-stu-id="246dc-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="246dc-144">Co je žádoucí jsou statické metody, které "float v prostoru" a lze zobrazit, jako by se při rozšiřování typu.</span><span class="sxs-lookup"><span data-stu-id="246dc-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="246dc-145">To je, kde budou nezbytné metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="246dc-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="246dc-146">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="246dc-146">Extension methods</span></span>

<span data-ttu-id="246dc-147">Nakonec metody rozšíření (říká se jim "C# stylu členy rozšíření") mohou být deklarovány v F# jako metodu statického člena třídy.</span><span class="sxs-lookup"><span data-stu-id="246dc-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="246dc-148">Rozšiřující metody jsou užitečné pro když chcete definovat rozšíření u obecného typu, který bude proměnná typu omezení.</span><span class="sxs-lookup"><span data-stu-id="246dc-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="246dc-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="246dc-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="246dc-150">Když se použije, tento kód filtrovacího řetězce se zobrazí jako `Sum` je definován na <xref:System.Collections.Generic.IEnumerable%601>, tak dlouho, dokud `Extensions` byl otevřen nebo je v oboru.</span><span class="sxs-lookup"><span data-stu-id="246dc-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="246dc-151">Další poznámky</span><span class="sxs-lookup"><span data-stu-id="246dc-151">Other remarks</span></span>

<span data-ttu-id="246dc-152">Rozšíření typu mít také následující atributy:</span><span class="sxs-lookup"><span data-stu-id="246dc-152">Type extensions also have the following attributes:</span></span>

* <span data-ttu-id="246dc-153">Je možné rozšířit libovolný typ, který je přístupný.</span><span class="sxs-lookup"><span data-stu-id="246dc-153">Any type that can be accessed can be extended.</span></span>
* <span data-ttu-id="246dc-154">Můžete definovat rozšíření pro vnitřní objekty a jsou volitelné typ _jakékoli_ typ členu, ne jenom metody.</span><span class="sxs-lookup"><span data-stu-id="246dc-154">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="246dc-155">Vlastnosti rozšíření jsou tedy také je to možné, např.</span><span class="sxs-lookup"><span data-stu-id="246dc-155">So extension properties are also possible, for example.</span></span>
* <span data-ttu-id="246dc-156">`self-identifier` Token [syntaxe](type-extensions.md#syntax) představuje instanci typu vyvolání, stejně jako běžné členy.</span><span class="sxs-lookup"><span data-stu-id="246dc-156">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
* <span data-ttu-id="246dc-157">Rozšířené členy může být statická nebo členy instance.</span><span class="sxs-lookup"><span data-stu-id="246dc-157">Extended members can be static or instance members.</span></span>
* <span data-ttu-id="246dc-158">Proměnné typu na typ rozšíření musí odpovídat omezením deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="246dc-158">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="246dc-159">Pro rozšíření typu také existují následující omezení:</span><span class="sxs-lookup"><span data-stu-id="246dc-159">The following limitations also exist for type extensions:</span></span>

* <span data-ttu-id="246dc-160">Rozšíření typu nepodporují virtuální nebo abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="246dc-160">Type extensions do not support virtual or abstract methods.</span></span>
* <span data-ttu-id="246dc-161">Rozšíření typu nepodporují přepsání metody jako rozšíření.</span><span class="sxs-lookup"><span data-stu-id="246dc-161">Type extensions do not support override methods as augmentations.</span></span>
* <span data-ttu-id="246dc-162">Rozšíření typu nepodporují [statisticky vyřešených parametrů typu](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="246dc-162">Type extensions do not support [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>
* <span data-ttu-id="246dc-163">Volitelné rozšíření typu nepodporují konstruktory jako rozšíření.</span><span class="sxs-lookup"><span data-stu-id="246dc-163">Optional Type extensions do not support constructors as augmentations.</span></span>
* <span data-ttu-id="246dc-164">Rozšíření typu nelze definovat na [typ – zkratky](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="246dc-164">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
* <span data-ttu-id="246dc-165">Rozšíření typu nejsou platné pro `byref<'T>` (i když mohou být deklarovány).</span><span class="sxs-lookup"><span data-stu-id="246dc-165">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
* <span data-ttu-id="246dc-166">Rozšíření typu nejsou platné pro atributy (i když mohou být deklarovány).</span><span class="sxs-lookup"><span data-stu-id="246dc-166">Type extensions are not valid for attributes (though they can be declared).</span></span>
* <span data-ttu-id="246dc-167">Můžete definovat rozšíření, která přetížit jiné metody se stejným názvem, ale F# kompilátor dává přednost metody rozšíření, pokud je nejednoznačné volání.</span><span class="sxs-lookup"><span data-stu-id="246dc-167">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="246dc-168">Nakonec pokud existuje více rozšíření vnitřního typu pro jeden typ, všechny členy musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="246dc-168">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="246dc-169">Pro volitelná rozšíření typů členové v jiných typech rozšíření stejného typu mají stejné názvy.</span><span class="sxs-lookup"><span data-stu-id="246dc-169">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="246dc-170">K chybám nejednoznačnosti dojde pouze v případě, že kód klienta otevře dva různé obory, které definují stejné názvy členů.</span><span class="sxs-lookup"><span data-stu-id="246dc-170">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="246dc-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="246dc-171">See also</span></span>

- [<span data-ttu-id="246dc-172">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="246dc-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="246dc-173">Členové</span><span class="sxs-lookup"><span data-stu-id="246dc-173">Members</span></span>](members/index.md)
