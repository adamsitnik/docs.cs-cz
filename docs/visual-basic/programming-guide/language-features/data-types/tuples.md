---
title: Řazené kolekce členů v Visual Basic
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: fdca36e47d0b1234a8964d7475354a726a61f085
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524575"
---
# <a name="tuples-visual-basic"></a>Řazené kolekce členů (Visual Basic)

Počínaje Visual Basic 2017 Visual Basic jazyk nabízí integrovanou podporu pro řazené kolekce členů, které usnadňují vytváření řazených kolekcí členů a přístup k prvkům řazených kolekcí členů. Řazená kolekce členů je odlehčená datová struktura, která má určitý počet a sekvenci hodnot. Při vytváření instance řazené kolekce členů definujte číslo a datový typ každé hodnoty (nebo element). Například 2-Tuple (nebo dvojice) má dva prvky. První může být `Boolean` hodnota, zatímco druhá je `String`. Vzhledem k tomu, že řazené kolekce členů usnadňují ukládání více hodnot do jediného objektu, jsou často používány jako jednoduchý způsob, jak vrátit více hodnot z metody.

> [!IMPORTANT]
> Podpora řazené kolekce členů vyžaduje typ <xref:System.ValueTuple>. Pokud není nainstalován .NET Framework 4,7, je nutné přidat balíček NuGet `System.ValueTuple`, který je k dispozici v galerii NuGet. Bez tohoto balíčku se může zobrazit chyba kompilace podobná "předdefinovaný typ ValueTuple (of,,,) není definován ani importován."

## <a name="instantiating-and-using-a-tuple"></a>Vytváření instancí a používání řazené kolekce členů

Vytvořte instanci řazené kolekce členů uzavřením hodnot oddělených čárkami a závorkou. Každá z těchto hodnot se pak stala polem řazené kolekce členů. Například následující kód definuje Troji (nebo 3-Tuple) s `Date` jako první hodnotu, `String` jako druhou a `Boolean` jako třetí.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Ve výchozím nastavení se název každého pole v rámci řazené kolekce členů skládá z řetězce `Item` společně s jednou pozicí pole v řazené kolekci členů. U této 3-řazené kolekce členů se pole `Date` `Item1`, `String` pole je `Item2` a `Boolean` pole je `Item3`. Následující příklad zobrazí hodnoty polí instance řazené kolekce členů v předchozím řádku kódu.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Pole Visual Basic řazené kolekce členů jsou pro čtení i zápis; Po vytvoření instance řazené kolekce členů můžete změnit její hodnoty. Následující příklad upraví dvě pole řazené kolekce členů vytvořená v předchozím příkladu a zobrazí výsledek.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Vytváření instancí a používání pojmenované řazené kolekce členů

Místo používání výchozích názvů pro pole řazené kolekce členů můžete vytvořit instanci *pojmenované řazené kolekce členů* přiřazením vlastních názvů prvkům řazené kolekce členů. K polím řazené kolekce členů lze následně přistupovat pomocí jejich přiřazených názvů *nebo* jejich výchozích názvů. Následující příklad vytvoří instanci stejné 3-řazené kolekce členů jako dříve, s tím rozdílem, že explicitně pojmenuje první pole `EventDate`, druhý `Name` a třetí `IsHoliday`. Pak zobrazí hodnoty polí, upraví je a zobrazí hodnoty polí znovu.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Odvozené názvy elementů řazené kolekce členů

Počínaje Visual Basic 15,3 Visual Basic mohou odvodit názvy elementů řazené kolekce členů; nemusíte je explicitně přiřazovat. Odvozené názvy řazených kolekcí členů jsou užitečné při inicializaci řazené kolekce členů ze sady proměnných a chcete, aby název elementu řazené kolekce členů byl stejný jako název proměnné.

Následující příklad vytvoří řazenou kolekci členů `stateInfo`, která obsahuje tři explicitně pojmenované elementy, `state`, `stateName` a `capital`. Všimněte si, že při pojmenovávání prvků příkaz inicializace řazené kolekce členů jednoduše přiřadí pojmenované prvky hodnoty identicky pojmenovaných proměnných.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]

