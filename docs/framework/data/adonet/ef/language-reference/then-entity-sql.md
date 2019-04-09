---
title: POTOM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: d5f9f2b8c9d7397cbcd91fa52a95544fc66e4dce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184587"
---
# <a name="then-entity-sql"></a><span data-ttu-id="85c57-102">POTOM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="85c57-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="85c57-103">Výsledek klauzuli WHEN, když je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="85c57-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85c57-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="85c57-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="85c57-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="85c57-106">Libovolný platný výraz Boolean.</span><span class="sxs-lookup"><span data-stu-id="85c57-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="85c57-107">Libovolný výraz platný dotaz, který vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="85c57-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85c57-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85c57-108">Remarks</span></span>  
 <span data-ttu-id="85c57-109">Pokud `when_expression` vyhodnocen na hodnotu `true`, výsledkem je odpovídající `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="85c57-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="85c57-110">Pokud není k dispozici z WHEN podmínky splněny, `else-expression` je vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="85c57-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="85c57-111">Ale pokud neexistuje žádný `else-expression`, výsledek je null.</span><span class="sxs-lookup"><span data-stu-id="85c57-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="85c57-112">Příklad najdete v tématu [případ](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="85c57-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85c57-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="85c57-113">Example</span></span>  
 <span data-ttu-id="85c57-114">Následující dotaz Entity SQL používá k vyhodnocení sady výraz CASE `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="85c57-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="85c57-115">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="85c57-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="85c57-116">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="85c57-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="85c57-117">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="85c57-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="85c57-118">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="85c57-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="85c57-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85c57-119">See also</span></span>

- [<span data-ttu-id="85c57-120">CASE</span><span class="sxs-lookup"><span data-stu-id="85c57-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [<span data-ttu-id="85c57-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="85c57-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
