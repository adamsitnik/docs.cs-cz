---
title: Souběžné spouštění v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 0ada258f74338fc7cbc9435fdea8fc896bd2efd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782707"
---
# <a name="side-by-side-execution-in-adonet"></a>Souběžné spouštění v ADO.NET
Souběžné spouštění v .NET Framework je schopnost spustit aplikaci na počítači, ve kterém je nainstalováno více verzí .NET Framework, výhradně pomocí verze, pro kterou byla aplikace zkompilována. Podrobné informace o konfiguraci souběžného spouštění najdete v tématu [Souběžné spouštění](../../deployment/side-by-side-execution.md).  
  
 Aplikace kompilovaná pomocí jedné verze .NET Framework může běžet v jiné verzi .NET Framework. Nicméně doporučujeme, abyste nakompilováni verzi aplikace pro každou nainstalovanou verzi .NET Framework a spouštěli je samostatně. V obou případech byste si měli být vědomi změn v ADO.NET mezi verzemi, které mohou ovlivnit dopředné a zpětné kompatibility vaší aplikace.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Dopředná kompatibilita a zpětná kompatibilita  
 Dopředná kompatibilita znamená, že aplikace může být zkompilována ve starší verzi .NET Framework, ale bude stále fungovat v novější verzi .NET Framework. ADO.NET kód napsaný pro .NET Framework verze 1,1 je dopředně kompatibilní s novějšími verzemi.  
  
 Zpětná kompatibilita znamená, že aplikace je kompilována pro novější verzi .NET Framework, ale nadále běží v dřívějších verzích .NET Framework bez jakékoliv ztráty funkčnosti. Samozřejmě to pro funkce, které jsou představené v nové verzi .NET Framework, to nebude mít žádný případ.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>Zprostředkovatel dat .NET Framework pro rozhraní ODBC  
 Počínaje verzí 1,1 je zprostředkovatel dat .NET Framework pro rozhraní ODBC (<xref:System.Data.Odbc>) součástí .NET Framework. Poskytovatel dat ODBC je k dispozici .NET Framework vývojářům verze 1,0 jako web ke stažení z [centra pro vývojáře pro přístup k datům a úložiště](https://go.microsoft.com/fwlink/?linkid=4173). Obor názvů pro stažený .NET Framework Zprostředkovatel dat pro ODBC je **Microsoft. data. ODBC**.  
  
 Pokud máte vyvinutou aplikaci pro .NET Framework verze 1,0, která používá poskytovatele dat ODBC pro připojení ke zdroji dat a chcete tuto aplikaci spustit v .NET Framework verze 1,1 nebo novější, je nutné aktualizovat obor názvů pro rozhraní ODBC dat poskytovatel k **System. data. ODBC**. Pak je nutné ji znovu zkompilovat pro novější verzi .NET Framework.  
  
 Pokud máte vyvinutou aplikaci pro .NET Framework verze 2,0 nebo novější, která používá poskytovatele dat ODBC pro připojení ke zdroji dat a chcete tuto aplikaci spustit v .NET Framework verze 1,0, je nutné stáhnout poskytovatele dat ODBC a nainstalovat ho. v systému .NET Framework verze 1,0. Pak musíte změnit obor názvů pro poskytovatele dat ODBC na **Microsoft. data. ODBC**a znovu zkompilovat aplikaci pro .NET Framework verze 1,0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET Framework pro Oracle  
 Počínaje verzí 1,1 je zprostředkovatel dat .NET Framework pro Oracle (<xref:System.Data.OracleClient>) součástí .NET Framework. Poskytovatel dat je k dispozici .NET Framework vývojářům verze 1,0 jako web ke stažení z [centra pro vývojáře pro přístup k datům a úložiště](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Pokud máte vyvinutou aplikaci pro .NET Framework verze 2,0 nebo novější, která používá poskytovatele dat pro připojení ke zdroji dat a chcete tuto aplikaci spustit v .NET Framework verze 1,0, je nutné stáhnout poskytovatele dat a nainstalovat jej na. NE. Systém T Framework verze 1,0.  
  
## <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Aby bylo možné spustit s oprávněním FullTrust, musí<xref:System.Data.SqlClient>být <xref:System.Data.OleDb>poskytovatelé dat .NET Framework v .NET Framework verze 1,0 (,). Jakékoli pokus o použití zprostředkovatelů dat .NET Framework k z .NET Framework verze 1,0 v zóně s oprávněním menším než FullTrust způsobuje <xref:System.Security.SecurityException>.  
  
 Počínaje verzí 2,0 .NET Framework ale všichni poskytovatelé dat .NET Framework můžete použít v částečně důvěryhodných zónách. Kromě toho se do zprostředkovatelů .NET Framework dat v .NET Framework verze 1,1 přidala nová funkce zabezpečení. Tato funkce umožňuje omezit, které připojovací řetězce je možné používat v určité zóně zabezpečení. Můžete také zakázat použití prázdných hesel pro konkrétní zónu zabezpečení. Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](code-access-security.md).  
  
 Vzhledem k tomu, že každá instalace .NET Framework má samostatný soubor Security. config, neexistují žádné problémy s kompatibilitou s nastavením zabezpečení. Pokud však vaše aplikace závisí na dalších možnostech zabezpečení ADO.NET obsažených v .NET Framework verze 1,1 a novější, nebudete ji moci distribuovat do systému verze 1,0.  
  
## <a name="sqlcommand-execution"></a>Spuštění metody SqlCommand  
 Počínaje verzí 1,1 .NET Framework se změnil způsob, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> jakým se spouští příkazy ve zdroji dat.  
  
 V .NET Framework verze 1,0 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> byly v kontextu uložené procedury **sp_executesql** provedeny všechny příkazy. V důsledku toho příkazy, které ovlivňují stav připojení (například nastavit počet na), platí pouze pro spuštění aktuálního příkazu. Stav připojení se nezmění pro žádné následné příkazy, které byly spuštěny, když je připojení otevřeno.  
  
 V .NET Framework verze 1,1 a novější <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> spustí příkaz pouze v kontextu uložené procedury **sp_executesql** , pokud příkaz obsahuje parametry, které poskytují výhody výkonu. Výsledkem je, že pokud příkaz ovlivňující stav připojení je zahrnutý v neparametrizovaném příkazu, upraví stav připojení pro všechny následné příkazy, které se spustí, když je připojení otevřené.  
  
 Vezměte v úvahu následující dávku příkazů spuštěných při volání <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 V .NET Framework verze 1,1 a novější zůstane počet pro všechny následné příkazy, které se spustí, když je připojení otevřené, i nadále. V .NET Framework verze 1,0 je počet Neurčen pouze pro aktuální spuštění příkazu.  
  
 Tato změna může ovlivnit dopředná i zpětnou kompatibilitu vaší aplikace, pokud závisíte na chování <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pro jednu z verzí .NET Framework.  
  
 Pro aplikace, které běží v předchozích i novějších verzích .NET Framework, můžete napsat kód, abyste se ujistili, že chování je stejné bez ohledu na verzi, na které používáte. Pokud se chcete ujistit, že příkaz upraví stav připojení pro všechny následné příkazy, doporučujeme spustit příkaz pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>příkazu. Pokud se chcete ujistit, že příkaz nemění připojení pro všechny následné příkazy, doporučujeme, abyste do příkazu obnovili stav připojení. Příklad:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
