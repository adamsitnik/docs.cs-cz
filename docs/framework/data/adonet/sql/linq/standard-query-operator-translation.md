---
title: Převod standardních operátorů dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 280557a5098c513111557f52d835b20d9a2eeb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876877"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="26648-102">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="26648-102">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-103">Standardní operátory dotazu se přeloží na příkazy jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="26648-103">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="26648-104">Procesor dotazů databáze určuje sémantika provádění SQL překladu.</span><span class="sxs-lookup"><span data-stu-id="26648-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="26648-105">Standardní operátoři dotazu jsou definováni proti *pořadí*.</span><span class="sxs-lookup"><span data-stu-id="26648-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="26648-106">Sekvence je *seřazené* a spoléhá na referenční identitě pro každý prvek pořadí.</span><span class="sxs-lookup"><span data-stu-id="26648-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="26648-107">Další informace najdete v tématu [přehled standardních operátorů dotazu (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) nebo [přehled operátory standardního dotazu (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="26648-107">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="26648-108">SQL se především se týká *neuspořádaná sady hodnot*.</span><span class="sxs-lookup"><span data-stu-id="26648-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="26648-109">Řazení je obvykle výslovně uvedeno, následné zpracování operace, která se použije na výsledek dotazu, nikoli mezilehlých výsledků.</span><span class="sxs-lookup"><span data-stu-id="26648-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="26648-110">Identita je definovaná pomocí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="26648-110">Identity is defined by values.</span></span> <span data-ttu-id="26648-111">Z tohoto důvodu jsou dotazy SQL pochopitelné řešit multisets (*kontejnery objektů a dat*) namísto *nastaví*.</span><span class="sxs-lookup"><span data-stu-id="26648-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="26648-112">Následující odstavce popisují rozdíly mezi standardní operátory dotazu a jejich překlad SQL pro zprostředkovatel SQL Server pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="26648-113">Podpora – operátor</span><span class="sxs-lookup"><span data-stu-id="26648-113">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="26648-114">concat</span><span class="sxs-lookup"><span data-stu-id="26648-114">Concat</span></span>

<span data-ttu-id="26648-115"><xref:System.Linq.Enumerable.Concat%2A> Metoda je definována pro uspořádaný multisets, kde příjemce a pořadím argumentu shodují.</span><span class="sxs-lookup"><span data-stu-id="26648-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="26648-116"><xref:System.Linq.Enumerable.Concat%2A> funguje jako `UNION ALL` přes multisets, za nímž následuje běžné pořadí.</span><span class="sxs-lookup"><span data-stu-id="26648-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="26648-117">Posledním krokem je řazení SQL předtím, než se produkují výsledky.</span><span class="sxs-lookup"><span data-stu-id="26648-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="26648-118"><xref:System.Linq.Enumerable.Concat%2A> Nezachovávat hodnotu pořadí z jejích argumentů.</span><span class="sxs-lookup"><span data-stu-id="26648-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="26648-119">Aby odpovídající řazení, musí explicitně řazení výsledků <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="26648-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="26648-120">Intersect, s výjimkou sjednocení</span><span class="sxs-lookup"><span data-stu-id="26648-120">Intersect, Except, Union</span></span>

<span data-ttu-id="26648-121"><xref:System.Linq.Enumerable.Intersect%2A> a <xref:System.Linq.Enumerable.Except%2A> metody jsou pouze na sady dobře definované.</span><span class="sxs-lookup"><span data-stu-id="26648-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="26648-122">Sémantika pro multisets není definován.</span><span class="sxs-lookup"><span data-stu-id="26648-122">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="26648-123"><xref:System.Linq.Enumerable.Union%2A> Je definována metoda pro multisets jako Neseřazený zřetězení multisets (efektivně výsledek klauzuli UNION ALL v SQL).</span><span class="sxs-lookup"><span data-stu-id="26648-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="26648-124">Take, Skip</span><span class="sxs-lookup"><span data-stu-id="26648-124">Take, Skip</span></span>

