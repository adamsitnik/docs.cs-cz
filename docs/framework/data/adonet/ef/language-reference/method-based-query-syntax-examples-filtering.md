---
title: 'Příklady syntaxe dotazů založených na volání metody: Filtrování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: 8bc8f46a1afa6afad0b1893dfd0f09878be0e7a2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397467"
---
# <a name="method-based-query-syntax-examples-filtering"></a><span data-ttu-id="7a809-102">Příklady syntaxe dotazů založených na volání metody: Filtrování</span><span class="sxs-lookup"><span data-stu-id="7a809-102">Method-Based Query Syntax Examples: Filtering</span></span>
<span data-ttu-id="7a809-103">Příklady v tomto tématu ukazují, jak používat `Where` metody a `Where…Contains` k dotazování [modelu prodeje společnosti AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="7a809-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="7a809-104">Poznámka, kde...`Contains`</span><span class="sxs-lookup"><span data-stu-id="7a809-104">Note, Where…`Contains`</span></span> <span data-ttu-id="7a809-105">nelze použít jako součást [zkompilovaného dotazu](compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="7a809-105">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="7a809-106">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7a809-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7a809-107">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="7a809-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="7a809-108">Where</span><span class="sxs-lookup"><span data-stu-id="7a809-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="7a809-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a809-109">Example</span></span>  
 <span data-ttu-id="7a809-110">Následující příklad vrátí všechny online objednávky.</span><span class="sxs-lookup"><span data-stu-id="7a809-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a><span data-ttu-id="7a809-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a809-111">Example</span></span>  
 <span data-ttu-id="7a809-112">Následující příklad vrátí objednávky, kde je množství objednávky větší než 2 a menší než 6.</span><span class="sxs-lookup"><span data-stu-id="7a809-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a><span data-ttu-id="7a809-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a809-113">Example</span></span>  
 <span data-ttu-id="7a809-114">Následující příklad vrátí všechny červené barevné produkty.</span><span class="sxs-lookup"><span data-stu-id="7a809-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a><span data-ttu-id="7a809-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a809-115">Example</span></span>  
 <span data-ttu-id="7a809-116">Následující příklad používá `Where` metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2003 a poté `order.SalesOrderDetail` pomocí vlastnosti navigace Získá podrobnosti pro každou objednávku.</span><span class="sxs-lookup"><span data-stu-id="7a809-116">The following example uses the `Where` method to find orders that were made after December 1, 2003 and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a><span data-ttu-id="7a809-117">Kde... Zobrazí</span><span class="sxs-lookup"><span data-stu-id="7a809-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="7a809-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a809-118">Example</span></span>  
 <span data-ttu-id="7a809-119">Následující příklad používá pole jako součást `Where…Contains` klauzule pro vyhledání všech produktů, které `ProductModelID` mají, které odpovídají hodnotě v poli.</span><span class="sxs-lookup"><span data-stu-id="7a809-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
> <span data-ttu-id="7a809-120">Jako `Where…Contains` součást predikátu v klauzuli můžete <xref:System.Array>použít, <xref:System.Collections.Generic.List%601>nebo, nebo kolekci libovolného typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a809-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="7a809-121">Můžete také deklarovat a inicializovat kolekci v rámci LINQ to Entitiesho dotazu.</span><span class="sxs-lookup"><span data-stu-id="7a809-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="7a809-122">Další informace najdete v dalším příkladu.</span><span class="sxs-lookup"><span data-stu-id="7a809-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7a809-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a809-123">Example</span></span>  
 <span data-ttu-id="7a809-124">Následující příklad deklaruje a inicializuje pole v `Where…Contains` klauzuli pro vyhledání všech produktů, které `ProductModelID` mají nebo `Size` , které odpovídají hodnotě v polích.</span><span class="sxs-lookup"><span data-stu-id="7a809-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or a `Size` that matches a value in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7a809-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a809-125">See also</span></span>

- [<span data-ttu-id="7a809-126">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7a809-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
