---
title: + (Přidat)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 1c525a1cd56d1d8b7ed0dad3a7cec686cb6b1ab3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580652"
---
# <a name="-add"></a>+ (Add)
Sečte dvě čísla.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz některou z číselných datových typů.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů. Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="remarks"></a>Poznámky  
 Pro EDM. Typy řetězce, sčítání je zřetězení.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá + aritmetického operátoru pro přidání dvou čísel. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Typy konceptuálních modelů (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