<span data-ttu-id="26648-125"><xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> metody jsou dobře definované pouze proti *seřazené sady*.</span><span class="sxs-lookup"><span data-stu-id="26648-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="26648-126">Sémantika pro Neseřazený sady nebo multisets nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="26648-126">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="26648-127"><xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když se používají v dotazech pro SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="26648-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="26648-128">Další informace najdete v tématu "Přeskočit a převzít výjimky v systému SQL Server 2000" položka v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="26648-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>

<span data-ttu-id="26648-129">Z důvodu omezení řazení SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout řazení argument z těchto metod na výsledek metody.</span><span class="sxs-lookup"><span data-stu-id="26648-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="26648-130">Představte si třeba následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu:</span><span class="sxs-lookup"><span data-stu-id="26648-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="26648-131">Vygenerovaný SQL pro tento kód přesune řazení do konce a následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="26648-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="26648-132">Je zřejmé, že všechny zadané řazení musí být konzistentní při <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> jsou zřetězen dohromady.</span><span class="sxs-lookup"><span data-stu-id="26648-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="26648-133">V opačném případě nejsou výsledky definovány.</span><span class="sxs-lookup"><span data-stu-id="26648-133">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="26648-134">Obě <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> jsou jasně definované pro záporná, konstantní celočíselné argumenty, které jsou založené na specifikaci standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="26648-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="26648-135">Operátory se žádný překlad</span><span class="sxs-lookup"><span data-stu-id="26648-135">Operators with No Translation</span></span>

<span data-ttu-id="26648-136">Následující metody nepřekládá podle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="26648-137">Nejběžnějším důvodem je rozdíl mezi Neseřazený multisets a pořadí.</span><span class="sxs-lookup"><span data-stu-id="26648-137">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="26648-138">Operátory</span><span class="sxs-lookup"><span data-stu-id="26648-138">Operators</span></span>|<span data-ttu-id="26648-139">Důvody</span><span class="sxs-lookup"><span data-stu-id="26648-139">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="26648-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="26648-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="26648-141">Dotazy SQL pracují s multisets, ne podle pořadí.</span><span class="sxs-lookup"><span data-stu-id="26648-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="26648-142">`ORDER BY` je nutné poslední klauzule použít na výsledky.</span><span class="sxs-lookup"><span data-stu-id="26648-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="26648-143">Z tohoto důvodu neexistuje žádný překlad pro obecné účely pro tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="26648-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="26648-144">Překlad tuto metodu je možné seřazené sady, ale není aktuálně přeložit modulem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="26648-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="26648-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="26648-146">Převod z těchto metod je možné seřazené sady, ale není aktuálně přeložit modulem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="26648-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="26648-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="26648-148">Dotazy SQL pracují s multisets, ne na indexovanou pořadí.</span><span class="sxs-lookup"><span data-stu-id="26648-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="26648-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (přetížení s výchozí argument)</span><span class="sxs-lookup"><span data-stu-id="26648-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="26648-150">Obecně platí nelze zadat výchozí hodnotu pro libovolný záznam.</span><span class="sxs-lookup"><span data-stu-id="26648-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="26648-151">Hodnoty Null pro řazené kolekce členů je možné v některých případech prostřednictvím vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="26648-151">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="26648-152">Výraz posunutí</span><span class="sxs-lookup"><span data-stu-id="26648-152">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="26648-153">Sémantika s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="26648-153">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-154">nepředstavuje sémantiku porovnání null v SQL.</span><span class="sxs-lookup"><span data-stu-id="26648-154">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="26648-155">Operátory porovnání jsou syntakticky převedeny na jejich ekvivalenty SQL.</span><span class="sxs-lookup"><span data-stu-id="26648-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="26648-156">Z tohoto důvodu odrážet sémantiku sémantiku SQL, který se definuje na základě nastavení serveru nebo připojení.</span><span class="sxs-lookup"><span data-stu-id="26648-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="26648-157">Například dvě hodnoty null se považují za nestejné podle výchozího nastavení systému SQL Server, ale můžete změnit nastavení, chcete-li změnit sémantiku.</span><span class="sxs-lookup"><span data-stu-id="26648-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-158">nebere v úvahu nastavení serveru při překládá dotazy.</span><span class="sxs-lookup"><span data-stu-id="26648-158">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="26648-159">Porovnání s literál null se přeloží na odpovídající verzi SQL (`is null` nebo `is not null`).</span><span class="sxs-lookup"><span data-stu-id="26648-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="26648-160">Hodnota `null` kolace je určené systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="26648-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-161">nedojde ke změně kolace.</span><span class="sxs-lookup"><span data-stu-id="26648-161">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="26648-162">Agregace</span><span class="sxs-lookup"><span data-stu-id="26648-162">Aggregates</span></span>

