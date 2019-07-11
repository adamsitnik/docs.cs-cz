---
title: SQL Server Compact a LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 5fa8f8ba2b0c5bdb92ad507bd48839a26837ba41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742862"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact a LINQ to SQL
SQL Server Compact je výchozí databáze nainstalován se sadou Visual Studio. Další informace najdete v tématu [pomocí SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 Toto téma popisuje hlavní rozdíly ve využití, konfiguraci, sady funkcí a rozsah [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporovat.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Vlastnosti systému SQL Server Compact ve vztahu k LINQ to SQL  
 Ve výchozím nastavení, SQL Server Compact se nainstaluje pro všechny edice sady Visual Studio a proto je k dispozici na na vývojovém počítači pro použití s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Nasazení aplikace, která používá SQL Server Compact, ale a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se liší od pro aplikaci systému SQL Server. SQL Server Compact není součástí rozhraní .NET Framework a proto musí být zabalené aplikace nebo stáhnout samostatně z webu společnosti Microsoft.  
  
 Mějte na paměti následující vlastnosti:  
  
- SQL Server Compact je zabalený jako knihovnu DLL, která se dá použít pro soubory databáze (s příponou .sdf) přímo.  
  
- SQL Server Compact běží ve stejném procesu jako klientská aplikace. Efektivitu komunikaci s SQL serverem Compact, proto může být výrazně vyšší než komunikaci se serverem SQL Server. Na druhé straně SQL Server Compact vyžaduje vzájemná funkční spolupráce mezi spravovaným a nespravovaným kódem s jeho odebrání dodatečné náklady.  
  
- Velikost SQL Server Compact knihovny DLL je malá. Tato funkce snižuje velikost celkového aplikace.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Modulu runtime a nástroje příkazového řádku SQLMetal podporu systému SQL Server Compact.  
  
- Návrhář relací objektů nepodporuje SQL Server Compact.  
  
## <a name="feature-set"></a>Sada funkcí  
 SQL Server Compact sada funkcí je mnohem jednodušší než sadě funkcí systému SQL Server následujícími způsoby, které můžou ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace:  
  
- SQL Server Compact nepodporuje uložené procedury nebo zobrazení.  
  
- SQL Server Compact podporuje jenom určité podmnožiny datových typů a funkcí SQL.  
  
- SQL Server Compact podporuje pouze podmnožinu SQL konstruktorů.  
  
- SQL Server Compact obsahuje pouze minimální optimalizace. Je možné, že několik dotazů může být vypršení časového limitu.  
  
- SQL Server Compact nepodporuje částečným vztahem důvěryhodnosti.  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
