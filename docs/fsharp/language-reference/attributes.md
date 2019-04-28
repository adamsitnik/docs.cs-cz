---
title: Atributy
description: Zjistěte, jak F# atributy povolit programovací konstrukce, které se použije k metadatům.
ms.date: 05/16/2016
ms.openlocfilehash: 6e80bc4e32ee4ff5ff132270bde8e2fd018369e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703202"
---
# <a name="attributes"></a>Atributy

Atributy umožňují metadata použije programovací konstrukce.

## <a name="syntax"></a>Syntaxe

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *cílové* je nepovinný a pokud jsou k dispozici, určuje typ entity program, který platí atribut pro. Platné hodnoty pro *cílové* jsou uvedené v tabulce, která se zobrazí později v tomto dokumentu.

*Název atributu* odkazuje na název (může být kvalifikován s obory názvů) platný atribut typu, s nebo bez přípony `Attribute` , která se obvykle používá v názvech typ atributu. Například typ `ObsoleteAttribute` lze zkrátit jenom `Obsolete` v tomto kontextu.

*Argumenty* argumenty konstruktoru pro typ atributu. Pokud atribut nemá výchozí konstruktor, lze vynechat seznam argumentů a závorky. Atributy podpory poziční argumenty a pojmenované argumenty. *Poziční argumenty* jsou argumenty, které se používají v pořadí, v jakém jsou uvedeny. Pojmenované argumenty je možné, pokud má atribut veřejné vlastnosti. Můžete nastavit tyto pomocí následující syntaxe v seznamu argumentů.

```
*property-name* = *property-value*
```

Inicializace taková vlastnost může být v libovolném pořadí, ale musí postupovat žádné poziční argumenty. Tady je příklad, který používá poziční argumenty a inicializací vlastností atributu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

V tomto příkladu je atribut `DllImportAttribute`, zde používá ve zkráceném tvaru. První argument je poziční parametr a druhý je vlastnost.

Atributy jsou .NET programovací konstrukce, která umožňuje označované jako objekt *atribut* má být přidružena k typu nebo jiný prvek programu. Ovládací prvek programu ke které se použije atribut se označuje jako *cíl atributu*. Atribut obvykle obsahuje metadata o cíli. V tomto kontextu může být metadata žádná data o typ jiný než jeho polí a členy.

Atributy v F# můžete použít pro následující programovací konstrukce: funkce, metody, sestavení, modulů, typů (tříd, záznamy, struktury, rozhraní, delegátů, výčty, sjednocení a tak dále), konstruktory, vlastnosti, pole, parametry, zadejte parametry a návratové hodnoty. Atributy nejsou povolené v `let` vazby uvnitř třídy, výrazy nebo výrazy pracovního postupu.

Obvykle deklarace atributu se zobrazí přímo před deklarací cíl atributu. Více atribut deklarace je možné společně, následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Atributy můžete dotazovat v době běhu pomocí reflexe .NET.

Je možné deklarovat několik atributů jednotlivě, stejně jako v předcházejícím příkladu, nebo je lze deklarovat v jednu sadu závorek je-li použít středník oddělit jednotlivé atributy a konstruktory, jak je znázorněno zde.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Zahrnout obvyklých atributy `Obsolete` atribut atributy pro požadavky na zabezpečení atributů pro podporu modelu COM, atributy, které se týkají vlastnictví kódu a atributy určující, zda typ lze serializovat. Následující příklad ukazuje použití `Obsolete` atribut.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Pro atribut cíle `assembly` a `module`, použít atributy k nejvyšší úrovni `do` vazby v sestavení. Může obsahovat slovo `assembly` nebo `module` v deklaraci atributu následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Pokud vynecháte cíl atributu pro atribut použitý k `do` vazby, F# kompilátor se pokusí určit atribut target, to dává smysl pro tento atribut. Mnoho atribut třídy mají atribut typu `System.AttributeUsageAttribute` , který obsahuje informace o možných cíle pro tento atribut nepodporuje. Pokud `System.AttributeUsageAttribute` naznačuje, že atribut podporuje funkce jako cíle, chcete-li použít hlavní vstupní bod programu se používá atribut. Pokud `System.AttributeUsageAttribute` naznačuje, že atribut podporuje sestavení jako cíle, kompilátor přijímá atribut, který chcete použít k sestavení. Většina atributy se nevztahují na funkce a sestavení, ale v případech, ve kterém se dělají, atribut věnovat platí pro hlavní funkce programu. Pokud cílový atribut je explicitně zadán, je atribut použit na zadané cílové.

I když obvykle nepotřebujete zadat atribut cílit explicitně, platné hodnoty pro *cílové* v atributu jsou uvedeny v následující tabulce, spolu s příkladem použití.

<table>
  <tr>
    <th>Cíl atributu</td>
    <th>Příklad</td> 
  </tr>
  <tr>
    <td>sestavení</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]<code></pre></td> 
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1<code></pre></td> 
  </tr>
  <tr>
    <td>pole</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int<code></pre></td> 
  </tr>
  <tr>
    <td>property</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x<code></pre></td> 
  </tr>
  <tr>
    <td>Param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10<code></pre></td> 
  </tr>
  <tr>
    <td> – typ</td>
    <td>
        <pre lang="fsharp"><code>
        [&lt;type: StructLayout(Sequential)&gt;] 
        type MyStruct = 
        struct 
        x : byte
        y : int
        end
        <code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)