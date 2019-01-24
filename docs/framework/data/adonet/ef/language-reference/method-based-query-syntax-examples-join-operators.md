---
title: 'Příklady syntaxe dotazů založených na volání metody: Join Operators'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 24d5b36e37802fee1452433b49fb6f4c4fbced14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595900"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="4bf65-102">Příklady syntaxe dotazů založených na volání metody: Join Operators</span><span class="sxs-lookup"><span data-stu-id="4bf65-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="4bf65-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A> metody k dotazování [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="4bf65-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="4bf65-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4bf65-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4bf65-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="4bf65-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="4bf65-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="4bf65-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="4bf65-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf65-107">Example</span></span>  
 <span data-ttu-id="4bf65-108">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky a vyhledá počet objednávek pro zákazníka.</span><span class="sxs-lookup"><span data-stu-id="4bf65-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="4bf65-109">Spojení skupiny je ekvivalentem levé vnější spojení, která vrátí všechny prvky objektu prvního zdroje dat (levý) i v případě, že žádné korelační prvky jsou ve zdroji dat jiné.</span><span class="sxs-lookup"><span data-stu-id="4bf65-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="4bf65-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf65-110">Example</span></span>  
 <span data-ttu-id="4bf65-111">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes kontaktní údaje a SalesOrderHeader tabulky a vyhledá počet objednávek za kontakt.</span><span class="sxs-lookup"><span data-stu-id="4bf65-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="4bf65-112">Zobrazí se počet objednávek a ID každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="4bf65-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="4bf65-113">Join</span><span class="sxs-lookup"><span data-stu-id="4bf65-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="4bf65-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf65-114">Example</span></span>  
 <span data-ttu-id="4bf65-115">Následující příklad provádí spojení kontaktní údaje a SalesOrderHeader tabulky.</span><span class="sxs-lookup"><span data-stu-id="4bf65-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="4bf65-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf65-116">Example</span></span>  
 <span data-ttu-id="4bf65-117">Následující příklad provádí spojení kontaktu a obraťte se na tabulky SalesOrderHeader, seskupení výsledků podle ID.</span><span class="sxs-lookup"><span data-stu-id="4bf65-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4bf65-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bf65-118">See also</span></span>
- [<span data-ttu-id="4bf65-119">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4bf65-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
