---
title: F#pravidla formátování kódu
description: Přečtěte si pokyny pro formátování F# kódu.
ms.date: 11/26/2018
ms.openlocfilehash: e8e0af2ebffd0e2f3720896bf710961afa11e7bd
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396822"
---
# <a name="f-code-formatting-guidelines"></a>F#pravidla formátování kódu

Tento článek nabízí pokyny k formátování kódu tak, aby vaše F# kód je:

* Obecně zobrazit jako čitelnější
* Je v souladu s konvencí použil(a) formátování nástroje v sadě Visual Studio a ostatní editory
* Podobně jako další kód online

Tyto pokyny jsou založeny na [komplexní pokyny k F# konvence formátování](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) podle [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Obecná pravidla pro odsazení

F#ve výchozím nastavení používá významných mezer. Následující pokyny jsou určeny a přidal se návod, jak některé běžné problémy, které to může často znamenat výrazný přehlednější.

### <a name="using-spaces"></a>Použití prostorů

Když odsazení se vyžaduje, je nutné použít prostory, ne karty. Vyžaduje se alespoň jedna mezera. Vaše organizace může vytvořit kódování standardy, chcete-li určit počet mezer pro odsazení; dvě, tři nebo čtyři mezery odsazení na všech úrovních, kde dochází k odsazení je obvyklé.

**Doporučujeme 4 mezery za odsazení.**

Ale nutné dodat, odsazení programů, což je subjektivní. Variace se OK, ale je první pravidlo, měli byste postupovat podle *konzistence odsazení*. Zvolte obecně přijímané styl odsazení a systematicky používat v rámci vašeho základu kódu.

## <a name="formatting-white-space"></a>Formátování prázdných znaků

F#rozlišuje prázdné znaky. I když většina sémantiku než prázdné znaky jsou předmětem správné odsazení, existují některé věci k uvážení.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Formátování operátory v aritmetických výrazech

Vždy používejte mezery kolem binárních aritmetických výrazů:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Unární `-` operátory by měly mít vždy hodnotu jsou negace bezprostředně následuje po:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Prázdný znak po přidání `-` operátor může vést k záměně pro ostatní uživatele.

Stručně řečeno je potřeba vždy:

* Před a za binární operátory s prázdné znaky
* Nikdy nemůžete mít prázdný znak za unární operátor

Obecné zásady binární aritmetického operátoru je obzvláště důležité. Selhání před a za binární soubor `-` operátor v kombinaci s určitým možnostmi formátování, může vést k interpretaci jako unární `-`.

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Definice vlastního operátoru prázdnými znaky před a za

Vždy použijte prázdné znaky před a za definici operátoru:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Pro všechny vlastní operátor, který začíná `*`, budete muset přidat mezery na začátku definice, aby se zabránilo nejednoznačnosti kompilátoru. Z toho důvodu se doporučuje, jednoduše uzavřete definice všechny operátory s jeden prázdný znak.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Funkce šipky parametr prázdnými znaky před a za

Při definování podpis funkce, použijte prázdný prostor kolem `->` symbolů:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a>Formátování prázdných řádků

* Samostatné nejvyšší úrovně funkce a třídy definice se dvěma prázdné řádky.
* Definice metody uvnitř třídy jsou odděleny jeden prázdný řádek.
* Prázdné řádky může použít k oddělení skupin souvisejících funkcí (střídmě). Můžete vynechat prázdné řádky mezi spoustu související one-liners (například sadu fiktivní implementace).
* Pomocí prázdné řádky ve službě functions opatrně, označte logické oddíly.

## <a name="formatting-comments"></a>Formátování komentáře

Obecně přednost více komentářů dvěma lomítky přes ML – vizuální styl blok komentáře.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Vložené komentáře by měl velké první písmeno první písmeno.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Zásady vytváření názvů

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Hodnoty vázané na třídu, vázané na výrazu a vzor vázané a funkcí pomocí camelCase

Je běžné a přijatou F# stylu camelCase používat pro všechny názvy vázaný jako lokální proměnné nebo v porovnávání vzorů a definice funkce.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Místně vázaných funkcí v třídách použít i pro camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Pro veřejné funkce vázané na modul pomocí camelCase

Pokud modul vázané funkce je součástí veřejného rozhraní API, měla by používat camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Pomocí camelCase pro interní a privátní hodnoty vázané na modul a funkce

Pomocí camelCase pro soukromé hodnoty vázané na modul, včetně následujících:

* Funkce ad hoc ve skriptech

* Hodnoty, které tvoří vnitřní implementace modulem nebo typem.

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Pro parametry pomocí camelCase

Všechny parametry používali camelCase v souladu s zásady vytváření názvů .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Pro moduly pomocí PascalCase

Všechny moduly (nejvyšší úrovně, interní, privátní, vnořené) používejte PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Pomocí PascalCase u deklarace typu, členů a popisků

Třídy, rozhraní, struktury, výčty, delegáti, záznamů a rozlišovaná sjednocení by měl název pomocí PascalCase. Členy v rámci typů a popisků záznamů a rozlišovaná sjednocení také používali PascalCase.

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Pro konstruktory, které jsou přirozené pro .NET pomocí PascalCase

Obory názvů, výjimky, události a projekt /`.dll` názvy mělo používat taky pomocí PascalCase. Nejen tím neodstraní, ale využití z jiných jazyků .NET působit přirozeně více uživatelům, je také v souladu s konvence pojmenování .NET, které budete pravděpodobně dojde k.

### <a name="avoid-underscores-in-names"></a>Vyhněte se podtržítka v názvech

V minulosti některé F# knihovny použili v názvech podtržítka. Ale to je přijat už široce, částečně proto, že je v konfliktu s zásady vytváření názvů .NET. Nicméně některé F# programátoři používají podtržítka silně, částečně z historických důvodů a odolnosti proti chybám a ohledu je důležité. Nezapomínejte, že styl je často disliked jinými uživateli, kteří rozhodnout o tom, jestli ji používat.

Některé výjimky zahrnuje spolupráce s nativními komponentami, kde jsou velmi běžné podtržítka.

### <a name="use-standard-f-operators"></a>Pomocí standardních F# operátory

Následující operátory jsou definovány v F# standardní knihovny a musí být použity místo definování ekvivalenty. Jak je obvykle, aby byl kód čitelnější a idiomatickou, doporučuje se použití těchto operátorů. Vývojáři a má zázemí ve OCaml nebo jiných funkcionálním programovacím jazyce může být na různých idiomy zvyklí. Následující seznam shrnuje doporučené F# operátory.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Použijte předponu syntaxi pro obecné typy (`Foo<T>`) před syntaxe přípony (`T Foo`)

F#dědí obě přípony ML styl pojmenování obecných typů (například `int list`) stejně jako předpona .NET stylu (například `list<int>`). Preferovat stylu .NET, s výjimkou čtyři konkrétní typy:

1. Pro F# seznamy, použijte příponový tvar: `int list` spíše než `list<int>`.
2. Pro F# možnosti použít příponový tvar: `int option` spíše než `option<int>`.
3. Pro F# pole, použijte syntaxi název `int[]` spíše než `int array` nebo `array<int>`.
4. Odkazové buňky pomocí `int ref` spíše než `ref<int>` nebo `Ref<int>`.

Pro všechny ostatní typy použijte prefixová podoba.

## <a name="formatting-tuples"></a>Formátování řazené kolekce členů

Vytvoření instance řazené kolekce členů musí být v závorce a oddělovací čárky v rámci by měl následovat jednu mezeru, například: `(1, 2)`, `(x, y, z)`.

Běžně přijetím vynechejte závorky v porovnávání vzorů řazených kolekcí členů:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a>Formátování rozlišované deklarace sjednocení

Odsadit `|` v definici typu 4 mezerami:

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>Formátování rozlišovaná sjednocení

Instance rozlišovaná sjednocení, které rozdělit mezi několik řádků by měla poskytnout dat obsažených nový obor s odsazením:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Pravá závorka může být také na nový řádek:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Formátování záznam deklarace

Odsadit `{` v typu definice 4 mezery a spustit v seznamu polí na stejný řádek:

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
// Unusual in F#
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    }
```

Uvedení na nový řádek a pravou token na nový řádek levou token je preferrable, pokud deklarujete implementace rozhraní nebo členy v záznamu:

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
type MyRecord =
    {
        SomeField : int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Formátování záznamů

Krátký záznamy je možné psát v jednom řádku:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Záznamy, které jsou delší používali nové řádky popisků:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Uvedení otevírání token na nový řádek, obsah s kartami více než jeden obor a pravou token na nový řádek je preferrable, pokud jste:

* Záznamy pohyb v kódu s obory odlišné odsazení
* Přesměrujete do funkce

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }
    
type MyRecord =
    {
        SomeField : int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

Stejná pravidla platí i pro seznam a pole prvků.

## <a name="formatting-lists-and-arrays"></a>Formátování seznamy a pole

Zápis `x :: l` s mezery kolem `::` – operátor (`::` je operátor vpony, proto obklopené mezerami).

Seznam a pole deklarovaná na jednom řádku by měly mít mezera za levou závorku a před pravou hranatou závorku:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Používejte vždy alespoň jednu mezeru mezi dva odlišné operátory podobném složenou závorku. Například, ponechte mezeru mezi `[` a `{`.

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

Stejné pravidlo platí pro seznamy a pole řazených kolekcí členů.

Seznamy a pole, která se rozdělit mezi několik řádků postupujte stejně jako záznamy podobné pravidlo:

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

A stejně jako u záznamů, deklarace otevírací a uzavírací hranaté závorce na vlastním řádku vám usnadní přesunutí kódu kolem a zřetězení příkazů do funkcí.

## <a name="formatting-if-expressions"></a>Formátování if výrazy

Odsazení podmíněné výrazy závisí na velikosti výrazy, které společně tvoří. Pokud `cond`, `e1` a `e2` jsou krátký, napište jednoduše na jednom řádku:

```fsharp
if cond then e1 else e2
```

Pokud `cond`, `e1` nebo `e2` delší dobu, ale ne více řádky:

```fsharp
if cond
then e1
else e2
```

Pokud je některý z výrazů více řádky:

```fsharp
if cond then
    e1
else
    e2
```

Více podmíněné výrazy s `elif` a `else` odsazeny ve stejném oboru jako `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Odpovídající vzor konstrukce

Použití `|` pro každou klauzuli shoda s žádné odsazení. Pokud výraz je krátký, můžete použít jeden řádek, pokud každý dílčí výraz je také jednoduchý.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Výraz na pravé straně porovnávání vzorů šipky je příliš velká, tento soubor přesune do následujícího řádku, odsazený jeden krok z `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Vzorovou shodu anonymní funkcí, které se spouští podle `function`, obecně by neměl příliš daleko odsazení. Například následující odsazení jeden rozsah je v pořádku:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Porovnávání vzorů v funkce určené `let` nebo `let rec` po spuštění by měl být odsazený 4 mezer `let`i v případě `function` – klíčové slovo se používá:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nedoporučujeme zarovnání šipky.

## <a name="formatting-trywith-expressions"></a>Formátování try / with výrazy

Vzorec pro porovnávání na typ výjimky by měly odsazena na stejné úrovni jako `with`.

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>Formátování aplikace parametr – funkce

Obecně platí většina aplikací parametr funkce se provádí na stejném řádku.

Pokud budete chtít použít parametry pro funkci na novém řádku, odsazení je jeden obor.

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

Podle stejných pravidel platí pro výrazy lambda jako argumenty funkce. Pokud hlavní část výrazu lambda, text může mít jiný řádek odsazeny o jeden obor

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

Nicméně pokud hlavní část výrazu lambda je více než jeden řádek, vezměte v úvahu řešení ho do samostatné funkce a nenechat konstrukci Víceřádkový použít jako jediný argument pro funkci.

### <a name="formatting-infix-operators"></a>Formátování infixové operátory

Samostatné operátory mezerami. Ze zřejmých výjimky z tohoto pravidla jsou `!` a `.` operátory.

Výrazy vpony je OK lineup na stejný sloupec:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formátování operátorů kanálů

Kanál `|>` operátory by měly patřit pod pracují na výrazy.

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>Formátovací moduly

Kód v místním modulu musí odsazený relativně k modulu, ale neměli odsazeny kódu v nejvyšší úrovni modulu. Prvky Namespace, není potřeba odsazeny.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Formátování objektové výrazy a rozhraní

Objektové výrazy a rozhraní zarovnání stejným způsobem s `member` se odsazena po 4 mezer.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formátování prázdných ve výrazech

Vyhněte se nadbytečné prázdné místo v F# výrazy.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Pojmenované argumenty neměli také místa okolo `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Atributy formátování

[Atributy](../language-reference/attributes.md) jsou umístěny nad konstrukce:

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a>Formátování atributy pro parametry

Atributy mohou být také míst na parametry. V takovém případě umístěte klikněte na stejném řádku jako parametr a před názvem:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Formátování více atributů

Při více atributy jsou použity konstrukce, která se nejedná o parametr, by měla být umístěna tak, že je jeden atribut na řádek:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Při použití parametru, musí být na stejném řádku a oddělené `;` oddělovač.

## <a name="formatting-literals"></a>Formátování literály

[F#literály](../language-reference/literals.md) pomocí `Literal` atribut by měl by měl umístit atribut na samostatném řádku a pomocí camelCase pojmenování:

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

Předejde atribut na stejný řádek jako hodnotu.
