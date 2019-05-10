---
title: Funkce poskytované přes System.Transactions
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 75277090652cd439d3466a307790f4b918ddb090
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645714"
---
# <a name="features-provided-by-systemtransactions"></a>Funkce poskytované přes System.Transactions
Tato část popisuje, jak lze pomocí funkce poskytované <xref:System.Transactions> obor názvů pro zápis vlastní transakční aplikace a zdroj správce. Konkrétně v této části zahrnuje jak vytvořit a účast v transakci (místní nebo distribuované) s jedním nebo více účastníky.  
  
## <a name="overview-of-systemtransactions"></a>Přehled System.Transactions  
 Třídy v infrastrukturu <xref:System.Transactions> obor názvů umožňuje transakční programování jednoduchý a efektivní podporou transakcí vyvolaných v systému SQL Server, ADO.NET, Message Queuing (MSMQ) a společnosti Microsoft distribuované transakce koordinátor MSDTC (). <xref:System.Transactions> Obor názvů obsahuje oba explicitní programovací model založený na <xref:System.Transactions.Transaction> třídy, jakož i jazyka implicitní programování pomocí modelu <xref:System.Transactions.TransactionScope> třídy, ve kterém jsou transakce automaticky spravuje infrastruktury. Další informace o tom, jak vytvořit transakční aplikaci pomocí těchto dvou modelech naleznete v tématu [zápis transakční aplikace](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
 <xref:System.Transactions> Názvů také obsahuje typy pro vás k implementaci správce prostředků. Správce prostředků spravuje trvalé nebo přechodné dat použitý v transakci a funkcí ve spolupráci se správcem transakcí pro aplikace s zárukou atomicitu a izolaci. Správce transakcí, která je poskytována <xref:System.Transactions> infrastruktura podporuje transakce zahrnující více těkavých prostředků nebo jeden prostředek trvalý. Další informace o implementaci správce prostředků najdete v tématu [implementace správce prostředků](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md).  
  
 Správce transakcí také transparentně eskaluje místní transakce na distribuované transakce podle koordinaci se správcem transakcí založené na disku jako ovládacího prvku návrhu, pokud správce další trvalý prostředků zapsán, samotné se transakce. Existují dva způsoby klíče, <xref:System.Transactions> infrastruktury nabízí lepší výkon.  
  
- Dynamické eskalace, který zajišťuje, že <xref:System.Transactions> infrastruktury provede příkaz MSDTC pouze, když transakce zabírá více distribuovaných zdrojů. Další informace o dynamické eskalace. Zobrazit [eskalace správy transakce](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tématu.  
  
- Možné zařazení, což umožňuje prostředků, jako je například databáze, převzít vlastnictví transakce, pokud je pouze entity účastnící se transakce. Později, v případě potřeby <xref:System.Transactions> infrastruktury mohou i nadále eskalovat transakce na příkaz MSDTC pro správu. Tím omezíte další možnost používání příkaz MSDTC. Možné zařazení jsou zahrnuta do hloubky v tématu[optimalizace pomocí Jednofázového potvrzení a možné zařazení Jednofázového oznámení](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 <xref:System.Transactions> Obor názvů definuje tři úrovně důvěryhodnosti – AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission(DTP) a úplný vztah důvěryhodnosti - omezit přístup pro typy prostředků zpřístupňuje. Další informace o různých úrovně důvěryhodnosti naleznete v tématu [úrovně důvěryhodnosti zabezpečení v přístupu k prostředkům](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
### <a name="writing-a-transactional-application"></a>Zápis transakční aplikace  
 <xref:System.Transactions> Obor názvů poskytuje dva modely pro vytváření transakční aplikací. [Implementace implicitní transakce s využitím oboru transakcí](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření implicitní transakce pomocí <xref:System.Transactions.TransactionScope> třídy.  
  
 [Implementace explicitní transakce přes CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md) popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření explicitní transakce pomocí <xref:System.Transactions.CommittableTransaction> třídy.  
  
 Další témata týkající se zápisu transakční aplikace naleznete v tématu [zápis transakční aplikace](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Implementace správce prostředků  
 K implementaci správce prostředků, které se mohou účastnit v transakci, naleznete v tématu [implementace správce prostředků](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md). Tato část zahrnuje zařazení materiálu, potvrzení transakcí, obnovení po selhání a osvědčené postupy pro optimalizaci.
