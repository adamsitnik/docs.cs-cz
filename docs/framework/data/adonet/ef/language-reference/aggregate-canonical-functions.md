---
title: Agregační kanonické funkce
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: f5d3584c6e9d35c9eb69b4f54cad45187416ee59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607450"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="e8fa7-102">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="e8fa7-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="e8fa7-103">Agregace jsou výrazy, které snižují řadu vstupní hodnoty do například jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="e8fa7-104">Agregace se obvykle používají ve spojení s klauzulí GROUP BY vyberte výrazu a existují omezení ve kterém můžou použít.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="e8fa7-105">Agregační kanonické funkce Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e8fa7-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="e8fa7-106">Následují agregační kanonické funkce Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="e8fa7-107">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-107">Avg(expression)</span></span>

<span data-ttu-id="e8fa7-108">Vrátí průměrnou hodnotu hodnot jiných než null.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="e8fa7-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-109">**Arguments**</span></span>

<span data-ttu-id="e8fa7-110">`Int32`, `Int64`, `Double`, A `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="e8fa7-111">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-111">**Return Value**</span></span>

<span data-ttu-id="e8fa7-112">Typ `expression`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-113">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="e8fa7-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-114">BigCount(expression)</span></span>

<span data-ttu-id="e8fa7-115">Vrátí velikost položky agregace, včetně hodnotu null a duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="e8fa7-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-116">**Arguments**</span></span>

<span data-ttu-id="e8fa7-117">Libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-117">Any type.</span></span>

<span data-ttu-id="e8fa7-118">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-118">**Return Value**</span></span>

<span data-ttu-id="e8fa7-119">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-119">An `Int64`.</span></span>

<span data-ttu-id="e8fa7-120">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="e8fa7-121">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-121">Count(expression)</span></span>

<span data-ttu-id="e8fa7-122">Vrátí velikost položky agregace, včetně hodnotu null a duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="e8fa7-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-123">**Arguments**</span></span>

<span data-ttu-id="e8fa7-124">Libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-124">Any type.</span></span>

<span data-ttu-id="e8fa7-125">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-125">**Return Value**</span></span>

<span data-ttu-id="e8fa7-126">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-126">An `Int32`.</span></span>

<span data-ttu-id="e8fa7-127">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="e8fa7-128">Max(Expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-128">Max(expression)</span></span>

<span data-ttu-id="e8fa7-129">Vrátí maximální hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="e8fa7-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-130">**Arguments**</span></span>

<span data-ttu-id="e8fa7-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="e8fa7-132">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-132">**Return Value**</span></span>

<span data-ttu-id="e8fa7-133">Typ `expression`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-134">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="e8fa7-135">Min(Expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-135">Min(expression)</span></span>

<span data-ttu-id="e8fa7-136">Vrátí minimální hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="e8fa7-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-137">**Arguments**</span></span>

<span data-ttu-id="e8fa7-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="e8fa7-139">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-139">**Return Value**</span></span>

<span data-ttu-id="e8fa7-140">Typ `expression`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-141">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="e8fa7-142">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-142">StDev(expression)</span></span>

<span data-ttu-id="e8fa7-143">Vrátí směrodatnou odchylku nenulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="e8fa7-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-144">**Arguments**</span></span>

<span data-ttu-id="e8fa7-145">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="e8fa7-146">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-146">**Return Value**</span></span>

<span data-ttu-id="e8fa7-147">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-147">A `Double`.</span></span> <span data-ttu-id="e8fa7-148">`Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-149">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="e8fa7-150">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-150">StDevP(expression)</span></span>

<span data-ttu-id="e8fa7-151">Vrací směrodatnou odchylku základního souboru hodnot.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="e8fa7-152">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-152">**Arguments**</span></span>

<span data-ttu-id="e8fa7-153">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="e8fa7-154">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-154">**Return Value**</span></span>

<span data-ttu-id="e8fa7-155">A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-156">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="e8fa7-157">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-157">Sum(expression)</span></span>

