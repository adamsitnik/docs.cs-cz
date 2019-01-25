---
title: Binární a vysoké hodnoty dat serveru SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: f6bd62d2e9d2f87947e01b7964c5d151690b62bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643026"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binární a vysoké hodnoty dat serveru SQL Server
SQL Server poskytuje `max` specifikátor, který rozbalí úložnou kapacitu `varchar`, `nvarchar`, a `varbinary` datové typy. `varchar(max)`, `nvarchar(max)`, a `varbinary(max)` se společně nazývají *velké hodnoty datových typů*. Velké hodnoty datové typy, které můžete použít k uložení až 2 ^ 31-1 bajtů.  
  
 SQL Server 2008 představuje atribut FILESTREAM, což není typ dat, ale místo toho atribut, který může být definovaný na sloupci, dat. velké hodnoty uložené v systému souborů namísto v databázi.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úprava vysokých (maximálních) hodnot v ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Popisuje způsob práce s typy dat vysoké hodnoty.  
  
 [Data FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 Popisuje, jak pracovat s daty velké hodnoty uložené v systému SQL Server 2008 s atributem FILESTREAM.  
  
## <a name="see-also"></a>Viz také:
- [Datové typy SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Operace dat na SQL Serveru v ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [Načítání a úpravy dat v ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
