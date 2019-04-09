---
title: Integrace CLR (Common Language Runtime) na SQL Serveru
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d87f2b89583747b80ef103f419bd9bd2e3b1e0da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089832"
---
# <a name="sql-server-common-language-runtime-integration"></a>Integrace CLR (Common Language Runtime) na SQL Serveru
SQL Server 2005 zavedené integraci běžné součásti modulu runtime (CLR) jazyk rozhraní .NET Framework pro Microsoft Windows. To znamená, že můžete napsat uložené procedury, aktivační události, uživatelem definovaných typů, uživatelem definované funkce, uživatelem definovaných agregacích a datových proudů funkce vracející tabulku pomocí libovolného jazyka, rozhraní .NET Framework, včetně Microsoft Visual Basic .NET a Microsoft Visual C#. <xref:Microsoft.SqlServer.Server> Obor názvů obsahuje sadu nových aplikačních programovacích rozhraní (API) tak, aby spravovaný kód může spolupracovat s prostředím Microsoft SQL Server.  
  
 Tato část popisuje funkce a chování, které jsou specifické pro integrace systému SQL Server common language runtime (CLR) a konkrétní rozšíření v procesu serveru SQL Server pro technologii ADO.NET.  
  
 Tato část poskytuje pouze dostatek informací, jak začít programovat díky integraci modulu CLR SQL serveru a není určena být vyčerpávající. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
1.  [Běžné koncepty programování integrace Language Runtime (CLR)](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úvod k integraci modulu CLR na SQL Serveru](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 Poskytuje úvod do integrace modulu CLR SQL serveru. Obsahuje odkazy na další témata.  
  
 [Uživatelem definované funkce CLR](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 Popisuje, jak implementovat a použít různé typy funkce CLR: agregační funkce vracející tabulku, skalární a definovaný uživatelem.  
  
 [Uživatelem definované typy CLR](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 Popisuje, jak implementovat a použít uživatelem definované typy CLR. Obsahuje odkazy na další témata.  
  
 [Uložené procedury CLR](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 Popisuje, jak implementovat a používat CLR uložené procedury. Obsahuje odkazy na další témata.  
  
 [Aktivační procedury CLR](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 Popisuje, jak implementovat a použít aktivační procedury modulu CLR. Obsahuje odkazy na další témata.  
  
 [Kontextové připojení](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 Popisuje připojení kontextu.  
  
 [Chování ADO.NET specifické pro proces SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 Popisuje rozšíření konkrétní v procesu systému SQL Server, ADO.NET a připojení kontextu. Obsahuje odkazy na další témata.  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
