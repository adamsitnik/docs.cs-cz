---
title: Řetězce
description: Přečtěte si F# , jak typ String představuje neproměnlivý text jako sekvenci znaků Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 25f5d7ce5059ba5ddb4e938313c511734c2d7320
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216732"
---
# <a name="strings"></a><span data-ttu-id="2f94a-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="2f94a-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="2f94a-104">Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN.</span><span class="sxs-lookup"><span data-stu-id="2f94a-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="2f94a-105">Reference k rozhraní docs.microsoft.com API není dokončená.</span><span class="sxs-lookup"><span data-stu-id="2f94a-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="2f94a-106">`string` Typ představuje neproměnlivý text jako posloupnost znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="2f94a-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="2f94a-107">`string`je alias pro `System.String` v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f94a-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f94a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f94a-108">Remarks</span></span>

<span data-ttu-id="2f94a-109">Řetězcové literály jsou odděleny znakem uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="2f94a-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="2f94a-110">Znak zpětného lomítka \\ () se používá ke kódování určitých speciálních znaků.</span><span class="sxs-lookup"><span data-stu-id="2f94a-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="2f94a-111">Zpětné lomítko a další znak dohromady se označují jako *řídicí sekvence*.</span><span class="sxs-lookup"><span data-stu-id="2f94a-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="2f94a-112">Řídicí sekvence podporované v F# řetězcových literálech jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2f94a-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="2f94a-113">Znak</span><span class="sxs-lookup"><span data-stu-id="2f94a-113">Character</span></span>|<span data-ttu-id="2f94a-114">Řídicí sekvence</span><span class="sxs-lookup"><span data-stu-id="2f94a-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="2f94a-115">Výstrahy</span><span class="sxs-lookup"><span data-stu-id="2f94a-115">Alert</span></span>|`\a`|
|<span data-ttu-id="2f94a-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="2f94a-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="2f94a-117">Informační kanál formuláře</span><span class="sxs-lookup"><span data-stu-id="2f94a-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="2f94a-118">Nového</span><span class="sxs-lookup"><span data-stu-id="2f94a-118">Newline</span></span>|`\n`|
|<span data-ttu-id="2f94a-119">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="2f94a-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="2f94a-120">Karta</span><span class="sxs-lookup"><span data-stu-id="2f94a-120">Tab</span></span>|`\t`|
|<span data-ttu-id="2f94a-121">Vertikální tabulátor</span><span class="sxs-lookup"><span data-stu-id="2f94a-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="2f94a-122">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="2f94a-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="2f94a-123">Znak uvozovek</span><span class="sxs-lookup"><span data-stu-id="2f94a-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="2f94a-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="2f94a-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="2f94a-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="2f94a-125">Unicode character</span></span>|<span data-ttu-id="2f94a-126">`\DDD`(kde `D` označuje desítkovou číslici; rozsah 000-255; `\231` například = "ç")</span><span class="sxs-lookup"><span data-stu-id="2f94a-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="2f94a-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="2f94a-127">Unicode character</span></span>|<span data-ttu-id="2f94a-128">`\xHH`(kde `H` označuje hexadecimální číslo; rozsah 00-FF; `\xE7` například = "ç")</span><span class="sxs-lookup"><span data-stu-id="2f94a-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="2f94a-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="2f94a-129">Unicode character</span></span>|<span data-ttu-id="2f94a-130">`\uHHHH`(UTF-16) (kde `H` označuje šestnáctkovou číslici; rozsah 0000-FFFF;  například `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="2f94a-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="2f94a-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="2f94a-131">Unicode character</span></span>|<span data-ttu-id="2f94a-132">`\U00HHHHHH`(UTF-32) (kde `H` označuje hexadecimální číslici, rozsah 000000-10FFFF;  například `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="2f94a-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="2f94a-133">`\DDD` Řídicí sekvence je Desítkový zápis, nikoli osmičkový zápis podobně jako ve většině ostatních jazyků.</span><span class="sxs-lookup"><span data-stu-id="2f94a-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="2f94a-134">Proto číslice `8` a `9` jsou platné a sekvence `\032` představuje mezeru (U + 0020), zatímco `\040`stejný bod kódu v osmičkové notaci by byl.</span><span class="sxs-lookup"><span data-stu-id="2f94a-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="2f94a-135">S omezením na rozsah 0-255 (0xFF), `\DDD` řídicí sekvence a `\x` jsou efektivně nastaveny jako znaková sada [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , protože se shoduje s 256 prvními body kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="2f94a-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="2f94a-136">Pokud předchází symbol @, je literál doslovného řetězce.</span><span class="sxs-lookup"><span data-stu-id="2f94a-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="2f94a-137">To znamená, že všechny řídicí sekvence jsou ignorovány s tím rozdílem, že dva znaky uvozovek jsou interpretovány jako jeden znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="2f94a-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="2f94a-138">Navíc může být řetězec uzavřen třemi uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="2f94a-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="2f94a-139">V tomto případě jsou všechny řídicí sekvence ignorovány, včetně znaků dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="2f94a-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="2f94a-140">Chcete-li zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete buď použít doslovné řetězec nebo trojitý řetězec v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="2f94a-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="2f94a-141">Pokud použijete doslovné řetězec, je nutné zadat dva znaky uvozovek, které označují znak jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="2f94a-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="2f94a-142">Použijete-li řetězec v uvozovkách, lze použít znaky jednoduchých uvozovek bez jejich analyzování jako konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="2f94a-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="2f94a-143">Tato technika může být užitečná při práci s XML nebo jinými strukturami, které zahrnují vložené uvozovky.</span><span class="sxs-lookup"><span data-stu-id="2f94a-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="2f94a-144">V kódu jsou řetězce, které mají zalomení řádků, přijaty a zalomení řádků jsou interpretovány jako newlines, pokud znak zpětného lomítka není poslední znak před koncem řádku.</span><span class="sxs-lookup"><span data-stu-id="2f94a-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="2f94a-145">Počáteční prázdné místo na dalším řádku se při použití znaku zpětného lomítka ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2f94a-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="2f94a-146">Následující kód vytvoří `str1` řetězec, který má hodnotu `"abc\ndef"` a řetězec `str2` , který má hodnotu `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="2f94a-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="2f94a-147">K jednotlivým znakům v řetězci můžete přistupovat pomocí syntaxe typu pole, a to následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="2f94a-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="2f94a-148">Výstup je `b`.</span><span class="sxs-lookup"><span data-stu-id="2f94a-148">The output is `b`.</span></span>

<span data-ttu-id="2f94a-149">Nebo můžete extrahovat podřetězce pomocí syntaxe řezu pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2f94a-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="2f94a-150">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="2f94a-150">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="2f94a-151">Řetězce ASCII můžete reprezentovat poli bajtů bez znaménka, typ `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="2f94a-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="2f94a-152">Přidáte příponu `B` do řetězcového literálu, který označuje, že se jedná o řetězec ASCII.</span><span class="sxs-lookup"><span data-stu-id="2f94a-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="2f94a-153">Řetězcové literály ASCII používané s poli bajtů podporují stejné řídicí sekvence jako řetězce Unicode, s výjimkou řídicích sekvencí Unicode.</span><span class="sxs-lookup"><span data-stu-id="2f94a-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="2f94a-154">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="2f94a-154">String Operators</span></span>

<span data-ttu-id="2f94a-155">Existují dva způsoby, jak zřetězit řetězce: pomocí `+` operátoru nebo `^` pomocí operátoru.</span><span class="sxs-lookup"><span data-stu-id="2f94a-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="2f94a-156">`+` Operátor udržuje kompatibilitu s funkcemi pro zpracování .NET Framework řetězců.</span><span class="sxs-lookup"><span data-stu-id="2f94a-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="2f94a-157">Následující příklad znázorňuje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="2f94a-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="2f94a-158">String – Třída</span><span class="sxs-lookup"><span data-stu-id="2f94a-158">String Class</span></span>

<span data-ttu-id="2f94a-159">Vzhledem k tomu, že F# typ řetězce v je `System.String` ve skutečnosti .NET Framework `System.String` typ, jsou k dispozici všichni členové.</span><span class="sxs-lookup"><span data-stu-id="2f94a-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="2f94a-160">To zahrnuje `+` operátor, který se používá ke zřetězení řetězců `Length` , vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="2f94a-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="2f94a-161">Další informace o řetězcích naleznete v `System.String`tématu.</span><span class="sxs-lookup"><span data-stu-id="2f94a-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="2f94a-162">`Chars` Pomocí`System.String`vlastnosti můžete k jednotlivým znakům v řetězci přistupovat zadáním indexu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2f94a-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="2f94a-163">Řetězec – modul</span><span class="sxs-lookup"><span data-stu-id="2f94a-163">String Module</span></span>

<span data-ttu-id="2f94a-164">Další funkce pro zpracování řetězců je obsažena v `String` modulu `FSharp.Core` v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2f94a-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="2f94a-165">Další informace najdete v tématu [modul Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="2f94a-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f94a-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f94a-166">See also</span></span>

- [<span data-ttu-id="2f94a-167">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2f94a-167">F# Language Reference</span></span>](index.md)
