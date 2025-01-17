---
title: Prozkoumejte kód pomocí nástroje Roslyn syntax Vizualizér v aplikaci Visual Studio
description: Vizualizér syntaxe poskytuje vizuální nástroj k prozkoumávání modelů, které sada SDK .NET Compiler Platform generuje pro kód.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: fa3b4fdbb8d573805119e13e8aa93f156c4111f9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972018"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Prozkoumejte kód pomocí nástroje Roslyn syntax Vizualizér v aplikaci Visual Studio

Tento článek poskytuje přehled nástroje Syntax Visualizer, který se dodává jako součást sady SDK .NET Compiler Platform ("Roslyn"). Syntax Visualizer je okno nástroje, které vám pomůže zkontrolovat a prozkoumat strom syntaxe. Je to základní nástroj pro pochopení modelů kódu, který chcete analyzovat. Je to také podpora ladění při vývoji vlastních aplikací pomocí sady .NET Compiler Platform ("Roslyn") SDK. Při vytváření prvních analyzátorů otevřete tento nástroj. Vizualizér vám pomůže pochopit modely používané rozhraními API. Můžete také použít nástroje, jako je [SharpLab](https://sharplab.io) nebo [LINQPad](https://www.linqpad.net/) , ke kontrole kódu a pochopení stromů syntaxe.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Seznamte se s koncepty použitými v sadě .NET Compiler Platform SDK v článku [Přehled](compiler-api-model.md) . Poskytuje Úvod ke stromům syntaxe, uzlem, tokenům a minihry.

## <a name="syntax-visualizer"></a>Syntax Visualizer

**Syntax visualizer** umožňuje kontrolu stromu syntaxe pro soubor kódu C# nebo v aktuálním aktivním editoru v rámci integrovaného vývojového prostředí sady Visual Studio. Vizualizér můžete spustit kliknutím na **Zobrazit** > **ostatní** > **syntax visualizer**Windows.  Můžete také použít panel nástrojů **snadného spuštění** v pravém horním rohu. Zadejte "syntax" a příkaz pro otevření **syntax visualizer** by měl být zobrazen.

Tento příkaz otevře Syntax Visualizer jako plovoucí okno nástrojů. Pokud nemáte otevřené okno editoru kódu, je zobrazení prázdné, jak je znázorněno na následujícím obrázku. 

![Okno nástroje Syntax Visualizer](media/syntax-visualizer/syntax-visualizer.png)

Ukotvěte toto okno nástroje na vhodné místo v rámci sady Visual Studio, například na levou stranu. Vizualizér zobrazuje informace o aktuálním souboru kódu.

Vytvořte nový projekt pomocí příkazu **soubor** > **Nový projekt** . Můžete vytvořit buď VB, nebo C# projekt. Když aplikace Visual Studio otevře soubor hlavního kódu pro tento projekt, Vizualizér zobrazí pro něj strom syntaxe. Můžete otevřít libovolný existující C# soubor/VB v této instanci sady Visual Studio a Vizualizér zobrazí strom syntaxe tohoto souboru. Pokud máte v aplikaci Visual Studio otevřeno více souborů kódu, Vizualizér zobrazí strom syntaxe pro aktuálně aktivní soubor kódu (soubor kódu, který má fokus klávesnice).

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Vizualizace stromu C# syntaxe](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
![Vizualizace stromu syntaxe VB](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak je znázorněno na předchozích obrázcích, okno nástroje Vizualizér zobrazí strom syntaxe v horní části a mřížku vlastností v dolní části. V mřížce vlastností se zobrazují vlastnosti položky, která je aktuálně vybrána ve stromové struktuře, včetně *typu* .NET a *druhu* (prvkem syntaxkind) položky.

Stromy syntaxe tvoří tři typy položek – *uzly*, *tokeny*a *minihry*. Další informace o těchto typech si můžete přečíst v článku věnovaném [práci se syntaxí](work-with-syntax.md) . Položky každého typu jsou reprezentovány pomocí jiné barvy. Kliknutím na tlačítko legenda zobrazíte přehled použitých barev.

Každá položka ve stromové struktuře také zobrazuje vlastní **Rozsah**. **Rozsah** je indexy (počáteční a koncové umístění) daného uzlu v textovém souboru.  V předchozím C# příkladu má vybraný token "UsingKeyword [0.. 5)" **Rozsah** , který je pět znaků široká, [0.. 5). Notace "[..)" znamená, že počáteční index je součástí rozsahu, ale koncový index není.

Existují dva způsoby, jak procházet stromovou strukturu:

* Rozbalte nebo klikněte na položky ve stromové struktuře. Vizualizér automaticky vybere text odpovídající rozsahu této položky v editoru kódu.
* V editoru kódu klikněte nebo vyberte text. Pokud v předchozím příkladu VB vyberete řádek obsahující "Module Module1" v editoru kódu, Vizualizér automaticky přejde na odpovídající uzel ModuleStatement ve stromu. 

Vizualizér zvýrazní položku ve stromu, jejíž rozsah nejlépe odpovídá rozsahu textu vybraného v editoru.

Vizualizér aktualizuje strom, aby odpovídal úpravám v aktivním souboru s kódem. Přidejte volání `Console.WriteLine()` dovnitř `Main()`. Když zadáte, Vizualizér aktualizuje strom.

Po zadání můžete `Console.`typ pozastavit. Strom obsahuje některé položky, které jsou v růžovém barvě. V tomto okamžiku jsou v zadaném kódu chyby (označované také jako ' Diagnostics '). Tyto chyby jsou připojeny k uzlům, tokenům a minihry ve stromu syntaxe. Vizualizér zobrazuje, ke kterým položkám jsou k dispozici chyby s zvýrazněním pozadí v růžovém zobrazení. Můžete zkontrolovat chyby u každé položky, která je růžová, přesunutím ukazatele myši na položku. Vizualizér zobrazuje pouze syntaktické chyby (chyby související se syntaxí typového kódu); nezobrazuje žádné sémantické chyby.
 
## <a name="syntax-graphs"></a>Grafy syntaxe

Klikněte pravým tlačítkem na libovolnou položku ve stromové struktuře a klikněte na **graf zobrazit směrnou syntaxi**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Vizualizér zobrazuje grafické znázornění podstromu root na vybrané položce. Vyzkoušejte tento postup pro uzel **MethodDeclaration** , který odpovídá `Main()` metodě v C# příkladu. Vizualizér zobrazuje graf syntaxe, který vypadá takto:

![Zobrazení C# syntaxe grafu](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

Zkuste stejný pro uzel **podbloku** odpovídající `Main()` metodě v předchozím příkladu VB. Vizualizér zobrazuje graf syntaxe, který vypadá takto:

![Zobrazení grafu syntaxe VB](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Prohlížeč syntaxe grafu má možnost Zobrazit legendu pro barevné schéma. Můžete také umístit ukazatel myši na jednotlivé položky v grafu syntaxe a zobrazit tak vlastnosti odpovídající dané položce.

Můžete zobrazit grafy syntaxe pro různé položky ve stromové struktuře opakovaně a grafy budou vždy zobrazeny ve stejném okně v rámci sady Visual Studio. Toto okno můžete ukotvit na vhodném místě v rámci sady Visual Studio, takže nemusíte přepínat mezi kartami a zobrazit nový graf syntaxe. Dolní, pod okny editoru kódu, je často pohodlné.

Toto je ukotvené rozložení, které se má použít v okně nástroje Vizualizér a v okně s grafem syntaxe:

![Jedno ukotvené rozložení pro okno s grafem Vizualizér a syntaxe](media/syntax-visualizer/docking-layout.png)

Další možností je umístit okno grafu syntaxe na druhý monitor v instalaci s duálním monitorováním.

## <a name="inspecting-semantics"></a>Kontrola sémantiky

Syntax Visualizer umožňuje základní kontrolu symbolů a sémantických informací. V `double x = 1 + 1;` C# příkladu zadejte dovnitř Main (). Pak vyberte výraz `1 + 1` v okně Editor kódu. Vizualizér zvýrazní uzel **AddExpression** v Vizualizér. Klikněte pravým tlačítkem na tuto **AddExpression** a klikněte na **Zobrazit symbol (pokud existuje)** . Všimněte si, že většina položek nabídky má kvalifikátor "if any". Syntax Visualizer kontroluje vlastnosti uzlu, včetně vlastností, které nemusí být k dispozici pro všechny uzly. 

Tabulka vlastností v Vizualizér se aktualizuje tak, jak je znázorněno na následujícím obrázku: Symbol pro výraz je **SynthesizedIntrinsicOperatorSymbol** s **typem Kind =** .

![Vlastnosti symbolu](media/syntax-visualizer/symbol-properties.png)

Zkuste **Zobrazit TypeSymbol (pokud existuje)** pro stejný uzel **AddExpression** . Tabulka vlastností v Vizualizér se aktualizuje tak, jak je znázorněno na následujícím obrázku, což značí, že typ vybraného výrazu `Int32`je.

![Vlastnosti TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Zkuste **zobrazit převedený TypeSymbol (pokud existuje)** pro stejný uzel **AddExpression** . Aktualizace mřížky vlastností, které označují, že i když je `Int32`typ výrazu, je převeden typ výrazu, jak je `Double` znázorněno na následujícím obrázku. Tento uzel obsahuje informace o převedených symbolech typu, protože výraz se `Int32` vyskytuje v kontextu, ve kterém musí být převeden `Double`na. Tento převod splňuje `Double` typ zadaný pro proměnnou `x` na levé straně operátoru přiřazení.

![Převedené vlastnosti TypeSymbol](media/syntax-visualizer/converted-type-symbol-properties.png)

Nakonec zkuste **Zobrazit konstantní hodnotu (pokud existuje)** pro stejný uzel **AddExpression** . Mřížka vlastností ukazuje, že hodnota výrazu je časová konstanta kompilace s hodnotou `2`.

![Konstantní hodnota](media/syntax-visualizer/constant-value.png)

Předchozí příklad lze také replikovat v jazyce VB. Zadejte `Dim x As Double = 1 + 1` soubor VB. V okně editoru `1 + 1` kódu vyberte výraz. Vizualizér zvýrazní odpovídající uzel **AddExpression** v Vizualizér. Opakujte předchozí kroky pro tento **AddExpression** a měli byste vidět identické výsledky.

Projděte si další kód v VB. Aktualizujte hlavní soubor VB pomocí následujícího kódu:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Tento kód zavádí alias s názvem `C` , který se mapuje na `System.Console` typ v horní části souboru a používá tento alias uvnitř `Main()`. Vyberte použití tohoto aliasu `C` v v `C.WriteLine()`rámci `Main()` metody. Vizualizér vybere odpovídající uzel **identifikátoru** v Vizualizér. Klikněte pravým tlačítkem na tento uzel a pak klikněte na **Zobrazit symbol (pokud existuje)** . Mřížka vlastností označuje, že tento identifikátor je vázán na typ `System.Console` , jak je znázorněno na následujícím obrázku:

![Vlastnosti symbolu](media/syntax-visualizer/symbol-visual-basic.png)

Zkuste **Zobrazit AliasSymbol (pokud existuje)** pro stejný uzel **identifikátoru** . Mřížka vlastností označuje, že identifikátor je alias s názvem `C` , který je vázán `System.Console` na cíl. Jinými slovy, Mřížka vlastností poskytuje informace týkající se **AliasSymbol** , které odpovídají identifikátoru `C`.

![Vlastnosti AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Zkontrolujte symbol odpovídající deklarovanému typu, metodě, vlastnosti. Vyberte odpovídající uzel v Vizualizér a klikněte na **Zobrazit symbol (pokud existuje)** . Vyberte metodu `Sub Main()`, včetně těla metody. Klikněte na **Zobrazit symbol (pokud existuje)** pro odpovídající uzel **podbloku** v Vizualizér. Mřížka vlastností zobrazuje **MethodSymbol** pro tento dílčí **blok** má název `Main` s návratovým typem. `Void`

![Zobrazení symbolu pro deklaraci metody](media/syntax-visualizer/method-symbol.png)

Výše uvedené příklady VB lze snadno replikovat v C#. `using C = System.Console;` Zadejte`Imports C = System.Console` místo pro alias. Předchozí kroky v C# systému poskytují identické výsledky v okně Vizualizér.

Operace sémantické inspekce jsou k dispozici pouze na uzlech. Nejsou k dispozici na tokenech nebo minihry. Ne všechny uzly mají zajímavé sémantické informace ke kontrole. Pokud uzel nemá zajímavé sémantické informace, kliknutím na **Symbol zobrazení \* (pokud existuje)** se zobrazí prázdná mřížka vlastností.

Můžete si přečíst další informace o rozhraních API pro provádění sémantické analýzy v dokumentu přehled [práce s sémantikou](work-with-semantics.md) .

## <a name="closing-the-syntax-visualizer"></a>Zavírá se Vizualizér syntaxe.

Okno Vizualizér můžete zavřít, pokud ho nepoužíváte k prohlédnutí zdrojového kódu. Vizualizér syntaxe aktualizuje svůj displej při procházení kódu, úpravy a změny zdroje. Může to být rušivé, když ho nepoužíváte. 
