---
title: '#Pokud se direktiva preprocesoru - C# odkaz'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: b92660a69194ff2d52cd78427f73510de514ea48
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545816"
---
# <a name="if-c-reference"></a>#if (referenční dokumentace jazyka C#)

Pokud nalezne kompilátor jazyka C# `#if` směrnice, a nakonec za [#endif](preprocessor-endif.md) direktiv, kompiluje kód mezi direktivy pouze v případě, že je definován zadaný symbol. Na rozdíl od jazyka C a C++ nelze přiřadit číselné hodnoty symbolu. Příkazu #if v jazyce C# je logická hodnota a pouze kontroluje, zda byl definován symbol, nebo ne. Příklad:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Můžete použít operátory [ == ](../operators/equality-operators.md#equality-operator-) (rovnost) a [! =](../operators/equality-operators.md#inequality-operator-) (nerovnost) pouze pro testování [true](../keywords/true.md) nebo [false](../keywords/false.md). Hodnota TRUE znamená, že je definován symbol. Příkaz `#if DEBUG` má stejný význam jako `#if (DEBUG == true)`. Můžete použít operátory [ && ](../operators/conditional-and-operator.md) (a), [ &#124; &#124; ](../operators/conditional-or-operator.md) (nebo), a [!](../operators/logical-negation-operator.md) (ne) k vyhodnocení, zda byly definovány více symbolů. Symboly a operátory je také možné seskupovat pomocí závorek.

## <a name="remarks"></a>Poznámky

`#if`, spolu s [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), a [#undef](preprocessor-undef.md) direktivy, vám umožní zahrnout nebo vyloučit kód založený na existenci jedné nebo víc symbolů. To může být užitečné při kompilování kódu pro sestavení pro ladění nebo při kompilaci pro konkrétní konfiguraci.

Podmíněné direktivy od `#if` – direktiva musí být explicitně ukončen direktivou `#endif` směrnice.

`#define` Umožňuje definovat symbol. Pak pomocí symbolu jako výraz předaný `#if` direktiv, je výraz vyhodnocen `true`.

Můžete také definovat symbol s [-definovat](../compiler-options/define-compiler-option.md) – možnost kompilátoru. Můžete nedefinovat symbol s [#undef](preprocessor-undef.md).

Symbol, který definujete pomocí `-define` nebo s `#define` nebude v rozporu s proměnnou se stejným názvem. To znamená název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.

Rozsah symbolu vytvořené pomocí `#define` je soubor, ve kterém byl definován.

Systém sestavení je také vědět, která představuje různé předdefinované symboly preprocesoru [platforem](../../../standard/frameworks.md). Jsou užitečné při vytváření aplikací určených více než jedné implementace rozhraní .NET nebo verzi.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Další předdefinované symboly zahrnovat konstanty ladění a trasování. Můžete přepsat hodnoty nastavené pro projekt pomocí `#define`. Symbol ladění, například se automaticky nastaví v závislosti na vlastností konfigurace sestavení (režim "Ladění" a "Vydání").

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak definovat symbol test v souboru a poté otestujte hodnoty symbolů ladění a test. Výstup tohoto příkladu závisí na, jestli jste sestavili projekt na režim konfigurace ladění nebo vydání.

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

Následující příklad ukazuje, jak otestovat pro jiné cílové architektury, abyste mohli používat novějších rozhraní API, pokud je to možné:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [C# Direktivy preprocesoru](index.md)
- [Postupy: Podmíněná kompilace pomocí trasování a ladění](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
