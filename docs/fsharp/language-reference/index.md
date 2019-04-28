---
title: Referenční dokumentace jazyka F#
description: Najít F# jazykové funkce informace z tohoto odkazu na jazyk tokeny, koncepty, typy, výrazy a témata konstrukce podporované kompilátorem.
ms.date: 05/16/2016
ms.openlocfilehash: b70264b44b0820993cd77cb6c4f95a1547783174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666440"
---
# <a name="f-language-reference"></a>Referenční dokumentace jazyka F#

Tato část se odkaz na F# jazyk, programovací jazyk více paradigmaty cílit na rozhraní .NET. F# Jazyk podporuje funkční, objektově orientované a imperativní programovací modely.

## <a name="f-tokens"></a>F#Tokeny

V následující tabulce jsou uvedeny odkazy na témata, které poskytují klíčová slova, symboly a literály použít jako tokeny v F#.

|Název|Popis|
|-----|-----------|
|[Referenční dokumentace klíčových slov](keyword-reference.md)|Obsahuje odkazy na informace o všech F# klíčová slova jazyka.|
|[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)|Tabulka symbolů a operátorů, které se používají v F# jazyka.|
|[Literály](literals.md)|Popisuje syntaxi pro hodnoty literálu v F# a jak určit informace o typu F# literály.|

## <a name="f-language-concepts"></a>F#– Jazykové koncepce

V následující tabulce jsou uvedeny referenční témata, které jsou k dispozici, které popisují – jazykové koncepce.

