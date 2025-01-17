---
title: je C# odkaz
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a04105137fad7cd3a25b869c3aa7fcbe91ed20ab
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566307"
---
# <a name="is-c-reference"></a>is (Referenční dokumentace jazyka C#)

Operátor zkontroluje, zda je výsledek výrazu kompatibilní s daným typem nebo (počínaje C# 7,0) testuje výraz na vzor. `is` Informace o operátoru testování `is` typu najdete v části [operátor is](../operators/type-testing-and-cast.md#is-operator) pro [operátory typu testování a přetypování](../operators/type-testing-and-cast.md) .

## <a name="pattern-matching-with-is"></a>Porovnávání vzorů s`is`

Počínaje C# 7,0, `is` příkazy [přepínače](switch.md) a podporují porovnávání vzorů. `is` Klíčové slovo podporuje následující vzory:

- [Vzor typu](#type-pattern), který testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování jej na proměnnou daného typu.

- [Konstantní vzor](#constant-pattern), který testuje, zda je výraz vyhodnocen na zadanou konstantní hodnotu.

- [var Pattern](#var-pattern), porovnávání, které vždy uspěje a váže hodnotu výrazu k nové místní proměnné.

### <a name="type-pattern"></a>Vzor typu

Při použití vzoru typu pro porovnávání vzorů testuje, `is` zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu. Je to jasné rozšíření `is` příkazu, které umožňuje vyhodnocování a konverzi stručných typů. Obecná forma `is` vzoru typu je:

```csharp
   expr is type varname
```

kde *expr* je výraz, který je vyhodnocen jako instance nějakého typu, *typ* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud `is` test je `true`. 

Výraz je `true` IF není *a kterákoli* z následujících možností je true: `null` `is`

- *výraz* je instancí stejného typu jako *typ*.

- *expr* je instance typu, která je odvozena z *typu*. Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.

- *výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*. *Typ v čase kompilace* proměnné je typ proměnné definovaný v jeho deklaraci. *Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.

- *expr* je instance typu, který implementuje rozhraní *typu* .

Počínaje C# 7,1, *expr* může být typ kompilace definovaný parametrem obecného typu a jeho omezeními.

Je-li `true` *výraz expr* a `is` je použit `if` s příkazem , je přiřazena pouze v `if` rámci příkazu. Rozsah *název_proměnné* je z `is` výrazu na konec `if` bloku ohraničujícího příkaz. Použití *název_proměnné* v jakémkoli jiném umístění generuje chybu při kompilaci pro použití proměnné, která nebyla přiřazena.

Následující příklad používá `is` vzor typu k poskytnutí implementace <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody typu.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez porovnávání vzorů může být tento kód napsán následujícím způsobem. Použití porovnávání vzorů typů vytváří více kompaktních a čitelných kódů tím, že eliminuje nutnost testovat, zda je `null`výsledek převodu.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Vzor `is` typu také při určování typu hodnoty vytvoří více kompaktního kódu. V následujícím příkladu je použit `is` vzorek typu k určení, zda `Person` je objekt nebo `Dog` instance před zobrazením hodnoty příslušné vlastnosti.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Konstantní vzorek

Při provádění porovnávání vzorů s konstantním vzorem otestuje, `is` zda výraz odpovídá zadané konstantě. V C# 6 a starších verzích je konstantní vzorek podporován příkazem [Switch](switch.md) . Počínaje C# 7,0 se podporuje `is` i příkaz. Jeho syntaxe je:

```csharp
   expr is constant
```

kde *expr* je výraz, který se má vyhodnotit, a *konstanta* je hodnota, která se má testovat. *konstanta* může být libovolný z následujících konstantních výrazů:

- Hodnota literálu.

- Název deklarované `const` proměnné.

- Konstanta výčtu.

Konstantní výraz je vyhodnocen následujícím způsobem:

- Pokud je *výraz* a *konstanta* integrální typy, C# operátor rovnosti určuje, zda výraz `true` vrátí hodnotu (tj. `expr == constant`zda).

- V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .  

Následující příklad kombinuje vzorce typu a konstanty k otestování, zda je `Dice` objekt instancí, a pokud je, k určení, zda je hodnota indexu předána 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

`null` Kontrolu lze provést pomocí konstantního vzoru. Klíčové slovo je podporováno `is` příkazem. `null` Jeho syntaxe je:

```csharp
   expr is null
```

Následující příklad ukazuje porovnání `null` kontrol:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>variabilní vzorek

`var` Vzor je catch-All pro libovolný typ nebo hodnotu. Hodnota *expr* je vždy přiřazena místní proměnné, která má stejný typ jako typ času kompilace *expr*. Výsledek `is` výrazu je vždy `true`. Jeho syntaxe je:

```csharp
   expr is var varname
```

V následujícím příkladu je použit vzorek var pro přiřazení výrazu proměnné s názvem `obj`. Pak zobrazí hodnotu a typ `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>specifikace jazyka C#
  
Další informace najdete v části [operátor is](~/_csharplang/spec/expressions.md#the-is-operator) v tématu [ C# specifikace jazyka](~/_csharplang/spec/introduction.md) a v následujících C# jazykových návrzích:

- [Porovnávání vzorů](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Porovnávání vzorů s obecnými typy](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Operátory testování typů a přetypování](../operators/type-testing-and-cast.md)
