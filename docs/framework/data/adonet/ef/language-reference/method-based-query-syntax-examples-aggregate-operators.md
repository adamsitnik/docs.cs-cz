---
title: 'Příklady syntaxe dotazů založených na volání metody: Agregační operátory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 69bc2d1ae64ee4aaa016a70f6b46ac1f26dcf563
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825560"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="1cd9b-102">Příklady syntaxe dotazů založených na volání metody: Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="1cd9b-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="1cd9b-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="1cd9b-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1cd9b-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="1cd9b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="1cd9b-106">Průměr</span><span class="sxs-lookup"><span data-stu-id="1cd9b-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="1cd9b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-107">Example</span></span>  
 <span data-ttu-id="1cd9b-108">V následujícím příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznamu produktů.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-109">Example</span></span>  
 <span data-ttu-id="1cd9b-110">V následujícím příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-111">Example</span></span>  
 <span data-ttu-id="1cd9b-112">V následujícím příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrné celkové potřebné.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-113">Example</span></span>  
 <span data-ttu-id="1cd9b-114">V následujícím příkladu <xref:System.Linq.Enumerable.Average%2A> ID metodu k získání celkové potřebné průměr pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-115">Example</span></span>  
 <span data-ttu-id="1cd9b-116">V následujícím příkladu <xref:System.Linq.Enumerable.Average%2A> metodu k získání celkové potřebné objednávky s průměrem každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="1cd9b-117">Počet</span><span class="sxs-lookup"><span data-stu-id="1cd9b-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="1cd9b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-118">Example</span></span>  
 <span data-ttu-id="1cd9b-119">V následujícím příkladu <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů v tabulce Product.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-120">Example</span></span>  
 <span data-ttu-id="1cd9b-121">V následujícím příkladu <xref:System.Linq.Enumerable.Count%2A> metoda vrátí seznam ID kontaktu a kolik objednávky, každá má.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-122">Example</span></span>  
 <span data-ttu-id="1cd9b-123">Následující příklad skupiny produktů pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů v každé skupině barvu.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="1cd9b-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="1cd9b-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="1cd9b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-125">Example</span></span>  
 <span data-ttu-id="1cd9b-126">Následující příklad získá kontaktní počet jako dlouhé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="1cd9b-127">Maximum</span><span class="sxs-lookup"><span data-stu-id="1cd9b-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="1cd9b-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-128">Example</span></span>  
 <span data-ttu-id="1cd9b-129">V následujícím příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší celková částka.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-130">Example</span></span>  
 <span data-ttu-id="1cd9b-131">V následujícím příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-132">Example</span></span>  
 <span data-ttu-id="1cd9b-133">V následujícím příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání s největší celková částka objednávky pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="1cd9b-134">Minimum</span><span class="sxs-lookup"><span data-stu-id="1cd9b-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="1cd9b-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-135">Example</span></span>  
 <span data-ttu-id="1cd9b-136">V následujícím příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší celková částka.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-137">Example</span></span>  
 <span data-ttu-id="1cd9b-138">V následujícím příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-139">Example</span></span>  
 <span data-ttu-id="1cd9b-140">V následujícím příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávky nejmenší celkem termín pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="1cd9b-141">Součet</span><span class="sxs-lookup"><span data-stu-id="1cd9b-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="1cd9b-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-142">Example</span></span>  
 <span data-ttu-id="1cd9b-143">V následujícím příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového počtu množství objednávek v tabulce Podrobnosti prodejní objednávky.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1cd9b-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd9b-144">Example</span></span>  
 <span data-ttu-id="1cd9b-145">V následujícím příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkové termín pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="1cd9b-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1cd9b-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1cd9b-146">See also</span></span>
- [<span data-ttu-id="1cd9b-147">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1cd9b-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