|Název|Popis|
|-----|-----------|
|[Funkce](functions/index.md)|Funkce je základní jednotkou spuštění programu v jakémkoli programovacím jazyce. Stejně jako v jiných jazycích F# funkce s názvem, mohou mít parametry a argumenty vzít a má tělo. F#také podporuje konstrukce funkčního programování, jako je zpracování funkce jako hodnoty pomocí nepojmenované funkce ve výrazech, složení funkcí k vytvoření nové funkce, curryfikované funkce a implicitní definice funkce prostřednictvím částečnou použití argumentů funkce.|
|[Typy F#](fsharp-types.md)|Popisuje typy, které se používají v F# a jak F# jsou typy s názvem a popsané.|
|[Odvození typu](type-inference.md)|Popisuje, jak F# kompilátor odvodí typ hodnoty, proměnné, parametry a návratové hodnoty.|
|[Automatická generalizace](generics/automatic-generalization.md)|Popisuje obecné konstrukce v F#.|
|[Dědičnost](inheritance.md)|Popisuje dědičnosti, který slouží k modelování vztah "je a", nebo vytvoření podtypů v objektově orientované programování.|
|[Členové](members/index.md)|Popisuje členy F# typy objektů.|
|[Parametry a argumenty](Parameters-and-Arguments.md)|Popisuje podporu jazyka pro definování parametrů a předávání argumentů do funkce, metody a vlastnosti. Obsahuje informace o tom, jak předávání odkazem.|
|[Přetížení operátoru](operator-overloading.md)|Popisuje, jak přetěžovat aritmetické operátory ve třídě nebo typ záznamu a na globální úrovni.|
|[Přetypování a převody](casting-and-conversions.md)|Popisuje podporu pro převody typů v F#.|
|[Řízení přístupu](access-control.md)|Popisuje řízení přístupu v F#. Řízení přístupu znamená, že deklarace klientů, kteří budou moct použít některé prvky programu, jako jsou typy, metody, funkce a tak dále.|
|[Porovnávání vzorů](pattern-matching.md)|Popisuje vzory, které jsou pravidla pro transformování vstupních dat, které se používají v celém F# jazyk k extrakci dat porovnávání se vzorem, jak rozložit data na základní části nebo extrahovat informace z dat různými způsoby.|
|[Aktivní vzory](active-patterns.md)|Popisuje aktivní vzory. Aktivní vzorky umožňují definovat pojmenované oddíly, které rozdělit vstupní data. Aktivní vzory můžete použít k rozložení dat v podobě přizpůsobené pro každý oddíl.|
|[Kontrolní výrazy](assertions.md)|Popisuje `assert` výrazu, což je funkce ladění, který můžete použít k otestování výrazu. Po selhání v režimu ladění generuje kontrolní výraz dialogové okno chyby systému.|
|[Zpracování výjimek](exception-handling/index.md)|Obsahuje informace o podpoře v zpracování výjimek F# jazyka.|
|[Atributy](attributes.md)|Popisuje atributy, které umožňují metadata použije programovací konstrukce.|
|[Správa prostředků: Klíčové slovo `use`](resource-management-the-use-keyword.md)|Popisuje klíčová slova `use` a `using`, které řídí, inicializace a uvolnění prostředků|
|[namespaces](namespaces.md)|Popisuje obor názvů podporu v F#. Obor názvů umožňuje uspořádat kódu do související funkční oblasti tím, že jste se připojit k seskupení prvků programu název.|
|[Moduly](modules.md)|Popisuje moduly. F# Modulu je seskupení F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu. Kód v modulech seskupení udržet související kód společně a pomáhá zamezilo se konfliktům názvů ve svém programu.|
|[Deklarace importu: Klíčové slovo `open`](import-declarations-the-open-keyword.md)|Popisuje, jak `open` funguje. Deklarace importu Určuje modul nebo obor názvů, jehož prvky, můžete využít bez použití plně kvalifikovaného názvu.|
|[Signatury](signatures.md)|Popisuje podpisy a souborů signatur. Soubor s podpisem obsahuje informace o veřejných podpisů sadu F# programu prvky, jako jsou moduly, typy a obory názvů. Slouží k určení usnadnění tyto prvky programu.|
|[Dokumentace XML](xml-documentation.md)|Popisuje podporu pro generování soubory dokumentace pro komentáře dokumentace XML, označované také jako Trojitá lomítko komentáře. Můžete vytvářet z kódu komentářů v dokumentaci F# stejně jako u jiných jazycích rozhraní .NET.|
|[Podrobná syntaxe](verbose-syntax.md)|Popisuje syntaxi pro F# vytvoří, pokud není povolené nenáročném syntaxi. Podrobná syntaxe je indikován `#light "off"` direktiv v horní části souboru kódu.|

## <a name="f-types"></a>Typy F#

Následující tabulka obsahuje odkazy na témata k dispozici, které popisují typy podporovaných F# jazyka.

|Název|Popis|
|-----|-----------|
|[Hodnoty](values/index.md)|Popisuje hodnoty, které jsou neměnné množství, které mají konkrétní typ; hodnoty může být integrálního typu nebo plovoucí desetinnou čárkou, znaky nebo hodnoty text, seznamy, pořadí, pole, řazených kolekcí členů, rozlišovaná sjednocení, záznamy, typy tříd nebo funkce.|
|[Základní typy](basic-types.md)|Popisuje základní typy, které se používají v F# jazyka. Pro každý typ také poskytuje odpovídající typy .NET a minimální a maximální hodnoty.|
|[Typ jednotky](unit-type.md)|Popisuje `unit` typu, což je typ, který ukazuje na nepřítomnost určitou hodnotu; `unit` typ má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud neexistuje žádná hodnota nebo je potřeba.|
|[Řetězce](strings.md)|Popisuje řetězce v F#. `string` Typ představuje neměnné text jako posloupnost znaků Unicode. `string` je alias pro `System.String` v rozhraní .NET Framework.|
|[Řazené kolekce členů](tuples.md)|Popisuje řazených kolekcí členů, které představují seskupení nepojmenované ale seřazené hodnoty by mohly mít odlišné typy.|
|[Typy kolekcí F#](fsharp-collection-types.md)|Přehled F# funkční kolekci typů, včetně typů pro pole, seznamy, sekvence (seq), mapy a sady.|
|[Seznamy](lists.md)|Popisuje seznamy. V seznamu v F# je seřazený, neměnné řadu prvků všechny stejného typu.|
|[Možnosti](options.md)|Popisuje typ možnosti. Možnost v F# se používá, když hodnota může nebo nemusí existovat. Možnost má základní typ a udržují buď hodnotu daného typu nebo nemusí mít hodnotu.|
|[Sekvence](sequences.md)|Popisuje pořadí. Sekvence je logické řady elementů jednoho typu. Jednotlivé pořadí prvků se pouze vypočítávají podle potřeby, tak reprezentace může být nižší než počet literal element označuje.|
|[Pole](arrays.md)|Popisuje pole. Pole jsou pevné velikosti, založený na nule, proměnlivé pořadí po sobě následujících datových elementů, všechny stejného typu.|
|[Záznamy](records.md)|Popisuje záznamy. Záznamy představují jednoduchý agregace pojmenovaných hodnot, volitelně s členy.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje rozlišovaná sjednocení, která poskytuje podporu pro hodnoty, které může být jeden z mnoha pojmenovaných případů, každá má by mohly mít odlišné hodnoty a typy.|
|[Výčty](enumerations.md)|Popisuje výčty jsou pojmenované typy, které mají definovanou sadu hodnot. Můžete je použít místo literály aby byl kód čitelnější a udržovatelný.|
|[Referenční buňky](reference-cells.md)|Popisuje odkazové buňky, které jsou úložná místa, které umožňují vytvořit proměnlivé proměnné pomocí odkazové sémantiky.|
|[Zkratky typů](type-abbreviations.md)|Popisuje zkratky typů, které jsou alternativní názvy typů.|
|[Třídy](classes.md)|Popisuje třídy, které jsou typy, které představují objekty, které mohou mít vlastnosti, metody a události.|
|[Struktury](structures.md)|Popisuje struktur, které jsou typy compact objektů, které může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.|
|[Rozhraní](interfaces.md)|Popisuje rozhraní, které určují sadu souvisejících členů, které implementují jiné třídy.|
|[Abstraktní třídy](abstract-classes.md)|Popisuje abstraktní třídy, které jsou třídy, které ponechte některé nebo všechny členy neimplementované, takže může být poskytnuty implementace z odvozených tříd.|
|[Rozšíření typů](type-extensions.md)|Popisuje rozšíření typu, které umožňují přidat nové členy dříve definovaného typu objektu.|
|[Flexibilní typy](flexible-types.md)|Popisuje flexibilní typy. Poznámku flexibilní typu je zadán jako ukazatel toho, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s typem, kde kompatibility se určuje podle umístění v hierarchii objektově orientované třídy nebo rozhraní.|
|[Delegáti](delegates.md)|Popisuje delegáty, které představují volání funkce jako objekt.|
|[Měrné jednotky](units-of-measure.md)|Popisuje měrné jednotky. Hodnoty plovoucího bodu v F# mohou být přidruženy jednotky měření, které se obvykle používají k označení délku, svazek, hmotnost a tak dále.|
|[Zprostředkovatelé typů](../tutorials/type-providers/index.md)|Popisuje typ poskytuje a obsahuje odkazy na návody týkající se použití předdefinovaných poskytovatelů typů pro databáze aplikace access a webové služby.|

## <a name="f-expressions"></a>F#Výrazy

V následující tabulce jsou uvedeny témata, která popisují F# výrazy.

|Název|Popis|
|-----|-----------|
|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Popisuje `if...then...else` výraz, který běží jiné větve kódu a také vyhodnotí na jinou hodnotu v závislosti na logický výraz zadaný.|
|[Výrazy shody](match-expressions.md)|Popisuje `match` výraz, který poskytuje větvení ovládací prvek, který je založena na porovnávání výrazů sadu vzorů.|
|[Smyčky: `for...to` Výraz](loops-for-to-expression.md)|Popisuje `for...to` výraz, který se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.|
|[Smyčky: `for...in` Výraz](loops-for-in-expression.md)|Popisuje `for...in` výraz, uvozuje konstruktor, který se používá k iteraci přes odpovídá vzoru v vyčíslitelné kolekce například rozsahu – výraz, pořadí, seznam, pole nebo jiné konstrukce, která podporuje výčtu.|
|[Smyčky: `while...do` Výraz](loops-while-do-expression.md)|Popisuje `while...do` výraz, který se používá k provedení iterativní spuštění (opakování), když je zadaný testovací podmínka pravdivá.|
|[Objektové výrazy](object-expressions.md)|Popisuje objektové výrazy, které jsou výrazy, které vytvářejí nové instance typu dynamicky generovaný anonymní objekt, který je založen na existující základní typ, rozhraní nebo sady rozhraní.|
|[Výrazy Lazy](lazy-expressions.md)|Popisuje opožděné výrazy, které jsou výpočty, které není u nich vyhodnoceno okamžitě, ale místo toho se vyhodnocují při výsledek je skutečně potřeba.|
|[Výpočetní výrazy](computation-expressions.md)|Popisuje výrazech výpočtu v F#, které poskytují pomocí pohodlné syntaxe pro zápis výpočty, které mohou být seřazeny a kombinované pomocí řízení toku konstrukcí a vazby. Slouží k poskytování pomocí pohodlné syntaxe pro *monády*, funkční programovací funkce, která slouží ke správě dat, řízení a vedlejší efekty při funkční programy. Jeden typ výrazu výpočtu, asynchronního pracovního postupu, poskytuje podporu pro asynchronní a paralelní výpočty. Další informace najdete v tématu [asynchronní pracovní postupy](asynchronous-workflows.md).|
|[Asynchronní pracovní postupy](asynchronous-workflows.md)|Popisuje funkce jazyka, který umožňuje zapisovat, asynchronní kód tak, že blíží tak, jak je přirozeně zapíše synchronního kódu asynchronní pracovní postupy.|
|[Citace kódu](code-quotations.md)|Uvozovky kódu, funkci jazyka, která umožňuje generovat a pracovat s popisuje F# kódu výrazy prostřednictvím kódu programu.|
|[Výrazy dotazu](query-expressions.md)|Popisuje výrazy dotazů, funkci jazyka, který implementuje LINQ pro F# a umožní vám psát dotazy proti zdroji dat nebo vyčíslitelné kolekce.|

## <a name="compiler-supported-constructs"></a>Konstrukce podporované kompilátorem

V následující tabulce jsou uvedeny témata, která popisují speciální konstrukce podporované kompilátorem.

|Téma|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku F# kompilátoru.|
|[Direktivy kompilátoru](compiler-directives.md)|Popisuje směrnice procesoru a direktivy kompilátoru.|
|[Identifikátory zdrojového řádku, souboru a cesty](source-line-file-path-identifiers.md)|Popisuje identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__`, které jsou předdefinované hodnoty, které vám umožní přístup ke zdrojové řádek číslo, adresář a název souboru ve vašem kódu.|

## <a name="see-also"></a>Viz také:

- [Visual F#](../index.md)
