---
title: Zabezpečení integrace CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 946401211d515df9ba5b9e38d7cfd10730973b64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165812"
---
# <a name="clr-integration-security-in-sql-server"></a>Zabezpečení integrace CLR na SQL Serveru
Microsoft SQL Server poskytuje integraci běžné součásti modulu runtime (CLR) jazyk rozhraní .NET Framework. Integrace modulu CLR umožňuje psát uložené procedury, aktivační události, uživatelem definovaných typů, uživatelem definované funkce, uživatelem definovaných agregacích a datových proudů funkce vracející tabulku, pomocí libovolného jazyka, rozhraní .NET Framework, jako je například Microsoft Visual Basic .NET nebo Microsoft Visual C#.  
  
 Modul CLR podporuje model zabezpečení pro spravovaný kód volá zabezpečení přístupu kódu (CAS). V tomto modelu jsou udělena oprávnění pro sestavení založená na důkaz, kód v metadatech. SQL Server integruje model zabezpečení založený na uživatele systému SQL Server s použitím modelu zabezpečení přístupu kódu modulu CLR.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o integraci modulu CLR SQL serveru najdete v následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečení přístupu kódu](../../../../../docs/framework/misc/code-access-security.md)|Obsahuje témata popisující certifikační Autority v rozhraní .NET Framework.|  
|[Zabezpečení integrace CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|Tento článek popisuje model zabezpečení pro spravovaný kód spuštění v rámci služby SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Integrace CLR (Common Language Runtime) na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)
- [Přehled ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)