<span data-ttu-id="26648-163">Metoda standardního operátoru dotazu aggregate <xref:System.Linq.Enumerable.Sum%2A> vyhodnocen jako nula k prázdné sekvenci nebo sekvenci, která obsahuje pouze hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="26648-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="26648-164">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechány beze změny, a <xref:System.Linq.Enumerable.Sum%2A> vyhodnotí jako `null` místo nula k prázdné sekvenci nebo sekvenci, která obsahuje pouze hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="26648-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="26648-165">Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="26648-166"><xref:System.Linq.Enumerable.Sum%2A> 32-bit integer není počítaný množství pomocí 64-bit výsledky.</span><span class="sxs-lookup"><span data-stu-id="26648-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="26648-167">Přetečení může dojít k pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad <xref:System.Linq.Enumerable.Sum%2A>i v případě implementace standardní operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.</span><span class="sxs-lookup"><span data-stu-id="26648-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="26648-168">Podobně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad <xref:System.Linq.Enumerable.Average%2A> celého čísla je vypočítán hodnoty jako `integer`, ne jako `double`.</span><span class="sxs-lookup"><span data-stu-id="26648-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="26648-169">Argumenty entity</span><span class="sxs-lookup"><span data-stu-id="26648-169">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-170">Umožňuje typy entit, který se má použít v <xref:System.Linq.Enumerable.GroupBy%2A> a <xref:System.Linq.Enumerable.OrderBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="26648-170">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="26648-171">V překladu těchto operátorů použijte argument typu je považovány za ekvivalentní se zadáním všechny členy tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="26648-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="26648-172">Například následující kód je ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="26648-172">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="26648-173">Equatable / srovnatelné argumenty</span><span class="sxs-lookup"><span data-stu-id="26648-173">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="26648-174">Rovnost hodnoty argumentů se vyžaduje k provedení následujících metod:</span><span class="sxs-lookup"><span data-stu-id="26648-174">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-175">podporuje rovnosti a porovnání pro *plochý* argumenty, ale ne pro argumenty, které jsou nebo obsahovat sekvence.</span><span class="sxs-lookup"><span data-stu-id="26648-175">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="26648-176">Plochý argumentu je typ, který je možné mapovat na řádku SQL.</span><span class="sxs-lookup"><span data-stu-id="26648-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="26648-177">Projekce jednoho nebo více typů entit, které se dá určit staticky neobsahují sekvenci se považuje za argumentem bez stromové struktury.</span><span class="sxs-lookup"><span data-stu-id="26648-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="26648-178">Následuje několik příkladů argumentů bez stromové struktury:</span><span class="sxs-lookup"><span data-stu-id="26648-178">Following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="26648-179">Následují příklady argumenty jiných ploché (hierarchické).</span><span class="sxs-lookup"><span data-stu-id="26648-179">The following are examples of non-flat (hierarchical) arguments.</span></span>

