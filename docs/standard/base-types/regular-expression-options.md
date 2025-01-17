---
title: Možnosti regulárních výrazů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, options
- constructs, options
- .NET Framework regular expressions, options
- inline option constructs
- options parameter
ms.assetid: c82dc689-7e82-4767-a18d-cd24ce5f05e9
ms.openlocfilehash: 4cc62696cb6589151e3abc59bbea64b693e8b3a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121734"
---
# <a name="regular-expression-options"></a>Možnosti regulárních výrazů

<a name="Top"></a>Ve výchozím nastavení porovnání vstupního řetězce s libovolným literálovým znakem ve vzoru regulárního výrazu rozlišuje velká a malá písmena a prázdné znaky ve vzorku regulárního výrazu jsou interpretovány jako literální prázdné znaky a zachytávající skupiny v regulárním výrazu. jsou pojmenovány implicitně a explicitně. Můžete upravit tyto a několik dalších aspektů výchozího chování regulárních výrazů zadáním možností regulárních výrazů. Tyto možnosti, které jsou uvedeny v následující tabulce, mohou být zahrnuty vložené jako součást vzoru regulárního výrazu, nebo mohou být poskytnuty do konstruktoru <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídy nebo statické metody porovnávání vzorů jako <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> hodnota výčtu.

