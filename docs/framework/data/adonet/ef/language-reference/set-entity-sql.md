---
title: NASTAVIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 76999bcbbb3b63fd945d2048734c58d97de8baea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249242"
---
# <a name="set-entity-sql"></a><span data-ttu-id="8cbda-102">NASTAVIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8cbda-102">SET (Entity SQL)</span></span>
<span data-ttu-id="8cbda-103">Výraz MNOŽINy se používá k převodu kolekce objektů na sadu pomocí získání nové kolekce s odebranými duplicitními prvky.</span><span class="sxs-lookup"><span data-stu-id="8cbda-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cbda-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8cbda-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8cbda-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8cbda-106">Libovolný platný výraz dotazu, který vrací kolekci.</span><span class="sxs-lookup"><span data-stu-id="8cbda-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cbda-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8cbda-107">Remarks</span></span>  
 <span data-ttu-id="8cbda-108">Výraz `SET(c)` množiny je logicky ekvivalentní následujícímu příkazu SELECT:</span><span class="sxs-lookup"><span data-stu-id="8cbda-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="8cbda-109">`SET`je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množin operátorů.</span><span class="sxs-lookup"><span data-stu-id="8cbda-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="8cbda-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="8cbda-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="8cbda-111">Viz [s výjimkou](except-entity-sql.md) pro informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prioritách pro množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="8cbda-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cbda-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8cbda-112">Example</span></span>  
 <span data-ttu-id="8cbda-113">Následující Entity SQL dotaz používá výraz SET pro převod kolekce objektů do sady.</span><span class="sxs-lookup"><span data-stu-id="8cbda-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="8cbda-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8cbda-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8cbda-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="8cbda-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8cbda-116">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="8cbda-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="8cbda-117">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="8cbda-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="8cbda-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cbda-118">See also</span></span>

- [<span data-ttu-id="8cbda-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8cbda-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