Vzhledem k tomu, že prvky a proměnné mají stejný název, kompilátor Visual Basic může odvodit názvy polí, jak ukazuje následující příklad.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Chcete-li povolit odvozené názvy elementů řazené kolekce členů, je nutné definovat verzi Visual Basic kompilátoru pro použití v souboru projektu Visual Basic (\*. vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.3</LangVersion>
</PropertyGroup>
```

Číslo verze může být libovolná verze Visual Basic kompilátoru od 15,3. Namísto hardwarového kódování konkrétní verze kompilátoru můžete také zadat "nejnovější" jako hodnotu `LangVersion` ke kompilaci s nejnovější verzí Visual Basic kompilátoru nainstalovanou v systému.

Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../../../language-reference/configure-language-version.md).

V některých případech kompilátor Visual Basic nemůže odvodit název prvku řazené kolekce členů z názvu kandidáta a pole řazené kolekce členů může být odkazováno pouze pomocí jeho výchozího názvu, například `Item1`, `Item2` atd. Mezi ně patří:

- Kandidátský název je stejný jako název člena řazené kolekce členů, například `Item3`, `Rest` nebo `ToString`.

- Název kandidáta je duplikován v řazené kolekci členů.

Pokud se odvození názvu pole nepovede, Visual Basic negeneruje chybu kompilátoru, ani při běhu není vyvolána výjimka. Místo toho musí být pole řazené kolekce členů odkazována podle jejich předdefinovaných názvů, například `Item1` a `Item2`.

## <a name="tuples-versus-structures"></a>Řazené kolekce členů versus struktury

Visual Basic řazená kolekce členů je hodnotový typ, který je instancí jednoho z obecných typů **System. ValueTuple** . Například `holiday` řazené kolekce členů definované v předchozím příkladu je instance <xref:System.ValueTuple%603> struktury. Je navržený jako odlehčený kontejner pro data. Vzhledem k tomu, že řazená kolekce členů je snazší vytvořit objekt s více datovými položkami, chybí některé funkce, které může mít vlastní struktura. Zde jsou některé z nich:

- Vlastní členové. Nemůžete definovat vlastní vlastnosti, metody nebo události pro řazenou kolekci členů.

- Export. Nemůžete ověřit pole data přiřazená.

- Neměnnosti. Řazené kolekce členů Visual Basic jsou proměnlivé. Na rozdíl od vlastní struktury vám umožní řídit, jestli je instance proměnlivá nebo neměnná.

Pokud jsou vlastní členové, ověřování vlastností a polí nebo neměnnosti důležité, měli byste použít příkaz [struktura](../../../language-reference/statements/structure-statement.md) Visual Basic k definování vlastního typu hodnoty.

Visual Basic řazené kolekce členů dědí členy svého typu **ValueTuple** . Kromě polí patří mezi ně tyto metody:

| Člen | Popis |
| ---|---|
| CompareTo | Porovná aktuální řazenou kolekci členů s jinou řazenou kolekci členů se stejným počtem prvků. |
| Rovná | Určuje, zda je aktuální řazená kolekce členů rovna jiné řazené kolekci členů nebo objektu. |
| GetHashCode | Vypočítá kód hash aktuální instance. |
| Metodu | Vrátí řetězcovou reprezentaci této řazené kolekce členů, která převezme `(Item1, Item2...)` formuláře, kde `Item1` a `Item2` reprezentují hodnoty polí řazené kolekce členů. |

Kromě toho typy **ValueTuple** implementují rozhraní <xref:System.Collections.IStructuralComparable> a <xref:System.Collections.IStructuralEquatable>, která umožňují definovat porovnávače zákazníků.

## <a name="assignment-and-tuples"></a>Přiřazení a řazené kolekce členů

Visual Basic podporuje přiřazení mezi typy řazené kolekce členů, které mají stejný počet polí. Typy polí lze převést, pokud je splněna jedna z následujících hodnot:

- Zdrojové a cílové pole je stejného typu.

- Je definovaný rozšiřující (nebo implicitní) převod zdrojového typu na cílový typ.

- `Option Strict` je `On` a je definována úzká (nebo explicitní) konverze zdrojového typu na cílový typ. Tento převod může vyvolat výjimku, pokud je zdrojová hodnota mimo rozsah cílového typu.

Jiné převody se nepovažují za přiřazení. Pojďme se podívat na typy přiřazení, která jsou povolená mezi typy řazené kolekce členů.

Vezměte v úvahu tyto proměnné, které se používají v následujících příkladech:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

První dvě proměnné, `unnamed` a `anonymous`, nemají pro pole k dispozici sémantické názvy. Jejich názvy polí jsou výchozí `Item1` a `Item2`. Poslední dvě proměnné `named` a `differentName` mají sémantické názvy polí. Všimněte si, že tyto dvě řazené kolekce členů mají pro pole různé názvy.

Všechny čtyři tyto řazené kolekce členů mají stejný počet polí (označované jako "aritou") a typy těchto polí jsou identické. Proto všechna tato přiřazení fungují:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Všimněte si, že názvy řazených kolekcí členů nejsou přiřazeny. Hodnoty polí jsou přiřazeny podle pořadí polí v řazené kolekci členů.

Nakonec si všimněte, že je možné přiřadit `named` řazené kolekce členů k `conversion` řazené kolekci členů, i když je prvním polem `named` `Integer` a prvním polem `conversion` je `Long`. Toto přiřazení je úspěšné, protože převod `Integer` na `Long` je rozšiřující převod.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Řazené kolekce členů s různými počty polí nelze přiřadit:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Řazené kolekce členů jako návratové hodnoty metody

Metoda může vracet pouze jednu hodnotu. Často se ale jako volání metody vrací více hodnot. Toto omezení můžete vyřešit několika způsoby:

- Můžete vytvořit vlastní třídu nebo strukturu, jejíž vlastnosti nebo pole reprezentují hodnoty vrácené metodou. Proto je těžké řešení; vyžaduje, abyste definovali vlastní typ, jehož jediným účelem je načíst hodnoty z volání metody.

- Můžete vrátit jednu hodnotu z metody a vrátit zbývající hodnoty jejich předáním odkazem na metodu. To zahrnuje režijní náklady na vytvoření instance proměnné a rizika nechtěně přepíší hodnotu proměnné, kterou předáte odkazem.

- Můžete použít řazenou kolekci členů, která poskytuje zjednodušené řešení pro načítání více návratových hodnot.

Například metody **TryParse** v rozhraní .net vracejí `Boolean` hodnotu, která označuje, zda byla operace analýzy úspěšná. Výsledek operace analýzy je vrácen v proměnné předané pomocí odkazu na metodu. V normálním případě volání metody analýzy, jako je například <xref:System.Int32.TryParse%2A?displayProperty=nameWithType>, vypadá takto:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Pokud zabalíme volání metody <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> v naší vlastní metodě, můžeme vrátit řazenou kolekci členů z operace analýzy. V následujícím příkladu `NumericLibrary.ParseInteger` volá metodu <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> a vrací pojmenované řazené kolekce členů se dvěma prvky.

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Pak můžete zavolat metodu s kódem podobným následujícímu:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic řazené kolekce členů a řazené kolekce členů v .NET Framework

Visual Basic řazená kolekce členů je instancí jednoho z obecných typů **System. ValueTuple** , které byly představeny v .NET Framework 4,7. .NET Framework také obsahuje sadu obecných tříd **System. Tuple** . Tyto třídy se však liší od Visual Basicch řazených kolekcí členů a obecných typů **System. ValueTuple** mnoha různými způsoby:

- Prvky tříd **řazené kolekce členů** jsou vlastnosti s názvem `Item1`, `Item2` a tak dále. V Visual Basic řazené kolekce členů a typy **ValueTuple** jsou prvky řazené kolekce členů pole.

- K prvkům instance **řazené kolekce členů** nebo instanci **ValueTuple** nelze přiřadit smysluplné názvy. Visual Basic umožňuje přiřadit názvy, které komunikují význam polí.

- Vlastnosti instance **řazené kolekce členů** jsou jen pro čtení; řazené kolekce členů jsou neměnné. V Visual Basic řazené kolekce členů a typy **ValueTuple** jsou pole řazené kolekce členů i pro čtení i zápis; řazené kolekce členů jsou proměnlivé.

- Obecné typy **řazené kolekce členů** jsou odkazové typy. Použití těchto typů **řazené kolekce členů** znamená přidělení objektů. U aktivních cest to může mít měřitelný dopad na výkon vaší aplikace. Visual Basic řazené kolekce členů a typy **ValueTuple** jsou typy hodnot.

Metody rozšíření ve třídě <xref:System.TupleExtensions> usnadňují konverzi mezi Visual Basic řazenými kolekcemi členů a objekty **řazené kolekce členů** .NET. Metoda **ToTuple** převádí Visual Basic řazené kolekce členů na objekt .NET **řazené** kolekce členů a metoda **ToValueTuple** převede objekt **řazené kolekce členů** .NET na Visual Basic řazené kolekce členů.

Následující příklad vytvoří řazenou kolekci členů, převede ji na objekt **řazené kolekce členů** .NET a převede ji zpět na Visual Basic řazené kolekce členů. Příklad následně Porovná tuto řazenou kolekci členů s původní verzí, aby se zajistilo, že jsou stejné.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](index.md)
