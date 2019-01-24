---
title: Načítání a úpravy dat v ADO.NET
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: ab6aa30708140aed2f5f325c3dae9f543937fac8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556428"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Načítání a úpravy dat v ADO.NET
Primární funkce libovolné aplikace, databáze je připojení ke zdroji dat a načítání dat, který ji obsahuje. Zprostředkovatelé dat .NET Framework ADO.NET slouží jako most mezi aplikací a zdroji dat, umožňuje spouštět i příkazy jde o načtení dat pomocí **DataReader** nebo **DataAdapter** . Klíčové funkce libovolné aplikace, databáze je možnost aktualizovat data, která je uložena v databázi. V ADO.NET, aktualizace dat je použít **DataAdapter** a <xref:System.Data.DataSet>, a **příkaz** objekty; a to může zahrnovat také použití transakcí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Popisuje, jak vytvořit připojení ke zdroji dat a jak pracovat s události připojení.  
  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 Obsahuje témata popisující různé aspekty pomocí připojovacích řetězců, včetně klíčových slov řetězec připojení, bezpečnostní údaje a ukládání a načítání je.  
  
 [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)  
 Popisuje zprostředkovatele dat .NET Framework sdružování připojení.  
  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Obsahuje témata popisující, jak vytvořit příkazy a příkaz počítačů, nakonfigurujte parametry a tom, jak spustit příkazy, které načítají a upravují data.  
  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Obsahuje témata popisující čtečky dat, parametry a adaptérů dat, zpracování událostí adaptéru dat a provádění dávkových operací.  
  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Obsahuje témata popisující, jak provádět místní transakce, distribuované transakce a pracovat s optimistického řízení souběžnosti.  
  
 [Načítání hodnot identity nebo automatického číslování](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 Poskytuje příklad mapování hodnoty pro generované **identity** sloupec v tabulce SQL serveru nebo pro **automatické** pole aplikace Microsoft Access tabulky ke sloupci vloženého řádku v tabulce. Tento článek popisuje sloučení hodnoty identity v `DataTable`.  
  
 [Načítání binárních dat](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 Popisuje, jak načíst binární data nebo velkých datových struktur pomocí `CommandBehavior`.`SequentialAccess` Chcete-li změnit výchozí chování `DataReader`.  
  
 [Úpravy dat pomocí uložených procedur](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Popisuje způsob používání vstupních parametrů uložené procedury a výstupní parametry pro vložení řádku v databázi, vrací novou hodnotu identity.  
  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 Popisuje, jak získat dostupné databáze nebo katalogů, tabulky a zobrazení v databázi, omezení, která pro tabulky a další informace o schématu ze zdroje dat existují.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Popisuje model objekt pro vytváření zprostředkovatele a ukazuje, jak použít základní třídy v `System.Data.Common` oboru názvů.  
  
 [Trasování data v ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md)  
 Popisuje, jak technologie ADO.NET poskytuje předdefinované datové funkce trasování.  
  
 [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)  
 Popisuje čítačů výkonu k dispozici pro `SqlClient` a `OracleClient`.  
  
 [Asynchronní programování](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 Popisuje [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] podporu pro asynchronní programování.  
  
 [Podpora streamování SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 Popisuje, jak psát aplikace datového proudu dat z SQL serveru bez nutnosti ho plně načten v paměti.  
  
## <a name="see-also"></a>Viz také:
- [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