|Člen RegexOptions|Vložený znak|Efekt|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Není k dispozici|Použijte výchozí chování. Další informace najdete v tématu [výchozí možnosti](#Default).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena. Další informace naleznete v tématu [porovnávání bez rozlišování velkých a](#Case)malých písmen.|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Použijte víceřádkový režim, kde `^` a `$` odpovídají začátku a konci každého řádku (místo začátku a konce vstupního řetězce). Další informace najdete v tématu [víceřádkový režim](#Multiline).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Použijte jednořádkový režim, kde tečka (.) odpovídá každému znaku (místo každého znaku kromě `\n`). Další informace najdete v tématu [režim režimu Singleline](#Singleline).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nezachytí nepojmenované skupiny. Jedinými platnými zachyceními jsou explicitně pojmenované nebo číslované skupiny formuláře `(?<`*název*`>` dílčího *výrazu*`)`. Další informace naleznete v tématu [pouze explicitní zachycení](#Explicit).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Není k dispozici|Zkompilujte regulární výraz do sestavení. Další informace naleznete v tématu [kompilované regulární výrazy](#Compiled).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Vylučte prázdné znaky bez řídicích znaků ze vzoru a povolte komentáře za číselným znaménkem (`#`). Další informace naleznete v tématu [Ignorovat prázdné](#Whitespace)znaky.|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Není k dispozici|Změňte směr hledání. Hledání se přesune zprava doleva, nikoli zleva doprava. Další informace najdete v tématu [Režim zprava doleva](#RightToLeft).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Není k dispozici|Povolí chování standardu ECMAScript pro výraz. Další informace naleznete v tématu [chování při shodě ECMAScript](#ECMAScript).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Není k dispozici|Ignorujte kulturní rozdíly v jazyce. Další informace naleznete v tématu [porovnání s použitím invariantní jazykové verze](#Invariant).|

## <a name="specifying-the-options"></a>Zadání možností

Možnosti regulárních výrazů lze zadat jedním ze tří způsobů:

- V parametru `options` konstruktoru <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídy nebo statické metody porovnávání vzorků (`Shared` v Visual Basic), jako je například <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. Parametr `options` je bitová nebo kombinace <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> výčtových hodnot.

  Pokud jsou zadány parametry <xref:System.Text.RegularExpressions.Regex> instance pomocí parametru `options` konstruktoru třídy, jsou možnosti přiřazeny vlastnosti <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>. Vlastnost <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> však neodráží vložené možnosti ve vzorku regulárního výrazu.

  V následujícím příkladu je uvedena ukázka. Používá parametr `options` <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody pro povolení porovnávání bez rozlišování velkých a malých písmen a při identifikaci slov začínajících písmenem "d" umožňuje ignorovat prázdné znaky vzoru.

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Použitím vložených možností ve vzoru regulárního výrazu se syntaxí `(?imnsx-imnsx)`. Možnost se vztahuje na vzor z bodu, ve kterém je možnost definována, buď na konec vzoru, nebo na bod, ve kterém není možnost definována jinou vloženou možností. Všimněte si, že vlastnost <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> instance <xref:System.Text.RegularExpressions.Regex> neodráží tyto vložené možnosti. Další informace naleznete v tématu [různé konstruktory](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) .

  V následujícím příkladu je uvedena ukázka. Používá vložené možnosti pro povolení porovnávání bez rozlišování velkých a malých písmen a při identifikaci slov začínajících písmenem "d" Ignorovat prázdné znaky vzoru.

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Použitím vložených možností v konkrétní seskupovací konstrukci ve vzoru regulárního výrazu s`)`syntaxe `(?imnsx-imnsx:`dílčího *výrazu* . Žádné znaménko před tím, než sada možností zapne. znaménko mínus před sadou možností je vypnuto. (`?` je pevně daná část syntaxe jazykové konstrukce, která je požadována, pokud jsou možnosti povoleny nebo zakázány.) Možnost se vztahuje pouze na tuto skupinu. Další informace naleznete v tématu [seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

  V následujícím příkladu je uvedena ukázka. Používá vložené možnosti v seskupovací konstrukci pro povolení porovnávání bez rozlišování velkých a malých písmen a při identifikaci slov, která začínají písmenem "d", ignoruje vzory prázdné znaky.

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Pokud jsou možnosti zadány jako vložené, znaménko mínus (`-`) před možností nebo sadou možností vypne tyto možnosti. Například vložená konstrukce `(?ix-ms)` zapne <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> a možnosti <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> a vypne <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnosti. Ve výchozím nastavení jsou všechny možnosti regulárních výrazů vypnuté.

> [!NOTE]
> Pokud jsou možnosti regulárních výrazů zadané v parametru `options` konstruktoru nebo volání metody v konfliktu s možnostmi určenými jako vložené ve vzoru regulárního výrazu, jsou použity vložené možnosti.

Následující pět možností regulárních výrazů lze nastavit pomocí parametru options i inline:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Následující pět možností regulárních výrazů lze nastavit pomocí parametru `options`, ale nelze je nastavit jako vložené:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Určení možností

Můžete určit, které možnosti byly poskytnuty <xref:System.Text.RegularExpressions.Regex>mu objektu při jeho vytvoření načtením hodnoty vlastnosti <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> jen pro čtení. Tato vlastnost je zvláště užitečná pro určení možností, které jsou definovány pro zkompilovaný regulární výraz vytvořený metodou <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>.

Chcete-li otestovat přítomnost jakékoli možnosti kromě <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, proveďte operaci a s hodnotou vlastnosti <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions> hodnotou, se kterou se zajímáte. Pak testujte, zda výsledek odpovídá <xref:System.Text.RegularExpressions.RegexOptions> hodnota. Následující příklad testuje, zda byla nastavena možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Chcete-li otestovat <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, určete, zda je hodnota vlastnosti <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> rovna <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, jak ukazuje následující příklad.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

V následujících částech jsou uvedeny možnosti podporované regulárním výrazem v rozhraní .NET.

<a name="Default"></a>

## <a name="default-options"></a>Výchozí možnosti

Možnost <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> označuje, že nebyly zadány žádné možnosti, a modul regulárních výrazů používá jeho výchozí chování. Ta zahrnují následující:

- Vzor je interpretován jako kanonický namísto regulárního výrazu ECMAScript.

- Vzor regulárního výrazu je porovnán ve vstupním řetězci zleva doprava.

- Při porovnávání se rozlišují malá a velká písmena.

- Prvky jazyka `^` a `$` odpovídají začátku a konci vstupního řetězce.

- Prvek jazyka `.` odpovídá každému znaku s výjimkou `\n`.

- Jakékoli prázdné místo ve vzoru regulárního výrazu je interpretováno jako literální znak mezery.

- Konvence aktuální jazykové verze se používají při porovnávání vzoru se vstupním řetězcem.

- Zachytávající skupiny ve vzoru regulárního výrazu jsou implicitní a také explicitní.

> [!NOTE]
> Možnost <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> nemá žádný vložený ekvivalent. Pokud jsou možnosti regulárních výrazů aplikovány na hodnotu inline, je výchozí chování obnoveno na základě možností podle možnosti vypnutím konkrétní možnosti. Například `(?i)` zapíná porovnávání bez rozlišení velkých a malých písmen a `(?-i)` obnoví výchozí porovnání s rozlišováním velkých a malých písmen.

Vzhledem k tomu, že možnost <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> představuje výchozí chování modulu regulárních výrazů, je zřídka explicitně určena ve volání metody. Místo toho se volá konstruktor nebo statická metoda porovnávání vzorů bez parametru `options`.

[Zpět na začátek](#Top)

<a name="Case"></a>

## <a name="case-insensitive-matching"></a>Porovnávání bez rozlišení velkých a malých písmen

Možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>, nebo `i` vložená možnost, poskytuje porovnávání bez rozlišení velkých a malých písmen. Ve výchozím nastavení se používají konvence pro velká a malá písmena aktuální jazykové verze.

Následující příklad definuje vzor regulárního výrazu, `\bthe\w*\b`, který odpovídá všem slovům začínajícím na "The". Vzhledem k tomu, že první volání metody <xref:System.Text.RegularExpressions.Regex.Match%2A> používá výchozí porovnání rozlišující malá a velká písmena, výstup označuje, že řetězec "The", který začíná větu, se neshoduje. Je porovnána při volání metody <xref:System.Text.RegularExpressions.Regex.Match%2A> s možnostmi nastavenými na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Následující příklad upravuje vzor regulárního výrazu z předchozího příkladu pro použití vložených možností namísto parametru `options` pro poskytnutí porovnání bez rozlišování velkých a malých písmen. První vzor definuje možnost nerozlišuje velká a malá písmena v seskupovací konstrukci, která se vztahuje pouze na písmeno "t" v řetězci "The". Vzhledem k tomu, že konstrukce možnosti probíhá na začátku vzoru, druhý vzor použije možnost nerozlišuje velká a malá písmena na celý regulární výraz.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

[Zpět na začátek](#Top)

<a name="Multiline"></a>

## <a name="multiline-mode"></a>Víceřádkový režim

Možnost <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> nebo `m` vložená možnost umožňuje modulu regulárních výrazů zpracovávat vstupní řetězec, který se skládá z více řádků. Změní výklad prvků `^` a `$` jazyka tak, aby odpovídaly začátku a konci řádku místo začátku a konce vstupního řetězce.

Ve výchozím nastavení `$` odpovídá pouze konci vstupního řetězce. Zadáte-li možnost <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, odpovídá buď znaku nového řádku (`\n`), nebo konci vstupního řetězce. Neshoduje se ale s kombinací znaků pro návrat na začátek řádku nebo v kanálu. Chcete-li je úspěšně porovnat, použijte dílčí výraz `\r?$` místo pouze `$`.

Následující příklad extrahuje názvy a skóre nadhazovačů ' a přidá je do kolekce <xref:System.Collections.Generic.SortedList%602>, která je seřadí v sestupném pořadí. Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A> je volána dvakrát. Při prvním volání metody je regulární výraz `^(\w+)\s(\d+)$` a nejsou nastaveny žádné možnosti. Jak ukazuje výstup, protože modul regulárních výrazů nemůže odpovídat vstupnímu vzoru spolu s počátkem a koncem vstupního řetězce, nebyly nalezeny žádné shody. Ve druhém volání metody je regulární výraz změněn na `^(\w+)\s(\d+)\r?$` a možnosti jsou nastaveny na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Jak ukazuje výstup, názvy a skóre se úspěšně shodují a skóre se zobrazí v sestupném pořadí.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Vzor regulárního výrazu `^(\w+)\s(\d+)\r*$` je definován tak, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`^`|Začněte na začátku řádku.|
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|
|`\s`|Porovná prázdný znak.|
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je druhá zachytávající skupina.|
|`\r?`|Porovná žádný nebo jeden znak návratu na začátek řádku.|
|`$`|Skončí na konci řádku.|

Následující příklad je ekvivalentní předchozímu, s tím rozdílem, že používá vloženou možnost `(?m)` k nastavení víceřádkové možnosti.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

[Zpět na začátek](#Top)

<a name="Singleline"></a>

## <a name="single-line-mode"></a>Jednořádkový režim

Možnost <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> nebo `s` vložená možnost způsobí, že modul regulárních výrazů zachází se vstupním řetězcem, jako by se skládal z jednoho řádku. Provádí to změnou chování prvku jazyka perioda (`.`) tak, aby odpovídal každému znaku, a nikoli každému znaku, kromě znaku nového řádku `\n` nebo \u000A.

Následující příklad ukazuje, jak se při použití možnosti <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> mění chování prvku jazyka `.`. Regulární výraz `^.+` začíná na začátku řetězce a odpovídá každému znaku. Ve výchozím nastavení porovnávání končí na konci prvního řádku; vzorek regulárního výrazu se shoduje se znakem návratu na začátek řádku, `\r` nebo \u000D, ale neodpovídá `\n`. Vzhledem k tomu, že možnost <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> interpretuje celý vstupní řetězec jako jediný řádek, odpovídá každému znaku ve vstupním řetězci, včetně `\n`.

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Následující příklad je ekvivalentní předchozímu, s tím rozdílem, že používá vloženou možnost `(?s)` pro povolení jednořádkového režimu.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

[Zpět na začátek](#Top)

<a name="Explicit"></a>

## <a name="explicit-captures-only"></a>Pouze explicitní zachycení

Ve výchozím nastavení jsou zachytávání skupin definovány pomocí závorek ve vzoru regulárního výrazu. Pojmenovaným skupinám se přiřadí název nebo číslo pomocí možnosti `(?<`*název*`>`dílčího *výrazu*`)`, zatímco v rámci indexu jsou přístupné nepojmenované skupiny. V objektu <xref:System.Text.RegularExpressions.GroupCollection> předjmenované skupiny předcházejí pojmenované skupiny.

Seskupovací konstrukce jsou často používány pouze k použití kvantifikátorů pro více prvků jazyka a zachycené podřetězce nejsou nijak důležité. Například, pokud následující regulární výraz:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

je určena pouze k extrakci vět, které končí tečkou, vykřičníkem nebo otazníkem z dokumentu, je důležité pouze výsledná věta (která je reprezentována objektem <xref:System.Text.RegularExpressions.Match>). Jednotlivá slova v kolekci nejsou.

Zachytávající skupiny, které se následně nepoužívají, mohou být nákladné, protože modul regulárních výrazů musí naplnit objekty kolekce <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection>. Jako alternativu můžete použít buď možnost <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nebo `n` vloženou možnost, abyste určili, že pouze platná zachycení jsou explicitně pojmenované nebo číslované skupiny, které jsou označeny *názvem* `(?<``>` dílčí *výraz* @no__t_6 Contains.

Následující příklad zobrazí informace o shodách vrácených vzorem regulárního výrazu `\b\(?((\w+),?\s?)+[\.!?]\)?`, pokud je metoda <xref:System.Text.RegularExpressions.Regex.Match%2A> volána s parametrem <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> a bez něj. Jak ukazuje výstup z prvního volání metody, modul regulárních výrazů plně naplní <xref:System.Text.RegularExpressions.GroupCollection> a objekty kolekce <xref:System.Text.RegularExpressions.CaptureCollection> s informacemi o zachycených podřetězcích. Vzhledem k tomu, že druhá metoda je volána s `options` nastavenou na <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nezachycuje informace o skupinách.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Vzor regulárního výrazu`\b\(?((?>\w+),?\s?)+[\.!?]\)?` je definován tak, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začněte na hranici slova.|
|`\(?`|Porovná žádný nebo jeden výskyt levé závorky ("(").|
|`(?>\w+),?`|Porovná jeden nebo více znaků slova, následované nula nebo jednou čárkou. Nepoužívejte mechanismu nevracení, pokud se shodují znaky slova.|
|`\s?`|Porovná žádný nebo jeden prázdný znak.|
|`((\w+),?\s?)+`|Porovná kombinaci jednoho nebo více znaků slova, nula nebo jedna čárka a nula nebo jeden prázdný znak jednou nebo vícekrát.|
|`[\.!?]\)?`|Porovná kterýkoli ze tří interpunkčních znamének, za kterými následuje nula nebo jedna uzavírací závorka (")").|

Můžete také použít vložený prvek `(?n)` pro potlačení automatických zachycení. Následující příklad upravuje předchozí vzor regulárního výrazu pro použití `(?n)` vloženého prvku namísto možnosti <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Nakonec můžete použít vložený prvek skupiny `(?n:)` pro potlačení automatických zachycení na základě skupin. Následující příklad upravuje předchozí vzor pro potlačení nepojmenovaných zachycení v vnější skupině, `((?>\w+),?\s?)`. Všimněte si, že to potlačí nepojmenované zachycení ve vnitřní skupině.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

[Zpět na začátek](#Top)

<a name="Compiled"></a>

## <a name="compiled-regular-expressions"></a>Kompilované regulární výrazy

Ve výchozím nastavení jsou interpretovány regulární výrazy v rozhraní .NET. Když je vytvořen objekt <xref:System.Text.RegularExpressions.Regex> nebo je volána statická metoda <xref:System.Text.RegularExpressions.Regex>, je vzorek regulárního výrazu analyzován do sady vlastních operačních kódů a překladač používá tyto operační kódy ke spuštění regulárního výrazu. Zahrnuje to kompromis: náklady na inicializaci modulu regulárních výrazů jsou minimalizovány na úkor výkonu za běhu.

Můžete použít zkompilované místo interpretovat regulární výrazy pomocí možnosti <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>. V tomto případě, když je vzor předán modulu regulárních výrazů, je analyzován do sady operačních kódů a následně převeden na jazyk MSIL (Microsoft Intermediate Language), který může být předán přímo do modulu CLR (Common Language Runtime). Zkompilované regulární výrazy maximalizují výkon za běhu na úkor doby inicializace.

> [!NOTE]
> Regulární výraz lze zkompilovat pouze zadáním hodnoty <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> do parametru `options` konstruktoru třídy <xref:System.Text.RegularExpressions.Regex> nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

Můžete použít zkompilované regulární výrazy v voláních statických i instancí regulárních výrazů. Ve statických regulárních výrazech je možnost <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> předána parametru `options` metody porovnávání vzorů regulárního výrazu. V regulárních výrazech je instance předána parametru `options` konstruktoru <xref:System.Text.RegularExpressions.Regex> třídy. V obou případech má za následek vyšší výkon.

Toto zlepšení výkonu však nastane pouze při splnění následujících podmínek:

- Objekt <xref:System.Text.RegularExpressions.Regex>, který představuje konkrétní regulární výraz, je používán ve více voláních metod porovnávání vzorků regulárních výrazů.

- Objektu <xref:System.Text.RegularExpressions.Regex> není povoleno přejít z oboru, aby jej bylo možné znovu použít.

- Statický regulární výraz je používán ve více voláních metod porovnávání vzorů regulárních výrazů. (Zlepšení výkonu je možné, protože regulární výrazy používané ve volání statických metod jsou ukládány do mezipaměti modulem regulárních výrazů.)

> [!NOTE]
> Možnost <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> nesouvisí s metodou <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>, která vytvoří sestavení pro zvláštní účely, které obsahuje předdefinované kompilované regulární výrazy.

[Zpět na začátek](#Top)

<a name="Whitespace"></a>

## <a name="ignore-white-space"></a>Ignorovat prázdné znaky

Ve výchozím nastavení je mezera ve vzoru regulárního výrazu významná; vynutí modul regulárních výrazů, aby odpovídal prázdnému znaku ve vstupním řetězci. Z tohoto důvodu je regulární výraz "`\b\w+\s`" a "`\b\w+`" zhruba ekvivalentní regulární výrazy. Kromě toho, pokud se ve vzoru regulárního výrazu nachází znaménko čísla (#), je interpretováno jako literální znak, který se má shodovat.

Možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>, nebo `x` vložená možnost, změní toto výchozí chování následujícím způsobem:

- Prázdné znaky bez řídicího znaku ve vzorku regulárního výrazu se ignorují. Aby bylo možné být součástí vzoru regulárního výrazu, musí být prázdné znaky uvozeny řídicím znakem (například jako `\s` nebo "`\`").

- Znak čísla (#) je interpretován jako začátek komentáře, nikoli jako literální znak. Veškerý text ve vzoru regulárního výrazu z znaku # na konec řetězce je interpretován jako komentář.

V následujících případech se však prázdné znaky v regulárním výrazu neignorují, i když použijete možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>:

- Prázdné znaky v rámci třídy znaků jsou vždy interpretovány doslova. Například vzor regulárního výrazu `[ .,;:]` odpovídá jakémukoli jednomu prázdnému znaku, tečkě, čárkě, středníku nebo dvojtečkě.

- Prázdné znaky nejsou povolené v kvantifikátoru v závorkách, například `{`*n*`}`, `{`*n*`,}`a `{`*n*`,`*m*`}`. Například vzor regulárního výrazu `\d{1, 3}` nedokáže vyhledat žádné sekvence číslic od jedné až tří číslic, protože obsahuje prázdný znak.

- Prázdné znaky nejsou povoleny ve znakové sekvenci, která zavádí prvek jazyka. Příklad:

  - Prvek jazyka `(?:`dílčí *výraz*`)` představuje nezachytávající skupinu a `(?:` část elementu nemůže obsahovat vložené mezery. Vzor `(? :`dílčí *výraz*`)` vyvolá <xref:System.ArgumentException> za běhu, protože modul regulárních výrazů nemůže analyzovat vzorek a dílčí *výraz* vzorce `( ?:``)` nedokáže porovnat dílčí *výraz*.

  - Prvek jazyka `\p{`*název*`}`, který představuje kategorii sady Unicode nebo pojmenovaný blok, nemůže do `\p{` části prvku vkládat vložené mezery. Pokud zadáte prázdné znaky, prvek vyvolá <xref:System.ArgumentException> v době běhu.

Povolení této možnosti pomáhá zjednodušit regulární výrazy, které je často obtížné analyzovat a pochopit. Zlepšuje čitelnost a umožňuje dokumentovat regulární výrazy.

Následující příklad definuje následující vzor regulárního výrazu:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Tento model je podobný vzoru definovanému pouze v sekci [explicitní zachycení](#Explicit) , s tím rozdílem, že používá možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> pro ignorování prázdných znaků Pattern.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

V následujícím příkladu je použita možnost inline `(?x)` k ignorování prázdného místa Pattern.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

[Zpět na začátek](#Top)

<a name="RightToLeft"></a>

## <a name="right-to-left-mode"></a>Režim zprava doleva

Ve výchozím nastavení modul regulárních výrazů vyhledává zleva doprava. Směr vyhledávání můžete obrátit pomocí možnosti <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>. Hledání automaticky začíná na poslední pozici znaku v řetězci. Pro metody porovnávání vzorků, které obsahují parametr počáteční pozice, jako je například <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, je počáteční pozice indexem pozice znaku vpravo, kde je hledání zahájeno.

> [!NOTE]
> Režim vzoru zprava doleva je k dispozici pouze zadáním hodnoty <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> do parametru `options` <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

Možnost <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> změní pouze směr hledání; neinterpretuje vzor regulárního výrazu zprava doleva. Například regulární výraz `\bb\w+\s` odpovídá slovům, která začínají písmenem "b" a jsou následovány prázdným znakem. V následujícím příkladu se vstupní řetězec skládá ze tří slov, která obsahují jeden nebo více znaků "b". První slovo začíná písmenem "b", druhým končí znakem "b" a třetí obsahuje dva znaky "b" uprostřed slova. Jak výstup z příkladu ukazuje, pouze první slovo odpovídá vzoru regulárního výrazu.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Všimněte si také, že kontrolní výraz dopředného vyhledávání (`(?=`dílčí *výraz*`)` prvek jazyka) a kontrolní výraz zpětného vyhledávání *(`(?<=`prvek* jazyka`)`) nemění směr. Kontrolní výrazy dopředného vyhledávání vypadají vpravo; kontrolní výrazy zpětného vyhledávání vypadají vlevo. Například regulární výraz `(?<=\d{1,2}\s)\w+,?\s\d{4}` používá kontrolní výraz zpětného vyhledávání k otestování data, které předchází názvu měsíce. Regulární výraz pak odpovídá měsíci a roku. Informace o kontrolních výrazech dopředného a zpětného vyhledávání naleznete v tématu [Grouping konstrukcís](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Začátek shody musí předcházet jednu nebo dvě desítkové číslice následované mezerou.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|`,?`|Porovná žádný nebo jeden znak čárky.|
|`\s`|Porovná prázdný znak.|
|`\d{4}`|Porovnává čtyři desítkové číslice.|

[Zpět na začátek](#Top)

<a name="ECMAScript"></a>

## <a name="ecmascript-matching-behavior"></a>Chování při shodě ECMAScript

Ve výchozím nastavení používá modul regulárních výrazů kanonické chování při porovnávání vzoru regulárního výrazu se vstupním textem. Můžete ale instruovat modul regulárních výrazů, aby používal chování při shodě ECMAScript zadáním možnosti <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>.

> [!NOTE]
> Chování kompatibilní s ECMAScript je k dispozici pouze zadáním hodnoty <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> do parametru `options` <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

Možnost <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> lze kombinovat pouze s možnostmi <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Použití jakékoli jiné možnosti v regulárním výrazu má za následek <xref:System.ArgumentOutOfRangeException>.

Chování jazyka ECMAScript a kanonických regulárních výrazů se liší ve třech oblastech: syntaxe třídy znaků, zachytávající skupiny s odkazem na sebe a osmičková a zpětná interpretace.

- Syntaxe třídy znaků. Vzhledem k tomu, že kanonické regulární výrazy podporují kódování Unicode zatímco ECMAScript nemá, třídy znaků v ECMAScript mají více omezené syntaxe a některé prvky jazyka třídy znaků mají jiný význam. Například ECMAScript nepodporuje jazykové prvky, jako je například kategorie sady Unicode nebo prvky blokování `\p` a `\P`. Podobně, `\w` prvek, který odpovídá znaku slova, je ekvivalentem `[a-zA-Z_0-9]` třídy znaků při použití jazyka ECMAScript a `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` při použití kanonického chování. Další informace naleznete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

  Následující příklad znázorňuje rozdíl mezi kanonickým a ECMAScript porovnáváním vzorů. Definuje regulární výraz `\b(\w+\s*)+`, který odpovídá slovům následovaným prázdnými znaky. Vstup se skládá ze dvou řetězců, z nichž jeden používá znakovou sadu Latin, a druhý, který používá znakovou sadu cyrilice. Jak ukazuje výstup, volání metody <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>, která používá porovnávání ECMAScript, nemůže odpovídat slovům v cyrilici, zatímco volání metody, které používá kanonické porovnávání, odpovídá těmto slovům.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Zachytávající skupiny odkazující samy na sebe. Třída zachycení regulárního výrazu s zpětným odkazem na sebe musí být aktualizována každou iterací zachycení. Jak ukazuje následující příklad, tato funkce umožňuje regulárnímu výrazu, aby `((a+)(\1) ?)+` při použití jazyka ECMAScript odpovídat vstupnímu řetězci "AA AAAA aaaaaa", ale ne při použití kanonického porovnávání.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Regulární výraz je definován tak, jak je uvedeno v následující tabulce.

  |Vzor|Popis|
  |-------------|-----------------|
  |(a +)|Porovnává písmeno "a" jednou nebo vícekrát. Toto je druhá zachytávající skupina.|
  |(\ 1)|Porovnává s podřetězcem zachyceným první zachytávající skupinou. Toto je třetí zachytávající skupina.|
  |?|Porovná žádný nebo jeden znak mezery.|
  |((a +) (\ 1)?) +|Porovná vzor jednoho nebo více znaků "a" následovaných řetězcem, který odpovídá první zachytávající skupině následované žádným nebo jedním znakem mezery jednou nebo vícekrát. Toto je první zachytávající skupina.|

- Řešení nejednoznačnosti mezi osmičkovým řídicím znakem a zpětnými odkazy. Následující tabulka shrnuje rozdíly v osmičkových a zpětných interpretech, a to pomocí regulárních výrazů, které jsou kanonické a ECMAScript.

  |Regulární výraz|Kanonické chování|Chování ECMAScript|
  |------------------------|------------------------|-------------------------|
  |`\0` následované 0 až 2 osmičkové číslice|Interpretujte jako osmičkové. Například `\044` je vždy interpretován jako osmičková hodnota a znamená "$".|Stejné chování.|
  |`\` následované číslicí od 1 do 9, následované nedalšími desítkovými číslicemi,|Interpretována jako zpětný odkaz. Například `\9` Always znamená zpětné odkazy 9, i když devátá zachytávající skupina neexistuje. Pokud zachytávající skupina neexistuje, vyvolá analyzátor regulárního výrazu <xref:System.ArgumentException>.|Pokud existuje jedna zachytávající desítková číslice, zpětný odkaz na tuto číslici. V opačném případě interpretujte hodnotu jako literál.|
  |`\` následované číslicí od 1 do 9 následovaný dalšími desítkovými číslicemi|Interpretujte číslice jako desítkovou hodnotu. Pokud tato zachytávající skupina existuje, interpretujte výraz jako zpětný odkaz.<br /><br /> V opačném případě interpretujte úvodní osmičkové číslice až na osmičkové 377; To znamená, že zvažte pouze nízkou hodnotu 8 bitů hodnoty. Interpretuje zbývající číslice jako literály. Například ve výrazu `\3000`, pokud existuje zachycující skupina 300, interpretována jako zpětný odkaz 300; Pokud zachytávající skupina 300 neexistuje, interpretujte jako osmičkové 300 následované 0.|Interpretována jako zpětný odkaz převedením tolika číslic na desítkovou hodnotu, která může odkazovat na zachycení. Pokud není možné převést číslice, interpretujte jako osmičkové číslice až na osmičkové 377; interpretuje zbývající číslice jako literály.|

[Zpět na začátek](#Top)

<a name="Invariant"></a>

## <a name="comparison-using-the-invariant-culture"></a>Porovnání s použitím neutrální jazykové verze

Ve výchozím nastavení, když modul regulárních výrazů provede porovnávání bez rozlišování velkých a malých písmen, používá konvence pro velká a malá písmena aktuální jazykové verze k určení ekvivalentních velkých a malých písmen.

Toto chování je však nežádoucí pro některé typy porovnávání, zejména při porovnávání vstupu uživatele s názvy systémových prostředků, jako jsou hesla, soubory nebo adresy URL. Následující příklad znázorňuje například scénář. Kód je určen k blokování přístupu k jakémukoli prostředku, jehož adresa URL je přednastavená na **File://** . Regulární výraz se pokusí o porovnávání bez rozlišení velkých a malých písmen s řetězcem pomocí regulárního výrazu `$FILE://`. Nicméně, pokud je aktuální jazyková verze systému tr-TR (Turečtina-Turecko), "I" není velkými ekvivalenty "i". V důsledku toho volání metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> vrátí `false`a přístup k souboru je povolen.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Další informace o porovnávání řetězců, která rozlišují velká a malá písmena a která používají invariantní jazykovou verzi, naleznete v tématu [osvědčené postupy pro použití řetězců](../../../docs/standard/base-types/best-practices-strings.md).

Namísto použití porovnávání bez rozlišování velkých a malých písmen aktuální jazykové verze můžete určit <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> možnosti ignorovat kulturní rozdíly v jazyce a použít konvence invariantní jazykové verze.

> [!NOTE]
> Porovnání s použitím invariantní jazykové verze je k dispozici pouze zadáním hodnoty <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> do parametru `options` <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

Následující příklad je stejný jako předchozí příklad s tím rozdílem, že metoda statického <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> je volána s možnostmi, které zahrnují <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. I v případě, že je aktuální jazyková verze nastavená na turečtina (Turecko), modul regulárních výrazů dokáže úspěšně porovnat "soubor" a "soubor" a zablokovat přístup k prostředku souboru.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
