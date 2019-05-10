---
title: Konstrukce alternace v regulárních výrazech .NET
description: Další informace o použití konstrukce alternace v regulárních výrazech podmíněné odpovídající.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 756d63be456dce10ca9e95963ed25602e6f4aec1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64634778"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="d8c84-103">Konstrukce alternace v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="d8c84-103">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="d8c84-104">Konstrukce alternace upravují regulární výraz, aby buď / nebo podmíněného přiřazování nebo.</span><span class="sxs-lookup"><span data-stu-id="d8c84-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="d8c84-105">.NET podporuje tři konstrukcí alternace:</span><span class="sxs-lookup"><span data-stu-id="d8c84-105">.NET supports three alternation constructs:</span></span>  
  
- [<span data-ttu-id="d8c84-106">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="d8c84-106">Pattern matching with &#124;</span></span>](#Either_Or)  
  
- [<span data-ttu-id="d8c84-107">Podmíněné porovnávání s (? () výraz) Ano&#124;žádné)</span><span class="sxs-lookup"><span data-stu-id="d8c84-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
- [<span data-ttu-id="d8c84-108">Podmíněného přiřazování na základě platný zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="d8c84-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="d8c84-109">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="d8c84-109">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="d8c84-110">Můžete použít svislá čára (`|`) znaků tak, aby odpovídaly některou z řady vzory, kde `|` odděluje každý vzorek.</span><span class="sxs-lookup"><span data-stu-id="d8c84-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="d8c84-111">Třída kladné znaků, jako jsou `|` znak můžete použít tak, aby odpovídaly některou z jednoho znaků.</span><span class="sxs-lookup"><span data-stu-id="d8c84-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="d8c84-112">Následující příklad používá třídu kladné znaků a buď / nebo porovnávání vzorů s `|` znak vyhledáte výskyty slova "gray" nebo "šedou" v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d8c84-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="d8c84-113">V takovém případě `|` znak vytváří regulární výraz, který je podrobnější.</span><span class="sxs-lookup"><span data-stu-id="d8c84-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="d8c84-114">Regulární výraz, který používá `|` znak, `\bgr(a|e)y\b`, je interpretován tak, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d8c84-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d8c84-115">Vzor</span><span class="sxs-lookup"><span data-stu-id="d8c84-115">Pattern</span></span>|<span data-ttu-id="d8c84-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d8c84-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d8c84-117">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="d8c84-118">Porovná znaky "gr".</span><span class="sxs-lookup"><span data-stu-id="d8c84-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="d8c84-119">Porovná buď se znakem „a“, nebo s „e“.</span><span class="sxs-lookup"><span data-stu-id="d8c84-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="d8c84-120">Odpovídá "y", na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-120">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="d8c84-121">`|` Znak je také možné provést buď / nebo shodu s více znaky nebo dílčích výrazů, které může obsahovat libovolnou kombinaci znakové literály a prvky jazyka regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="d8c84-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="d8c84-122">(Znak třídy tuto funkci neposkytuje.) V následujícím příkladu `|` znaků k extrakci buď USA Sociálního pojištění USA (SSN), což je číslo 9 číslic s formátem *ddd*-*dd*-*dddd*, nebo číslu Zaměstnavatel identifikační číslo (EIN), což je číslo 9 číslic s formátem *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="d8c84-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="d8c84-123">Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d8c84-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d8c84-124">Vzor</span><span class="sxs-lookup"><span data-stu-id="d8c84-124">Pattern</span></span>|<span data-ttu-id="d8c84-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d8c84-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d8c84-126">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="d8c84-127">Porovná jednu z následujících akcí: dvě desetinné číslice, za nímž následuje spojovník následovaný písmenem sedm desítkových číslic; nebo tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.</span><span class="sxs-lookup"><span data-stu-id="d8c84-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="d8c84-128">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-128">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="d8c84-129">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d8c84-129">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="d8c84-130">Podmíněné porovnávání s výrazem</span><span class="sxs-lookup"><span data-stu-id="d8c84-130">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="d8c84-131">Tento prvek jazyka se pokusí porovnat jednu ze dvou vzorků v závislosti na tom, zda lze porovnat počáteční vzorek.</span><span class="sxs-lookup"><span data-stu-id="d8c84-131">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="d8c84-132">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="d8c84-132">Its syntax is:</span></span>  
  
 <span data-ttu-id="d8c84-133">`(?(` *výraz* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="d8c84-133">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d8c84-134">kde *výraz* je počáteční vzor pro shodu, *Ano* je vzor splněno, pokud *výraz* je nalezena shoda, a *žádné* je volitelný Pokud odpovídající vzor *výraz* se neshoduje.</span><span class="sxs-lookup"><span data-stu-id="d8c84-134">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="d8c84-135">Modul regulárních výrazů zachází *výraz* jako kontrolní výraz nulové šířky; to znamená, že modul regulárních výrazů nepřesouvejte vpřed v vstupního datového proudu po je vyhodnocen jako *výraz*.</span><span class="sxs-lookup"><span data-stu-id="d8c84-135">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="d8c84-136">Proto tento konstruktor je ekvivalentní následujícímu zápisu:</span><span class="sxs-lookup"><span data-stu-id="d8c84-136">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="d8c84-137">`(?(?=` *výraz* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="d8c84-137">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d8c84-138">kde `(?=` *výraz* `)` je konstrukce kontrolní výraz nulové šířky.</span><span class="sxs-lookup"><span data-stu-id="d8c84-138">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="d8c84-139">(Další informace najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Protože modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz nulové šířky), *výraz* musí být buď kontrolní výraz nulové šířky (Další informace najdete v tématu [ Kotvy vztahů](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) nebo jako dílčí výraz, který je také součástí *Ano*.</span><span class="sxs-lookup"><span data-stu-id="d8c84-139">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="d8c84-140">V opačném případě *Ano* vzor neshoduje.</span><span class="sxs-lookup"><span data-stu-id="d8c84-140">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8c84-141">Pokud *výraz*pojmenovanou nebo číslovanou zachytávající skupinu, je konstrukce alternace, je interpretován jako zachycení testu; Další informace naleznete v další části [podmíněné odpovídající založené na platné zachycené skupině](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="d8c84-141">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="d8c84-142">Jinými slovy modul regulárních výrazů nepokusí tak, aby odpovídaly zachycené podřetězce, ale místo toho testy pro přítomnosti nebo nepřítomnosti skupiny.</span><span class="sxs-lookup"><span data-stu-id="d8c84-142">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="d8c84-143">Následující příklad je podobný příkladu, který se zobrazí [buď / nebo porovnávání vzorů s &#124; ](#Either_Or) oddílu.</span><span class="sxs-lookup"><span data-stu-id="d8c84-143">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="d8c84-144">Používá podmíněného přiřazování k určení, zda první tři znaky po hranici slova jsou dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d8c84-144">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="d8c84-145">Pokud ano, pokusí se porovnat USA Zaměstnavatel identifikační číslo (EIN).</span><span class="sxs-lookup"><span data-stu-id="d8c84-145">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="d8c84-146">Pokud ne, pokusí se porovnat americké Číslo sociálního pojištění (SSN).</span><span class="sxs-lookup"><span data-stu-id="d8c84-146">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="d8c84-147">Vzor regulárního výrazu `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d8c84-147">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d8c84-148">Vzor</span><span class="sxs-lookup"><span data-stu-id="d8c84-148">Pattern</span></span>|<span data-ttu-id="d8c84-149">Popis</span><span class="sxs-lookup"><span data-stu-id="d8c84-149">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d8c84-150">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-150">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="d8c84-151">Určení, zda následující tři znaky jsou dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d8c84-151">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="d8c84-152">Pokud předchozí vzor odpovídá, porovná dvě číslice následované spojovníkem a 7 číslicemi.</span><span class="sxs-lookup"><span data-stu-id="d8c84-152">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="d8c84-153">Pokud předchozí vzorek neodpovídá, porovná tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.</span><span class="sxs-lookup"><span data-stu-id="d8c84-153">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="d8c84-154">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-154">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="d8c84-155">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d8c84-155">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="d8c84-156">Podmíněného přiřazování na základě platný zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="d8c84-156">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="d8c84-157">Tento prvek jazyka se pokusí porovnat jednu ze dvou vzorků v závislosti na tom, jestli má odpovídá zadané zachytávající skupiny.</span><span class="sxs-lookup"><span data-stu-id="d8c84-157">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="d8c84-158">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="d8c84-158">Its syntax is:</span></span>  
  
 <span data-ttu-id="d8c84-159">`(?(` *název* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="d8c84-159">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d8c84-160">or</span><span class="sxs-lookup"><span data-stu-id="d8c84-160">or</span></span>  
  
 <span data-ttu-id="d8c84-161">`(?(` *číslo* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="d8c84-161">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d8c84-162">kde *název* je název a *číslo* je počet zachytávající skupinu, *Ano* je výraz, který se shodují, pokud *název* nebo *číslo* shoduje, a *žádné* je volitelný výraz, který splněno, pokud tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="d8c84-162">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="d8c84-163">Pokud *název* neodpovídá názvu zachytávající skupinu, která se používá ve vzoru regulárního výrazu, alternace je interpretován jako test výrazu, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="d8c84-163">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="d8c84-164">Obvykle to znamená, že *výraz* vyhodnotí jako `false`.</span><span class="sxs-lookup"><span data-stu-id="d8c84-164">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="d8c84-165">Pokud *číslo* neodpovídá očíslovanou zachytávající skupinu, která se používá ve vzoru regulárního výrazu, vyvolá modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="d8c84-165">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="d8c84-166">Následující příklad je podobný příkladu, který se zobrazí [buď / nebo porovnávání vzorů s &#124; ](#Either_Or) oddílu.</span><span class="sxs-lookup"><span data-stu-id="d8c84-166">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="d8c84-167">Používá zachytávající skupina s názvem `n2` , která obsahuje dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d8c84-167">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="d8c84-168">Konstrukce alternace testuje, jestli tato zachytávající skupina pravá složená závorka ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="d8c84-168">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="d8c84-169">Pokud ano, bude se Alternující konstrukce pokusí se porovnat posledních 7 číslic devět číslic USA Zaměstnavatel identifikační číslo (EIN).</span><span class="sxs-lookup"><span data-stu-id="d8c84-169">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="d8c84-170">Pokud ne, pokusí se porovnat devět číslic USA Číslo sociálního pojištění (SSN).</span><span class="sxs-lookup"><span data-stu-id="d8c84-170">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="d8c84-171">Vzor regulárního výrazu `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d8c84-171">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d8c84-172">Vzor</span><span class="sxs-lookup"><span data-stu-id="d8c84-172">Pattern</span></span>|<span data-ttu-id="d8c84-173">Popis</span><span class="sxs-lookup"><span data-stu-id="d8c84-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d8c84-174">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-174">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="d8c84-175">Porovná žádný nebo jeden výskyt dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d8c84-175">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="d8c84-176">Název této zachytávající skupiny `n2`.</span><span class="sxs-lookup"><span data-stu-id="d8c84-176">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="d8c84-177">Test, zda `n2` odpovídal ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="d8c84-177">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="d8c84-178">Pokud `n2` byla shoda, porovná sedm desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="d8c84-178">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="d8c84-179">Pokud `n2` neodpovídá, odpovídá tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.</span><span class="sxs-lookup"><span data-stu-id="d8c84-179">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="d8c84-180">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8c84-180">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="d8c84-181">Variace tohoto příkladu, který používá číslované skupiny místo pojmenovanou skupinu se zobrazí v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d8c84-181">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="d8c84-182">Jeho vzor regulárního výrazu je `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="d8c84-182">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d8c84-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8c84-183">See also</span></span>

- [<span data-ttu-id="d8c84-184">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="d8c84-184">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
