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
ms.openlocfilehash: 38e56b8c0ec6bab89052ee42a2cd9c24053c658e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768326"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="55745-102">Like – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55745-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="55745-103">Porovná řetězec oproti vzoru.</span><span class="sxs-lookup"><span data-stu-id="55745-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="55745-104">`Like` Operátor není aktuálně podporován v projektech .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="55745-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="55745-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55745-105">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="55745-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="55745-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="55745-107">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="55745-107">Required.</span></span> <span data-ttu-id="55745-108">Žádné `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="55745-108">Any `Boolean` variable.</span></span> <span data-ttu-id="55745-109">Výsledkem je `Boolean` hodnotu, která určuje, jestli `string` splňuje požadavky `pattern`.</span><span class="sxs-lookup"><span data-stu-id="55745-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="55745-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="55745-110">Required.</span></span> <span data-ttu-id="55745-111">Žádné `String` výrazu.</span><span class="sxs-lookup"><span data-stu-id="55745-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="55745-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="55745-112">Required.</span></span> <span data-ttu-id="55745-113">Žádné `String` výraz vyhovující konvencím porovnávání vzorů je popsáno v "Poznámky".</span><span class="sxs-lookup"><span data-stu-id="55745-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55745-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55745-114">Remarks</span></span>  
 <span data-ttu-id="55745-115">Pokud hodnota v `string` vyhovuje vzoru součástí `pattern`, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="55745-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="55745-116">Pokud řetězec nevyhovuje vzoru, `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="55745-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="55745-117">Pokud mají oba `string` a `pattern` jsou prázdné řetězce, výsledkem je `True`.</span><span class="sxs-lookup"><span data-stu-id="55745-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="55745-118">Metoda porovnání</span><span class="sxs-lookup"><span data-stu-id="55745-118">Comparison Method</span></span>  
 <span data-ttu-id="55745-119">Chování `Like` operátor závisí [možnost porovnat příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="55745-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="55745-120">Výchozí metodu porovnání řetězce pro každý zdrojový soubor je `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="55745-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="55745-121">Vzor možnosti</span><span class="sxs-lookup"><span data-stu-id="55745-121">Pattern Options</span></span>  
 <span data-ttu-id="55745-122">Předdefinovaných vzorů poskytuje univerzální nástroj pro porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="55745-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="55745-123">Umožňují vám tak, aby odpovídaly každý znak v porovnávání vzorů funkce `string` proti konkrétní znak, zástupných znaků, seznam znak nebo rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="55745-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="55745-124">V následující tabulce jsou uvedeny znaků povolených v `pattern` a aby odpovídaly.</span><span class="sxs-lookup"><span data-stu-id="55745-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="55745-125">Znaky v `pattern`</span><span class="sxs-lookup"><span data-stu-id="55745-125">Characters in `pattern`</span></span>|<span data-ttu-id="55745-126">Odpovídá v `string`</span><span class="sxs-lookup"><span data-stu-id="55745-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="55745-127">Libovolný znak</span><span class="sxs-lookup"><span data-stu-id="55745-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="55745-128">Nula nebo více znaků</span><span class="sxs-lookup"><span data-stu-id="55745-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="55745-129">Libovolné číslici (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="55745-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="55745-130">Libovolnému jednomu znaku v `charlist`</span><span class="sxs-lookup"><span data-stu-id="55745-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="55745-131">Libovolný znak není v `charlist`</span><span class="sxs-lookup"><span data-stu-id="55745-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="55745-132">Znak seznamy</span><span class="sxs-lookup"><span data-stu-id="55745-132">Character Lists</span></span>  
 <span data-ttu-id="55745-133">Skupina jednoho nebo více znaků (`charlist`) v závorkách (`[ ]`) slouží k odpovídá jakémukoli jednomu znaku v `string` a může obsahovat kód na téměř jakýkoli znak, včetně číslic.</span><span class="sxs-lookup"><span data-stu-id="55745-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="55745-134">Vykřičník (`!`) na začátku `charlist` znamená, že shoda se provádí v případě, že jakémukoliv znaku kromě znaků `charlist` se nachází v `string`.</span><span class="sxs-lookup"><span data-stu-id="55745-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="55745-135">Při použití mimo hranaté závorky, představují vykřičník sebe sama.</span><span class="sxs-lookup"><span data-stu-id="55745-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="55745-136">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="55745-136">Special Characters</span></span>  
 <span data-ttu-id="55745-137">Tak, aby odpovídaly levá závorka speciální znaky (`[`), otazník (`?`), znak (`#`) a hvězdička (`*`), uzavřete do hranatých závorek.</span><span class="sxs-lookup"><span data-stu-id="55745-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="55745-138">Pravá hranatá závorka (`]`) nelze použít v rámci skupiny tak, aby odpovídaly samostatně, ale můžou se používat mimo skupinu jako jednotlivé znaky.</span><span class="sxs-lookup"><span data-stu-id="55745-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="55745-139">Sekvence znaků `[]` se považuje za řetězec nulové délky (`""`).</span><span class="sxs-lookup"><span data-stu-id="55745-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="55745-140">Však nemůže být součástí seznamu znak uzavřen v závorkách.</span><span class="sxs-lookup"><span data-stu-id="55745-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="55745-141">Pokud chcete zkontrolovat, jestli na umístění v `string` obsahuje nejméně jednu skupinu znaky ani žádný znak na všechny, můžete použít `Like` dvakrát.</span><span class="sxs-lookup"><span data-stu-id="55745-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="55745-142">Příklad najdete v tématu [jak: Porovnání řetězce se vzorem](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="55745-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="55745-143">Rozsahy znaků</span><span class="sxs-lookup"><span data-stu-id="55745-143">Character Ranges</span></span>  
 <span data-ttu-id="55745-144">Použitím spojovníku (`–`) k oddělení dolní a horní mez rozsahu, `charlist` můžete určit rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="55745-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="55745-145">Například `[A–Z]` výsledků v shoda, pokud na odpovídající znak umístěte `string` obsahuje libovolný znak v rozsahu `A`–`Z`, a `[!H–L]` výsledkem shoda, pokud umístit na odpovídající znak obsahuje libovolný znak mimo rozsah `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="55745-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="55745-146">Když zadáte rozsah znaků, musí být uvedena ve vzestupném pořadí řazení, to znamená, od nejnižší a nejvyšší.</span><span class="sxs-lookup"><span data-stu-id="55745-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="55745-147">Proto `[A–Z]` je platný vzor, ale `[Z–A]` není.</span><span class="sxs-lookup"><span data-stu-id="55745-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="55745-148">Více rozsahů znaků</span><span class="sxs-lookup"><span data-stu-id="55745-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="55745-149">Pokud chcete zadat více rozsahů pro stejnou pozici znaku, vytvořte z nich v rámci stejné závorky bez oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="55745-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="55745-150">Například `[A–CX–Z]` výsledků v shoda, pokud na odpovídající znak umístěte `string` obsahuje libovolný znak buď do rozsahu `A`–`C` nebo rozsahu `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="55745-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="55745-151">Využití spojovníku</span><span class="sxs-lookup"><span data-stu-id="55745-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="55745-152">Pomlčka (`–`) se mohou objevit na začátku (po vykřičník, pokud existuje) nebo na konci `charlist` tak, aby odpovídaly samotný.</span><span class="sxs-lookup"><span data-stu-id="55745-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="55745-153">V jiném umístění spojovník identifikuje rozsah znaků oddělených znaky na obou stranách spojovník.</span><span class="sxs-lookup"><span data-stu-id="55745-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="55745-154">Pořadí řazení</span><span class="sxs-lookup"><span data-stu-id="55745-154">Collating Sequence</span></span>  
 <span data-ttu-id="55745-155">Význam určeného rozsahu závisí na znak řazení v době běhu určeného `Option Compare` a nastavení národního prostředí systému, je kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="55745-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="55745-156">S `Option Compare Binary`, rozsahu `[A–E]` odpovídá `A`, `B`, `C`, `D`, a `E`.</span><span class="sxs-lookup"><span data-stu-id="55745-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="55745-157">S `Option Compare Text`, `[A–E]` odpovídá `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, a `e`.</span><span class="sxs-lookup"><span data-stu-id="55745-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="55745-158">Rozsah se neshoduje s `Ê` nebo `ê` protože znaky s diakritikou kompletují za výslovnost příslušných hlásek bez znaků v pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="55745-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="55745-159">Digraph znaků</span><span class="sxs-lookup"><span data-stu-id="55745-159">Digraph Characters</span></span>  
 <span data-ttu-id="55745-160">V některých jazycích jsou znaky abecedy, které představují dva samostatné znaky.</span><span class="sxs-lookup"><span data-stu-id="55745-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="55745-161">Například několik jazyků použít znak `æ` k reprezentování znaky `a` a `e` Jakmile se zobrazí společně.</span><span class="sxs-lookup"><span data-stu-id="55745-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="55745-162">`Like` Operátor rozpozná, že jsou ekvivalentní digraph jeden znak a dvě jednotlivých znaků.</span><span class="sxs-lookup"><span data-stu-id="55745-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="55745-163">Pokud je jazyk, který se používá znak digraph zadaný v nastavení národního prostředí systému, výskytu digraph jednoho znaku v buď `pattern` nebo `string` odpovídá sekvenci ekvivalentní dvou znaků do řetězce.</span><span class="sxs-lookup"><span data-stu-id="55745-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="55745-164">Obdobně digraph znaku v `pattern` uzavřený v hranatých závorkách (samy o sobě, v seznamu nebo v rozsahu) odpovídá sekvenci ekvivalentní dvou znaků v `string`.</span><span class="sxs-lookup"><span data-stu-id="55745-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="55745-165">Přetížení</span><span class="sxs-lookup"><span data-stu-id="55745-165">Overloading</span></span>  
 <span data-ttu-id="55745-166">`Like` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="55745-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="55745-167">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="55745-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="55745-168">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="55745-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55745-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="55745-169">Example</span></span>  
 <span data-ttu-id="55745-170">V tomto příkladu `Like` operátor porovnání řetězců do různých vzorů.</span><span class="sxs-lookup"><span data-stu-id="55745-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="55745-171">Výsledky přejít na `Boolean` označující, zda každý řetězec vyhovuje vzor proměnné.</span><span class="sxs-lookup"><span data-stu-id="55745-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="55745-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55745-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="55745-173">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="55745-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="55745-174">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55745-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="55745-175">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="55745-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="55745-176">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="55745-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="55745-177">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="55745-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="55745-178">Postupy: Porovnání řetězce se vzorem</span><span class="sxs-lookup"><span data-stu-id="55745-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
