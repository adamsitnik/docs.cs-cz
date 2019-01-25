---
title: Načítání dat do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 0f50638beb50220d06daef7bbd6002b319a92476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622959"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="9fa10-102">Načítání dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="9fa10-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="9fa10-103">A <xref:System.Data.DataSet> musí předtím, než můžete dát dotaz na něj s prvním naplnění objektu [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa10-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="9fa10-104">Existuje několik různých způsobů, jak naplnit <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9fa10-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9fa10-105">Například můžete použít [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] k dotazování databáze a načte výsledky do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9fa10-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9fa10-106">Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="9fa10-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="9fa10-107">Dalším běžným způsobem načtení dat do <xref:System.Data.DataSet> , je použít <xref:System.Data.Common.DataAdapter> třídy k načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="9fa10-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="9fa10-108">To je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fa10-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fa10-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fa10-109">Example</span></span>  
 <span data-ttu-id="9fa10-110">Tento příklad používá <xref:System.Data.Common.DataAdapter> k dotazování databáze AdventureWorks prodejní informace v roce 2002 a načte výsledky do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9fa10-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9fa10-111">Po <xref:System.Data.DataSet> naplněné, můžete psát dotazy proti ho pomocí [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa10-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="9fa10-112">`FillDataSet` Metoda v tomto příkladu se používá v příkladů dotazů v [příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="9fa10-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="9fa10-113">Další informace najdete v tématu [dotazování datových sad](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9fa10-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="9fa10-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fa10-114">See also</span></span>
- [<span data-ttu-id="9fa10-115">Přehled LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9fa10-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="9fa10-116">Dotazy na datové sady</span><span class="sxs-lookup"><span data-stu-id="9fa10-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="9fa10-117">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9fa10-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