[!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="26648-180">Funkce převodu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26648-180">Visual Basic Function Translation</span></span>

<span data-ttu-id="26648-181">Následující pomocná funkce, které se používají v kompilátoru jazyka Visual Basic jsou přeloženy na odpovídající SQL operátory a funkce:</span><span class="sxs-lookup"><span data-stu-id="26648-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="26648-182">Převod metody:</span><span class="sxs-lookup"><span data-stu-id="26648-182">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="26648-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="26648-183">ToBoolean</span></span>|<span data-ttu-id="26648-184">Tosbyte –</span><span class="sxs-lookup"><span data-stu-id="26648-184">ToSByte</span></span>|<span data-ttu-id="26648-185">Tobyte –</span><span class="sxs-lookup"><span data-stu-id="26648-185">ToByte</span></span>|<span data-ttu-id="26648-186">Tochar –</span><span class="sxs-lookup"><span data-stu-id="26648-186">ToChar</span></span>|
|<span data-ttu-id="26648-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="26648-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="26648-188">Do data</span><span class="sxs-lookup"><span data-stu-id="26648-188">ToDate</span></span>|<span data-ttu-id="26648-189">Todecimal –</span><span class="sxs-lookup"><span data-stu-id="26648-189">ToDecimal</span></span>|<span data-ttu-id="26648-190">Todouble –</span><span class="sxs-lookup"><span data-stu-id="26648-190">ToDouble</span></span>|
|<span data-ttu-id="26648-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="26648-191">ToInteger</span></span>|<span data-ttu-id="26648-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="26648-192">ToUInteger</span></span>|<span data-ttu-id="26648-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="26648-193">ToLong</span></span>|<span data-ttu-id="26648-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="26648-194">ToULong</span></span>|
|<span data-ttu-id="26648-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="26648-195">ToShort</span></span>|<span data-ttu-id="26648-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="26648-196">ToUShort</span></span>|<span data-ttu-id="26648-197">Tosingle –</span><span class="sxs-lookup"><span data-stu-id="26648-197">ToSingle</span></span>|<span data-ttu-id="26648-198">ToString</span><span class="sxs-lookup"><span data-stu-id="26648-198">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="26648-199">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="26648-199">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="26648-200">Omezení pro mapování dědičnosti</span><span class="sxs-lookup"><span data-stu-id="26648-200">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="26648-201">Další informace najdete v tématu [jak: Mapování hierarchií dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="26648-201">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="26648-202">Dědičnost v dotazech</span><span class="sxs-lookup"><span data-stu-id="26648-202">Inheritance in Queries</span></span>

<span data-ttu-id="26648-203">Přetypování C# jsou podporovány pouze v projekci.</span><span class="sxs-lookup"><span data-stu-id="26648-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="26648-204">Přetypování, které se používají jinde nepřekládá a budou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="26648-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="26648-205">Kromě SQL názvy funkcí, SQL ve skutečnosti provádí pouze ekvivalent modulu common language runtime (CLR) <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="26648-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="26648-206">To znamená SQL, můžete změnit hodnoty jednoho typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="26648-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="26648-207">Neexistuje žádný ekvivalent přetypování, protože neexistuje žádný koncept opětovná interpretace bity stejné jako u jiného typu CLR.</span><span class="sxs-lookup"><span data-stu-id="26648-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="26648-208">To je důvod, proč a C# přetypování funguje jenom místně.</span><span class="sxs-lookup"><span data-stu-id="26648-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="26648-209">Není vzdálený.</span><span class="sxs-lookup"><span data-stu-id="26648-209">It is not remoted.</span></span>

<span data-ttu-id="26648-210">Operátory, `is` a `as`a `GetType` metoda nejsou omezeni `Select` operátor.</span><span class="sxs-lookup"><span data-stu-id="26648-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="26648-211">Jejich lze použít v jiných operátorů dotazu také.</span><span class="sxs-lookup"><span data-stu-id="26648-211">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="26648-212">SQL Server 2008 Support</span><span class="sxs-lookup"><span data-stu-id="26648-212">SQL Server 2008 Support</span></span>

<span data-ttu-id="26648-213">Počínaje rozhraním .NET Framework 3.5 SP1, LINQ to SQL podporuje mapování na nové datum a čas typy zavedena v systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="26648-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="26648-214">Existují ale určitá omezení do technologie LINQ to SQL operátorů dotazu, které můžete použít při práci s hodnotami, které jsou namapované na tyto nové typy.</span><span class="sxs-lookup"><span data-stu-id="26648-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="26648-215">Dotaz se nepodporuje operátory</span><span class="sxs-lookup"><span data-stu-id="26648-215">Unsupported Query Operators</span></span>

<span data-ttu-id="26648-216">Následující operátory dotazu nejsou podporovány u hodnot, které jsou namapované na nové typy data a času systému SQL Server: `DATETIME2`, `DATE`, `TIME`, a `DATETIMEOFFSET`.</span><span class="sxs-lookup"><span data-stu-id="26648-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="26648-217">Další informace o mapování pro tyto typy data a času systému SQL Server najdete v tématu [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="26648-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="26648-218">SQL Server 2005 Support</span><span class="sxs-lookup"><span data-stu-id="26648-218">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-219">nepodporuje následující funkce SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="26648-219">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="26648-220">Uložené procedury napsané pro SQL CLR.</span><span class="sxs-lookup"><span data-stu-id="26648-220">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="26648-221">Uživatelem definovaného typu.</span><span class="sxs-lookup"><span data-stu-id="26648-221">User-defined type.</span></span>

- <span data-ttu-id="26648-222">Funkce dotazu XML.</span><span class="sxs-lookup"><span data-stu-id="26648-222">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="26648-223">SQL Server 2000 Support</span><span class="sxs-lookup"><span data-stu-id="26648-223">SQL Server 2000 Support</span></span>

<span data-ttu-id="26648-224">Následující [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] omezení (ve srovnání s [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporovat.</span><span class="sxs-lookup"><span data-stu-id="26648-224">The following [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] limitations (compared to [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="26648-225">Křížové použití a vnější použít operátory</span><span class="sxs-lookup"><span data-stu-id="26648-225">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="26648-226">Tyto operátory nejsou k dispozici v [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-226">These operators are not available in [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="26648-227">se pokusí řadu přepisů pro jejich nahrazení odpovídající spojení.</span><span class="sxs-lookup"><span data-stu-id="26648-227">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="26648-228">`Cross Apply` a `Outer Apply` jsou generovány pro navigaci vztah.</span><span class="sxs-lookup"><span data-stu-id="26648-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="26648-229">Sadu dotazů, pro které je možné takové přepisů není dobře definováno.</span><span class="sxs-lookup"><span data-stu-id="26648-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="26648-230">Z tohoto důvodu minimální sadu dotazů, které je podporováno pro [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] je sada, která nezahrnuje vztah navigace.</span><span class="sxs-lookup"><span data-stu-id="26648-230">For this reason, the minimal set of queries that is supported for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="26648-231">text / ntext</span><span class="sxs-lookup"><span data-stu-id="26648-231">text / ntext</span></span>

<span data-ttu-id="26648-232">Datové typy `text`  /  `ntext` nelze použít v určité operace dotazů vůči `varchar(max)`  /  `nvarchar(max)`, které jsou podporovány [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span></span>

<span data-ttu-id="26648-233">Žádné řešení, protože je k dispozici pro toto omezení.</span><span class="sxs-lookup"><span data-stu-id="26648-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="26648-234">Konkrétně byste měli nelze použít `Distinct()` na některý z výsledků, který obsahuje členy, které jsou mapovány na `text` nebo `ntext` sloupce.</span><span class="sxs-lookup"><span data-stu-id="26648-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="26648-235">Chování aktivuje vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="26648-235">Behavior Triggered by Nested Queries</span></span>

[!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] <span data-ttu-id="26648-236">(prostřednictvím SP4) má vazač některá specifika, které jsou aktivovány vnořené dotazy.</span><span class="sxs-lookup"><span data-stu-id="26648-236">(through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="26648-237">Sadu dotazů SQL, který spouští tyto specifika není dobře definováno.</span><span class="sxs-lookup"><span data-stu-id="26648-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="26648-238">Z tohoto důvodu nelze definovat sadu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy, které může způsobit, že výjimky serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="26648-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="26648-239">Přeskočit a převzít operátory</span><span class="sxs-lookup"><span data-stu-id="26648-239">Skip and Take Operators</span></span>

<span data-ttu-id="26648-240"><xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když se používají v dotazech proti [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26648-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> <span data-ttu-id="26648-241">Další informace najdete v tématu "Přeskočit a převzít výjimky v systému SQL Server 2000" položka v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="26648-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="26648-242">Materializace objektů</span><span class="sxs-lookup"><span data-stu-id="26648-242">Object Materialization</span></span>

<span data-ttu-id="26648-243">Materializace vytvoří objekty CLR z řádků, které jsou vráceny dotazy SQL jeden nebo více.</span><span class="sxs-lookup"><span data-stu-id="26648-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="26648-244">Následující volání jsou *spuštěn lokálně* jako součást materializace:</span><span class="sxs-lookup"><span data-stu-id="26648-244">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="26648-245">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="26648-245">Constructors</span></span>

  - <span data-ttu-id="26648-246">`ToString` metody v projekce</span><span class="sxs-lookup"><span data-stu-id="26648-246">`ToString` methods in projections</span></span>

  - <span data-ttu-id="26648-247">Přetypování typu v projekce</span><span class="sxs-lookup"><span data-stu-id="26648-247">Type casts in projections</span></span>

- <span data-ttu-id="26648-248">Metody, které následují <xref:System.Linq.Enumerable.AsEnumerable%2A> metodu *spuštěn lokálně*.</span><span class="sxs-lookup"><span data-stu-id="26648-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="26648-249">Tato metoda nezpůsobí okamžité spuštění.</span><span class="sxs-lookup"><span data-stu-id="26648-249">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="26648-250">Můžete použít `struct` jako návratový typ výsledku dotazu, nebo jako člen typu výsledku.</span><span class="sxs-lookup"><span data-stu-id="26648-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="26648-251">Entity jsou musí být třídy.</span><span class="sxs-lookup"><span data-stu-id="26648-251">Entities are required to be classes.</span></span> <span data-ttu-id="26648-252">Anonymní typy jsou vyhodnocena jako instance třídy, ale pojmenované struktury (jiné entity) lze použít v projekci.</span><span class="sxs-lookup"><span data-stu-id="26648-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="26648-253">Člen návratový typ výsledku dotazu nemůže být typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="26648-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="26648-254">Je vyhodnocena jako místní kolekce.</span><span class="sxs-lookup"><span data-stu-id="26648-254">It is materialized as a local collection.</span></span>

- <span data-ttu-id="26648-255">Následující metody způsobit, že *okamžité materializace* sekvence, která se použijí metody pro:</span><span class="sxs-lookup"><span data-stu-id="26648-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="26648-256">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26648-256">See also</span></span>

- [<span data-ttu-id="26648-257">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="26648-257">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="26648-258">Vrácení nebo přeskočení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="26648-258">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="26648-259">Zřetězení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="26648-259">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)
- [<span data-ttu-id="26648-260">Vrácení rozdílů množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="26648-260">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="26648-261">Vrácení průniku množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="26648-261">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="26648-262">Vrácení sjednocení množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="26648-262">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
