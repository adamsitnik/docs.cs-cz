---
title: 'Příklady syntaxe dotazů založených na volání metody: Množinové operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 48aa6044f39be93f144b6c4af5137b131dda0b30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085815"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="e4fe7-102">Příklady syntaxe dotazů založených na volání metody: Množinové operátory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e4fe7-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="e4fe7-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, a <xref:System.Linq.Enumerable.Union%2A> operátory k provádění operací porovnání založené na hodnotách sad řádky dat.[ Načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) naleznete v tématu [porovnání DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) Další informace o <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="e4fe7-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) See [Comparing DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="e4fe7-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="e4fe7-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="e4fe7-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e4fe7-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e4fe7-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e4fe7-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="e4fe7-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e4fe7-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="e4fe7-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="e4fe7-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4fe7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4fe7-109">Example</span></span>  
 <span data-ttu-id="e4fe7-110">V tomto příkladu <xref:System.Linq.Enumerable.Distinct%2A> metoda odebrání duplicitních prvků v posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="e4fe7-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="e4fe7-111">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="e4fe7-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4fe7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4fe7-112">Example</span></span>  
 <span data-ttu-id="e4fe7-113">V tomto příkladu <xref:System.Linq.Enumerable.Except%2A> metoda vrátí kontakty, které se zobrazují v první tabulce, ale nikoli do druhého.</span><span class="sxs-lookup"><span data-stu-id="e4fe7-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="e4fe7-114">Intersect</span><span class="sxs-lookup"><span data-stu-id="e4fe7-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4fe7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4fe7-115">Example</span></span>  
 <span data-ttu-id="e4fe7-116">V tomto příkladu <xref:System.Linq.Enumerable.Intersect%2A> metoda vrátí kontakty, které se zobrazují v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="e4fe7-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="e4fe7-117">Unie</span><span class="sxs-lookup"><span data-stu-id="e4fe7-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4fe7-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4fe7-118">Example</span></span>  
 <span data-ttu-id="e4fe7-119">V tomto příkladu <xref:System.Linq.Enumerable.Union%2A> metoda vrátí jedinečný kontakty pomocí kteréhokoli z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="e4fe7-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="e4fe7-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4fe7-120">See also</span></span>

- [<span data-ttu-id="e4fe7-121">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="e4fe7-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="e4fe7-122">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e4fe7-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="e4fe7-123">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="e4fe7-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e4fe7-124">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4fe7-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
