---
title: Stránkování (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: f6ff95c387224705e58edb0b80bf908f39391a80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672926"
---
# <a name="paging-entity-sql"></a>Stránkování (Entity SQL)
Fyzické stránkování lze provést pomocí [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí ustanovení [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli. Provádět nedeterministicky fyzické stránkování, měli byste použít přeskočit a omezení. Pokud chcete omezit počet řádků ve výsledku tak Nedeterministický, měli byste použít [horní](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). TOP a SKIP/LIMIT se vzájemně vylučují.  
  
## <a name="top-overview"></a>HORNÍ – přehled  
 Klauzule SELECT může mít volitelné dílčí klauzule TOP následující volitelný modifikátor ALL/DISTINCT. Dílčí klauzule TOP Určuje, že bude vrácen pouze první sada řádků z výsledku dotazu. Další informace najdete v tématu [horní](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Přehled omezení a přeskočit  
 Přeskočit a omezení jsou součástí klauzule ORDER by. Pokud výraz dílčí klauzuli SKIP je přítomna v klauzuli ORDER BY, výsledky budou seřazeny podle specifikace řazení a sada výsledků zahrne řádky, počínaje další řádek hned po výrazu SKIP. Například přeskočit 5 přeskočte prvních pět řádků, který se vrátí z řádku šestého vpřed. Pokud dílčí klauzuli LIMIT výrazu je přítomna v klauzuli ORDER BY, dotazu budou seřazeny podle specifikace řazení a výsledný počet řádků se omezí výrazu omezení. LIMIT 5, omezí sadu výsledků do pěti instance nebo řádků. Přeskočit a omezení nemají být použity současně; můžete použít jenom přeskočit nebo jenom omezení s klauzulí ORDER BY. Další informace naleznete v následujících tématech:  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Postupy: Stránkovat výsledky dotazu](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