<span data-ttu-id="e8fa7-158">Vrátí součet hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="e8fa7-159">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-159">**Arguments**</span></span>

<span data-ttu-id="e8fa7-160">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="e8fa7-161">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-161">**Return Value**</span></span>

<span data-ttu-id="e8fa7-162">A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-163">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="e8fa7-164">Var(Expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-164">Var(expression)</span></span>

<span data-ttu-id="e8fa7-165">Vrací odchylku všech hodnot jiných než null.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="e8fa7-166">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-166">**Arguments**</span></span>

<span data-ttu-id="e8fa7-167">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="e8fa7-168">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-168">**Return Value**</span></span>

<span data-ttu-id="e8fa7-169">A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-170">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="e8fa7-171">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="e8fa7-171">VarP(expression)</span></span>

<span data-ttu-id="e8fa7-172">Vrací odchylku pro naplnění všechny nenulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="e8fa7-173">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-173">**Arguments**</span></span>

<span data-ttu-id="e8fa7-174">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="e8fa7-175">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-175">**Return Value**</span></span>

<span data-ttu-id="e8fa7-176">A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="e8fa7-177">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e8fa7-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="e8fa7-178">Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="e8fa7-179">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e8fa7-179">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="e8fa7-180">Na základě kolekce agregace</span><span class="sxs-lookup"><span data-stu-id="e8fa7-180">Collection-based aggregates</span></span>

<span data-ttu-id="e8fa7-181">Na základě kolekce agregace (kolekce funkcí) pracovat s kolekcí a vracet hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="e8fa7-182">Například pokud objednávky je kolekce všechny objednávky, můžete vypočítat datum příjemce se následující výraz:</span><span class="sxs-lookup"><span data-stu-id="e8fa7-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="e8fa7-183">Výrazy v kolekci na základě agregace jsou vyhodnocovány v aktuálním oboru okolí překlad názvů.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="e8fa7-184">Agregace na základě skupin</span><span class="sxs-lookup"><span data-stu-id="e8fa7-184">Group-based aggregates</span></span>

<span data-ttu-id="e8fa7-185">Agregace na základě skupin se počítá v průběhu skupiny definované v klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="e8fa7-186">Pro každou skupinu ve výsledku se počítá samostatné agregace pomocí elementů v každé skupině jako vstup do agregačního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="e8fa7-187">Při použití klauzule group by ve výrazu select může být k dispozici v projekci nebo order by – klauzule pouze seskupení názvy výrazů, agregace nebo konstantní výrazy.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="e8fa7-188">Následující příklad vypočítá průměrné množství, řazení pro jednotlivé produkty:</span><span class="sxs-lookup"><span data-stu-id="e8fa7-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="e8fa7-189">Je možné mít agregace podle skupiny bez klauzule explicitní Group ve výrazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="e8fa7-190">V takovém případě všechny prvky jsou považovány za jednu skupinu.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="e8fa7-191">To je ekvivalentní zadání seskupení založené na konstantu.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="e8fa7-192">Vezměme si jako příklad následující výraz:</span><span class="sxs-lookup"><span data-stu-id="e8fa7-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="e8fa7-193">To je ekvivalentní následujícímu zápisu:</span><span class="sxs-lookup"><span data-stu-id="e8fa7-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="e8fa7-194">Uvnitř agregace skupinové výrazy jsou vyhodnocovány v rámci oboru rozlišení názvů, které se staly viditelnými pro výraz klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="e8fa7-195">Stejně jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], na základě skupin agregace můžete také určit všechny nebo odlišné modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-195">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="e8fa7-196">Pokud není zadána odlišné modifikátor, duplicitní položky zanikne brány v agregační vstupní kolekce předtím, než je vypočítán agregace.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="e8fa7-197">Pokud je zadán modifikátorem všechny (nebo pokud není zadán žádný modifikátor), bez odstranění duplicit se provádí.</span><span class="sxs-lookup"><span data-stu-id="e8fa7-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8fa7-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8fa7-198">See also</span></span>

- [<span data-ttu-id="e8fa7-199">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="e8fa7-199">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
