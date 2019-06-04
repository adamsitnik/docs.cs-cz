---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: af704d00800a72b4ab670781c5bb3adec93683cb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489892"
---
# <a name="select-entity-sql"></a><span data-ttu-id="e34e8-102">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e34e8-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="e34e8-103">Určuje prvků vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="e34e8-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e34e8-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="e34e8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e34e8-105">Arguments</span></span>  
 <span data-ttu-id="e34e8-106">VŠECHNY</span><span class="sxs-lookup"><span data-stu-id="e34e8-106">ALL</span></span>  
 <span data-ttu-id="e34e8-107">Určuje, že duplicitní položky se zobrazí v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="e34e8-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="e34e8-108">VŠE je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="e34e8-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="e34e8-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="e34e8-109">DISTINCT</span></span>  
 <span data-ttu-id="e34e8-110">Určuje, že pouze jedinečné výsledky se zobrazí v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="e34e8-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="e34e8-111">HODNOTA</span><span class="sxs-lookup"><span data-stu-id="e34e8-111">VALUE</span></span>  
 <span data-ttu-id="e34e8-112">Umožňuje zadat, pouze jednu položku a nedojde k přidání na obálku řádek.</span><span class="sxs-lookup"><span data-stu-id="e34e8-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="e34e8-113">Libovolný platný výraz, který označuje počet prvních výsledků vrácených z dotazu ve formuláři `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="e34e8-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="e34e8-114">Parametr LIMIT [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operátor také vám umožní vybrat prvních n položek v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="e34e8-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="e34e8-115">Výraz ve tvaru:</span><span class="sxs-lookup"><span data-stu-id="e34e8-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="e34e8-116">`expr` jako `identifier`&#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="e34e8-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="e34e8-117">Literál nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="e34e8-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e34e8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e34e8-118">Remarks</span></span>  
 <span data-ttu-id="e34e8-119">Klauzule SELECT je vyhodnocen po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [Group](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), a [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) vyhodnocení klauzule.</span><span class="sxs-lookup"><span data-stu-id="e34e8-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="e34e8-120">Klauzule SELECT může odkazovat pouze na položky aktuálně oboru (z klauzule FROM nebo z vnějšího obory).</span><span class="sxs-lookup"><span data-stu-id="e34e8-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="e34e8-121">Pokud je zadaná klauzule GROUP BY, klauzule SELECT je povolena pouze tak, aby odkazovaly aliasy pro klíče GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="e34e8-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="e34e8-122">Odkazy na položky klauzule FROM je povolená jenom v agregačních funkcích.</span><span class="sxs-lookup"><span data-stu-id="e34e8-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="e34e8-123">Seznam jedné nebo více výrazů dotazu následující vyberte klíčové slovo se označuje jako seznamu příkazu select nebo formálně jako projekce.</span><span class="sxs-lookup"><span data-stu-id="e34e8-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="e34e8-124">Nejobecnější projekce má výraz jeden dotaz.</span><span class="sxs-lookup"><span data-stu-id="e34e8-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="e34e8-125">Pokud vyberete člen `member1` z kolekce `collection1`, vytvoří novou kolekci všech `member1` hodnoty pro každý objekt v `collection1`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e34e8-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="e34e8-126">Například pokud `customers` je kolekce typu `Customer` , který má vlastnost `Name` , který je typu `string`, kde vyberou `Name` z `customers` předá kolekce řetězců, jak je znázorněno v následujícím příkladu .</span><span class="sxs-lookup"><span data-stu-id="e34e8-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="e34e8-127">Je také možné použít syntaxi příkazu JOIN (FULL, vnitřní, vlevo, vnější, ON a vpravo).</span><span class="sxs-lookup"><span data-stu-id="e34e8-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="e34e8-128">Dále je třeba vnitřní spojení a je nChcete-li povolen křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="e34e8-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="e34e8-129">Řádek a hodnota klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="e34e8-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e34e8-130">podporuje dvě varianty klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="e34e8-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="e34e8-131">První varianta, vyberte řádek, je identifikován vyberte – klíčové slovo a je možné zadat jednu nebo více hodnot, které by měl použít k projekci navýšení kapacity. Protože obálka řádek je implicitně přidat kolem hodnoty vrácené, výsledek výrazu dotazu je vždy použita třída multiset řádků.</span><span class="sxs-lookup"><span data-stu-id="e34e8-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="e34e8-132">Každý výraz dotazu, vyberte řádek zadejte alias.</span><span class="sxs-lookup"><span data-stu-id="e34e8-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="e34e8-133">Pokud není zadán žádný alias,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat alias pomocí pravidel pro vytvoření aliasu.</span><span class="sxs-lookup"><span data-stu-id="e34e8-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="e34e8-134">Varianta klauzuli SELECT, vyberte hodnotu, je identifikován – klíčové slovo SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="e34e8-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="e34e8-135">Umožňuje pouze jednu hodnotu, chcete-li zadán a nedojde k přidání řádku obálku.</span><span class="sxs-lookup"><span data-stu-id="e34e8-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="e34e8-136">Vyberte řádek je vždy anyAttribute z hlediska hodnota vyberte, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e34e8-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="e34e8-137">Všechny a odlišné modifikátory</span><span class="sxs-lookup"><span data-stu-id="e34e8-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="e34e8-138">Obě varianty, vyberte v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] povolit specifikaci všechny nebo odlišné modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e34e8-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="e34e8-139">Pokud je zadán odlišné modifikátor, duplicitní položky zanikne brány v kolekci vytvořenou testovaným výrazu dotazu (až po a včetně klauzule SELECT).</span><span class="sxs-lookup"><span data-stu-id="e34e8-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="e34e8-140">Pokud se všechny modifikátor tyto informace zadané, ne duplicitní vyloučení se provádí; VŠE je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="e34e8-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="e34e8-141">Rozdíly v Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e34e8-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="e34e8-142">Na rozdíl od příkazů jazyka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje použití \* argument v klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="e34e8-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="e34e8-143">Místo toho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje vytvářet dotazy do projektu si celých záznamů pomocí odkazu na kolekci aliasy z klauzule FROM, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e34e8-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="e34e8-144">Předchozí výraz dotazu jazyka Transact-SQL je vyjádřen v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e34e8-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="e34e8-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="e34e8-145">Example</span></span>  
 <span data-ttu-id="e34e8-146">Následující dotaz Entity SQL vyberte operátor, který se používá k určení prvků vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="e34e8-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="e34e8-147">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e34e8-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e34e8-148">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="e34e8-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e34e8-149">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e34e8-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e34e8-150">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e34e8-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="e34e8-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e34e8-151">See also</span></span>

- [<span data-ttu-id="e34e8-152">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="e34e8-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="e34e8-153">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e34e8-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e34e8-154">TOP</span><span class="sxs-lookup"><span data-stu-id="e34e8-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
