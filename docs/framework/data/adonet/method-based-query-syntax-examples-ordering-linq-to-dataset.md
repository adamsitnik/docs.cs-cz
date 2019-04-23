---
title: 'Příklady syntaxe dotazů založených na volání metody: Řazení (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 76bc4751a25e82a731e136f838d12b8d1c1d691f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119558"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="91f19-102">Příklady syntaxe dotazů založených na volání metody: Řazení (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="91f19-102">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="91f19-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, a <xref:System.Linq.Enumerable.ThenBy%2A> metody pro dotazování <xref:System.Data.DataSet> a řazení výsledků pomocí syntaxe metody dotazu.</span><span class="sxs-lookup"><span data-stu-id="91f19-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="91f19-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="91f19-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="91f19-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="91f19-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="91f19-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="91f19-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="91f19-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="91f19-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="91f19-108">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="91f19-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="91f19-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="91f19-109">Example</span></span>  
 <span data-ttu-id="91f19-110">V tomto příkladu <xref:System.Linq.Enumerable.OrderBy%2A> metodu s vlastní porovnávací metody provedete velkých a malých písmen druh příjmení.</span><span class="sxs-lookup"><span data-stu-id="91f19-110">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="91f19-111">reverzní</span><span class="sxs-lookup"><span data-stu-id="91f19-111">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="91f19-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="91f19-112">Example</span></span>  
 <span data-ttu-id="91f19-113">V tomto příkladu <xref:System.Linq.Enumerable.Reverse%2A> metodu pro vytvoření seznamu objednávek where `OrderDate` je starší než 20. února 2002.</span><span class="sxs-lookup"><span data-stu-id="91f19-113">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="91f19-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="91f19-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="91f19-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="91f19-115">Example</span></span>  
 <span data-ttu-id="91f19-116">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> a <xref:System.Linq.Enumerable.ThenBy%2A> metody s vlastní porovnávací metody první řadit podle ceníku a pak proveďte velkých a malých písmen sestupné řazení produktů.</span><span class="sxs-lookup"><span data-stu-id="91f19-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="91f19-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91f19-117">See also</span></span>

- [<span data-ttu-id="91f19-118">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="91f19-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="91f19-119">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="91f19-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="91f19-120">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="91f19-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="91f19-121">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91f19-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
