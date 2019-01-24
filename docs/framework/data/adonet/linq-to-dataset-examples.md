---
title: Příklady LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: 8e6cce8ba79cad42ade6ac373631094f9e2d4e04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634529"
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="cb1e1-102">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="cb1e1-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="cb1e1-103">Tato část obsahuje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programování příklady použití standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples that use the standard query operators.</span></span> <span data-ttu-id="cb1e1-104"><xref:System.Data.DataSet> Používá v těchto příkladech je vyplněna pomocí `FillDataSet` metodu, která je zadána v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="cb1e1-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="cb1e1-105">Další informace najdete v tématu [přehled standardních operátorů dotazu](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="cb1e1-105">For more information, see [Standard Query Operators Overview](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb1e1-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cb1e1-106">In This Section</span></span>  
 [<span data-ttu-id="cb1e1-107">Příklady výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="cb1e1-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="cb1e1-108">Obsahuje následující příklady:</span><span class="sxs-lookup"><span data-stu-id="cb1e1-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="cb1e1-109">Projekce</span><span class="sxs-lookup"><span data-stu-id="cb1e1-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="cb1e1-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="cb1e1-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="cb1e1-111">Segmentace</span><span class="sxs-lookup"><span data-stu-id="cb1e1-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="cb1e1-112">Řazení</span><span class="sxs-lookup"><span data-stu-id="cb1e1-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="cb1e1-113">Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="cb1e1-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="cb1e1-114">Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="cb1e1-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="cb1e1-115">Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="cb1e1-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="cb1e1-116">Příklady dotazů založených na metodách</span><span class="sxs-lookup"><span data-stu-id="cb1e1-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="cb1e1-117">Obsahuje následující příklady:</span><span class="sxs-lookup"><span data-stu-id="cb1e1-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="cb1e1-118">Projekce</span><span class="sxs-lookup"><span data-stu-id="cb1e1-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="cb1e1-119">Segmentace</span><span class="sxs-lookup"><span data-stu-id="cb1e1-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="cb1e1-120">Řazení</span><span class="sxs-lookup"><span data-stu-id="cb1e1-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="cb1e1-121">Množinové operátory</span><span class="sxs-lookup"><span data-stu-id="cb1e1-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="cb1e1-122">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="cb1e1-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="cb1e1-123">Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="cb1e1-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="cb1e1-124">Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="cb1e1-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="cb1e1-125">Spojení</span><span class="sxs-lookup"><span data-stu-id="cb1e1-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="cb1e1-126">Příklady operátorů specifických pro datovou sadu</span><span class="sxs-lookup"><span data-stu-id="cb1e1-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="cb1e1-127">Obsahuje příklady, které ukazují, jak používat <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda a <xref:System.Data.DataRowComparer> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb1e1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb1e1-128">See also</span></span>
- [<span data-ttu-id="cb1e1-129">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="cb1e1-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [<span data-ttu-id="cb1e1-130">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="cb1e1-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
