---
title: Like – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 795ecc2e80d57af29ccd50c50d2dd209c6425e40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701125"
---
# <a name="like-operator-visual-basic"></a>Like – operátor (Visual Basic)
Porovná řetězec se vzorem.  

> [!IMPORTANT]
> Operátor `Like` aktuálně není v projektech .NET Core a .NET Standard podporován.

## <a name="syntax"></a>Syntaxe  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Jakákoli proměnná `Boolean`. Výsledkem je hodnota @no__t 0, která označuje, zda `string` splňuje požadavky `pattern`.  
  
 `string`  
 Požadováno. Libovolný výraz `String`.  
  
 `pattern`  
 Požadováno. Libovolný výraz `String`, který odpovídá konvencím porovnávání vzorů popsaných v tématu "poznámky".  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota v `string` vyhovuje vzoru obsaženému v `pattern`, `result` je `True`. Pokud řetězec nevyhovuje vzoru, `result` je `False`. Pokud jsou `string` i `pattern` prázdné řetězce, výsledek je `True`.  
  
## <a name="comparison-method"></a>Metoda porovnání  
 Chování operátoru `Like` závisí na [příkazu Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md). Výchozí metoda porovnání řetězců pro každý zdrojový soubor je `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Možnosti vzorku  
 Předdefinované porovnávání vzorů poskytuje univerzální nástroj pro porovnávání řetězců. Funkce porovnávání se vzorci vám umožní porovnat jednotlivé znaky v `string` s konkrétním znakem, zástupným znakem, seznamem znaků nebo rozsahem znaků. V následující tabulce jsou uvedeny znaky povolené v `pattern` a co se shodují.  
  
|Znaky v `pattern`|Shody v `string`|  
|-----------------------------|-------------------------|  
|`?`|Libovolný jeden znak|  
|`*`|Nula nebo více znaků|  
|`#`|Jakákoli jedna číslice (0 – 9)|  
|`[charlist]`|Libovolný jeden znak v `charlist`|  
|`[!charlist]`|Libovolný jeden znak, který není v `charlist`|  
  
## <a name="character-lists"></a>Seznamy znaků  
 Skupina jednoho nebo více znaků (`charlist`) uzavřená v závorkách (`[ ]`) se dá použít k vyhledání libovolného znaku v `string` a může obsahovat skoro jakýkoli kód znaku, včetně číslic.  
  
 Vykřičník (`!`) na začátku `charlist` znamená, že je provedena shoda, pokud libovolný znak kromě znaků v `charlist` se nachází v `string`. Při použití mimo hranaté závorky se vykřičník shoduje.  
  
## <a name="special-characters"></a>Speciální znaky  
 Aby se shodovaly se speciálními znaky, levou hranatou závorku (`[`), otazníkem (`?`), znakem čísla (`#`) a hvězdičkou (`*`), vložte je do závorek. Pravou hranatou závorku (`]`) nelze použít v rámci skupiny, aby se shodovala se sebou, ale lze ji použít mimo skupinu jako jednotlivý znak.  
  
 Sekvence znaků `[]` je považována za řetězec s nulovou délkou (`""`). Nemůže však být součástí seznamu znaků uzavřený v závorkách. Chcete-li ověřit, zda pozice v `string` obsahuje jednu ze skupin znaků nebo žádný znak vůbec, můžete použít `Like` dvakrát. Příklad naleznete v tématu [How to: Match String to a vzor](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Rozsahy znaků  
 Když použijete spojovník (`–`) k oddělení dolních a horních mezí rozsahu, `charlist` může určit rozsah znaků. Například `[A–Z]` má za následek shodu, pokud odpovídající pozice znaku v `string` obsahuje libovolný znak v rozsahu `A` – `Z` a `[!H–L]` má za následek shodu, pokud odpovídající pozice znaku obsahuje libovolný znak mimo Range `H` – `L`.  
  
 Když zadáte rozsah znaků, musí být ve vzestupném pořadí řazení, tj. od nejnižší po nejvyšší. Proto je `[A–Z]` platný vzor, ale `[Z–A]` není.  
  
### <a name="multiple-character-ranges"></a>Více rozsahů znaků  
 Chcete-li zadat více rozsahů pro stejné umístění znaků, vložte je do stejné hranaté závorky bez oddělovačů. Například `[A–CX–Z]` má za následek shodu, pokud odpovídající pozice znaku v `string` obsahuje libovolný znak v rozsahu `A` – `C` nebo v rozsahu `X` – `Z`.  
  
### <a name="usage-of-the-hyphen"></a>Použití pomlčky  
 Spojovník (`–`) se může objevit buď na začátku (za vykřičníkem, pokud existuje), nebo na konci `charlist` pro vyhledání sebe sama. V jakémkoli jiném umístění pomlčka identifikuje rozsah znaků oddělených znaky na obou stranách pomlčky.  
  
## <a name="collating-sequence"></a>Sekvence řazení  
 Význam zadaného rozsahu závisí na řazení znaků v době běhu, počítáno od `Option Compare` a nastavení národního prostředí systému, na kterém je spuštěn kód. U `Option Compare Binary` odpovídá rozsah `[A–E]` `A`, `B`, `C`, `D` a `E`. U `Option Compare Text` odpovídá `[A–E]` `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, 0, 1, 2 a 3. Rozsah neodpovídá `Ê` nebo `ê`, protože zvýrazněné znaky se v pořadí řazení vyhodnotí po nezvýrazněných znacích.  
  
## <a name="digraph-characters"></a>Znaky grafu  
 V některých jazycích existují abecední znaky, které představují dva samostatné znaky. Například několik jazyků používá znak `æ` pro reprezentaci znaků `a` a `e`, když se zobrazí dohromady. Operátor `Like` rozpozná, že jediný znak v grafu a dva jednotlivé znaky jsou ekvivalentní.  
  
 Pokud je v nastavení národního prostředí systému určen jazyk, který používá znak rozgrafu, je výskyt jednoduchého znaku grafu v `pattern` nebo `string` stejný jako ekvivalentní sekvence dvou znaků v druhém řetězci. Podobně znak v `pattern` uzavřený v závorkách (sám o sobě, v seznamu nebo v rozsahu) odpovídá ekvivalentní posloupnosti dvou znaků v `string`.  
  
## <a name="overloading"></a>Přetížení  
 Operátor `Like` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá operátor `Like` pro porovnání řetězců s různými vzory. Výsledky přejdou do proměnné `Boolean` určující, zda každý řetězec vyhovuje vzoru.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Postupy: Porovnání řetězce se vzorem](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
