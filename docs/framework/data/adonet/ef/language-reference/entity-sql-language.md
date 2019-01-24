---
title: Jazyk Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 0c698f04c3b95ffb204a20d41e91ef3f6210c5d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494093"
---
# <a name="entity-sql-language"></a>Jazyk Entity SQL
Entita SQL je nezávislý na úložišti dotazovací jazyk podobný SQL. Entita SQL vám umožní provádět dotazy na entity data, jako objekty nebo ve formě tabulky. Měli byste zvážit použití Entity SQL v následujících případech:  
  
-   Pokud dotaz musí dynamicky zkonstruovat za běhu. V takovém případě byste měli také zvážit použití metody Tvůrce dotazů <xref:System.Data.Objects.ObjectQuery%601> místo vytváření Entity SQL řetězec za běhu dotazu.  
  
-   Pokud chcete definovat dotaz jako součást definice modelu. V datovém modelu se podporuje jenom Entity SQL. Další informace najdete v tématu [Element QueryView (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
-   Při použití zprostředkovatel EntityClient pro vrácení dat jen pro čtení entity jako s použitím sady řádků <xref:System.Data.EntityClient.EntityDataReader>. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   Pokud jste už jste odborník v jazycích dotazů založených na SQL, se může zdát vám nejvíc fyzické Entity SQL.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Použití se zprostředkovatelem EntityClient Entity SQL  
 Pokud chcete používat Entity SQL se zprostředkovatelem EntityClient, naleznete v následujících tématech pro další informace:  
  
 [Zprostředkovatel EntityClient pro Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Postupy: Vytvoření připojovacího řetězce EntityConnection](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu RefType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Postupy: Provedení dotazu, který vrátí komplexní typy](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Postupy: Provedení dotazu, který vrátí vnořené kolekce](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Postupy: Provést parametrizovaného dotazu Entity SQL pomocí EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Postupy: Spuštění Polymorfního dotazu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Postupy: Procházení vztahů pomocí navigačního operátoru](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Pomocí dotazy objektu Entity SQL  
 Pokud chcete používat Entity SQL pomocí objektu dotazů, naleznete v následujících tématech pro další informace:  
  
 [Postupy: Provedení dotazu, který vrací objekty typu Entity](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Postupy: Spuštění parametrizovaného dotazu](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Postupy: Procházení vztahů pomocí navigačních vlastností](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Postupy: Volání uživatelem definované funkce](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Postupy: Filtrování dat](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Postupy: Řazení dat](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Postupy: Skupiny dat](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Postupy: Aggregate Data](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Postupy: Provedení dotazu, který vrací objekty anonymního typu](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Postupy: Provedení dotazu, který vrátí kolekce primitivních typů](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Postupy: Dotaz v objekt EntityCollection související objekty](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Postupy: Pořadí sjednocení dva dotazy](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [Postupy: Stránkovat výsledky dotazu](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Viz také:
- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
- [Referenční dokumentace jazyka](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
