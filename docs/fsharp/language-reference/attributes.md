---
title: Atributy
description: Zjistěte, jak F# atributy povolit programovací konstrukce, které se použije k metadatům.
ms.date: 05/16/2016
ms.openlocfilehash: 34223523efbb3bd89bb73f35fac3dfd8113d8611
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611839"
---
# <a name="attributes"></a><span data-ttu-id="8eafc-103">Atributy</span><span class="sxs-lookup"><span data-stu-id="8eafc-103">Attributes</span></span>

<span data-ttu-id="8eafc-104">Atributy umožňují metadata použije programovací konstrukce.</span><span class="sxs-lookup"><span data-stu-id="8eafc-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="8eafc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8eafc-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="8eafc-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8eafc-106">Remarks</span></span>

<span data-ttu-id="8eafc-107">V předchozí syntaxi *cílové* je nepovinný a pokud jsou k dispozici, určuje typ entity program, který platí atribut pro.</span><span class="sxs-lookup"><span data-stu-id="8eafc-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="8eafc-108">Platné hodnoty pro *cílové* jsou uvedené v tabulce, která se zobrazí později v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="8eafc-109">*Název atributu* odkazuje na název (může být kvalifikován s obory názvů) platný atribut typu, s nebo bez přípony `Attribute` , která se obvykle používá v názvech typ atributu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="8eafc-110">Například typ `ObsoleteAttribute` lze zkrátit jenom `Obsolete` v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="8eafc-111">*Argumenty* argumenty konstruktoru pro typ atributu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="8eafc-112">Pokud atribut nemá výchozí konstruktor, lze vynechat seznam argumentů a závorky.</span><span class="sxs-lookup"><span data-stu-id="8eafc-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="8eafc-113">Atributy podpory poziční argumenty a pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="8eafc-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="8eafc-114">*Poziční argumenty* jsou argumenty, které se používají v pořadí, v jakém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="8eafc-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="8eafc-115">Pojmenované argumenty je možné, pokud má atribut veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8eafc-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="8eafc-116">Můžete nastavit tyto pomocí následující syntaxe v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="8eafc-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="8eafc-117">Inicializace taková vlastnost může být v libovolném pořadí, ale musí postupovat žádné poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="8eafc-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="8eafc-118">Tady je příklad, který používá poziční argumenty a inicializací vlastností atributu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="8eafc-119">V tomto příkladu je atribut `DllImportAttribute`, zde používá ve zkráceném tvaru.</span><span class="sxs-lookup"><span data-stu-id="8eafc-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="8eafc-120">První argument je poziční parametr a druhý je vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8eafc-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="8eafc-121">Atributy jsou .NET programovací konstrukce, která umožňuje označované jako objekt *atribut* má být přidružena k typu nebo jiný prvek programu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="8eafc-122">Ovládací prvek programu ke které se použije atribut se označuje jako *cíl atributu*.</span><span class="sxs-lookup"><span data-stu-id="8eafc-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="8eafc-123">Atribut obvykle obsahuje metadata o cíli.</span><span class="sxs-lookup"><span data-stu-id="8eafc-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="8eafc-124">V tomto kontextu může být metadata žádná data o typ jiný než jeho polí a členy.</span><span class="sxs-lookup"><span data-stu-id="8eafc-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="8eafc-125">Atributy v F# můžete použít pro následující programovací konstrukce: funkce, metody, sestavení, modulů, typů (tříd, záznamy, struktury, rozhraní, delegátů, výčty, sjednocení a tak dále), konstruktory, vlastnosti, pole, parametry, zadejte parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8eafc-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="8eafc-126">Atributy nejsou povolené v `let` vazby uvnitř třídy, výrazy nebo výrazy pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="8eafc-127">Obvykle deklarace atributu se zobrazí přímo před deklarací cíl atributu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="8eafc-128">Více atribut deklarace je možné společně, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="8eafc-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="8eafc-129">Atributy můžete dotazovat v době běhu pomocí reflexe .NET.</span><span class="sxs-lookup"><span data-stu-id="8eafc-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="8eafc-130">Je možné deklarovat několik atributů jednotlivě, stejně jako v předcházejícím příkladu, nebo je lze deklarovat v jednu sadu závorek je-li použít středník oddělit jednotlivé atributy a konstruktory, jak je znázorněno zde.</span><span class="sxs-lookup"><span data-stu-id="8eafc-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="8eafc-131">Zahrnout obvyklých atributy `Obsolete` atribut atributy pro požadavky na zabezpečení atributů pro podporu modelu COM, atributy, které se týkají vlastnictví kódu a atributy určující, zda typ lze serializovat.</span><span class="sxs-lookup"><span data-stu-id="8eafc-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="8eafc-132">Následující příklad ukazuje použití `Obsolete` atribut.</span><span class="sxs-lookup"><span data-stu-id="8eafc-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="8eafc-133">Pro atribut cíle `assembly` a `module`, použít atributy k nejvyšší úrovni `do` vazby v sestavení.</span><span class="sxs-lookup"><span data-stu-id="8eafc-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="8eafc-134">Může obsahovat slovo `assembly` nebo `module` v deklaraci atributu následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="8eafc-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="8eafc-135">Pokud vynecháte cíl atributu pro atribut použitý k `do` vazby, F# kompilátor se pokusí určit atribut target, to dává smysl pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="8eafc-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="8eafc-136">Mnoho atribut třídy mají atribut typu `System.AttributeUsageAttribute` , který obsahuje informace o možných cíle pro tento atribut nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="8eafc-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="8eafc-137">Pokud `System.AttributeUsageAttribute` naznačuje, že atribut podporuje funkce jako cíle, chcete-li použít hlavní vstupní bod programu se používá atribut.</span><span class="sxs-lookup"><span data-stu-id="8eafc-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="8eafc-138">Pokud `System.AttributeUsageAttribute` naznačuje, že atribut podporuje sestavení jako cíle, kompilátor přijímá atribut, který chcete použít k sestavení.</span><span class="sxs-lookup"><span data-stu-id="8eafc-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="8eafc-139">Většina atributy se nevztahují na funkce a sestavení, ale v případech, ve kterém se dělají, atribut věnovat platí pro hlavní funkce programu.</span><span class="sxs-lookup"><span data-stu-id="8eafc-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="8eafc-140">Pokud cílový atribut je explicitně zadán, je atribut použit na zadané cílové.</span><span class="sxs-lookup"><span data-stu-id="8eafc-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="8eafc-141">I když obvykle nepotřebujete zadat atribut cílit explicitně, platné hodnoty pro *cílové* v atributu jsou uvedeny v následující tabulce, spolu s příkladem použití.</span><span class="sxs-lookup"><span data-stu-id="8eafc-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="8eafc-142">Cíl atributu</span><span class="sxs-lookup"><span data-stu-id="8eafc-142">Attribute target</span></span></td>
    <th><span data-ttu-id="8eafc-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="8eafc-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8eafc-144">sestavení</span><span class="sxs-lookup"><span data-stu-id="8eafc-144">assembly</span></span></td>
    <td><span data-ttu-id="8eafc-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="8eafc-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8eafc-146">return</span><span class="sxs-lookup"><span data-stu-id="8eafc-146">return</span></span></td>
    <td><span data-ttu-id="8eafc-147">"umožnit function1 x: [<return: Obsolete>] int = x + 1</span><span class="sxs-lookup"><span data-stu-id="8eafc-147">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8eafc-148">pole</span><span class="sxs-lookup"><span data-stu-id="8eafc-148">field</span></span></td>
    <td><span data-ttu-id="8eafc-149">"[<field: DefaultValue>] val mutable x: int.</span><span class="sxs-lookup"><span data-stu-id="8eafc-149">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8eafc-150">property</span><span class="sxs-lookup"><span data-stu-id="8eafc-150">property</span></span></td>
    <td><span data-ttu-id="8eafc-151">"[<property: Obsolete>] to. MyProperty = x.</span><span class="sxs-lookup"><span data-stu-id="8eafc-151">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8eafc-152">Param</span><span class="sxs-lookup"><span data-stu-id="8eafc-152">param</span></span></td>
    <td><span data-ttu-id="8eafc-153">"člen to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10</span><span class="sxs-lookup"><span data-stu-id="8eafc-153">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8eafc-154">– typ</span><span class="sxs-lookup"><span data-stu-id="8eafc-154">type</span></span></td>
    <td>

        ```
        [<type: StructLayout(Sequential)>] 
        type MyStruct = 
        struct 
        x : byte
        y : int
        end
        ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8eafc-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8eafc-155">See also</span></span>

- [<span data-ttu-id="8eafc-156">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="8eafc-156">F# Language Reference</span></span>](index.md)