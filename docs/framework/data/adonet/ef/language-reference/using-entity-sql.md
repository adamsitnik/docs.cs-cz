---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319209"
---
# <a name="using-entity-sql"></a>USING (Entity SQL)
Určuje obory názvů použité ve výrazu dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Určuje kratší alias pro získání oboru názvů pomocí.  
  
 `namespace`  
 Libovolný platný obor názvů.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru USING určí obory názvů použité ve výrazu dotazu. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Viz také:

- [Obory názvů](namespaces-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
