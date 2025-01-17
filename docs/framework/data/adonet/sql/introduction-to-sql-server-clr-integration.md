---
title: Úvod k integraci modulu CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 76c6fb4cb37807f286f1f1f2aeedbdea6c74fe38
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002141"
---
# <a name="introduction-to-sql-server-clr-integration"></a>Úvod k integraci modulu CLR na SQL Serveru
Modul CLR (Common Language Runtime) je srdcem společnosti Microsoft .NET Framework a poskytuje spouštěcí prostředí pro veškerý kód .NET Framework. Kód, který běží v rámci CLR, je označován jako spravovaný kód. CLR poskytuje různé funkce a služby, které jsou nezbytné pro spuštění programu, včetně kompilace JIT (just-in-time), přidělování a správě paměti, vynucování bezpečnosti typů, zpracování výjimek, správy vláken a zabezpečení.  
  
 S modulem CLR hostovaným v Microsoft SQL Server (nazývaným integrace CLR) můžete vytvářet uložené procedury, triggery, uživatelsky definované funkce, uživatelsky definované typy a uživatelsky definované agregace ve spravovaném kódu. Vzhledem k tomu, že spravovaný kód se zkompiluje do nativního kódu před provedením, můžete v některých scénářích dosáhnout výrazného zvýšení výkonu.  
  
 Spravovaný kód používá zabezpečení přístupu kódu (CAS), odkazy na kód a domény aplikace, aby se zabránilo sestavením v provádění určitých operací. SQL Server používá CAS ke zvýšení zabezpečení spravovaného kódu a zabránění ohrožení zabezpečení operačního systému nebo databázového serveru.  
  
 Tato část je určena pouze k tomu, aby poskytovala dostatek informací, aby bylo možné začít programovat s SQL Server integrací CLR a není určeno pro komplexní. Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **SQL Server Knihy online**  
  
- [Přehled integrace modulu CLR (Common Language Runtime)](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Povolení integrace modulu CLR  
 Funkce integrace modulu CLR (Common Language Runtime) je ve výchozím nastavení vypnuta v Microsoft SQL Server a musí být povolena, aby bylo možné použít objekty, které jsou implementovány pomocí integrace modulu CLR. Chcete-li povolit integraci modulu CLR pomocí jazyka Transact-SQL, použijte možnost `clr enabled` uložené procedury `sp_configure`, jak je znázorněno níže:  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Integraci modulu CLR můžete zakázat nastavením možnosti `clr enabled` na hodnotu 0. Zakážete-li integraci modulu CLR, SQL Server zastaví provádění všech rutin CLR a uvolní všechny domény aplikace.  
  
 Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **SQL Server Knihy online**  
  
- [Povolení integrace modulu CLR](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Nasazení sestavení CLR  
 Až budou metody CLR testovány a ověřeny na testovacím serveru, mohou být distribuovány na provozní servery pomocí skriptu nasazení. Skript nasazení lze vytvořit ručně nebo pomocí SQL Server Management Studio. Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **SQL Server Knihy online**  
  
1. [Nasazení objektů databáze CLR](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Zabezpečení integrace CLR  
 Model zabezpečení Microsoft SQL Server integrace s modulem CLR (Common Language Runtime) společnosti Microsoft .NET Framework spravuje a zabezpečuje přístup mezi různými typy objektů CLR a objekty mimo CLR spuštěnými v SQL Server. Tyto objekty mohou být volány příkazem jazyka Transact-SQL nebo jiným objektem CLR běžícím na serveru.  
  
 Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **SQL Server Knihy online**  
  
- [Zabezpečení integrace CLR](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Ladění sestavení CLR  
 Microsoft SQL Server poskytuje podporu pro ladění objektů Transact-SQL a modulu CLR (Common Language Runtime) v databázi. Ladění funguje napříč jazyky: uživatelé můžou bezproblémově krokovat objekty CLR z jazyka Transact-SQL a naopak.  
  
 Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **SQL Server Knihy online**  
  
- [Ladění objektů databáze CLR](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu ke kódu a ADO.NET](../code-access-security.md)
- [Přehled ADO.NET](../ado-net-overview.md)
