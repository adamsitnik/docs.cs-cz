---
title: Trvalost pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: db0e4acc76f758004948857fc0b23a9cbc62f244
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669340"
---
# <a name="workflow-persistence"></a>Trvalost pracovního postupu
Trvalost pracovního postupu je trvalý zachycení stavu instance pracovního postupu, nezávisle na informace o procesu nebo počítač. To se provádí k poskytování známého bodu obnovení pro instanci pracovního postupu v případě selhání systému, nebo pro zachování paměti podle uvolnění instancí pracovních postupů, které nejsou aktivně provádějící práce nebo přesunout do jiného stavu instance pracovního postupu z jednoho uzlu uzel v serverové farmě.  
  
 Trvalost umožňuje procesu flexibilitu, škálovatelnost, zotavení i v případě selhání a možnost spravovat efektivněji paměť. Proces trvalého zahrnuje identifikaci bod trvalost, shromažďují data, která mají být uloženy a nakonec delegování skutečnou velikost úložiště dat do poskytovatele trvalého chování.  
  
 K povolení trvalosti pro pracovní postup, je nutné přidružit úložiště instance s **WorkflowApplication** nebo **hostitele služby pracovního postupu** jak je uvedeno v [jak: Povolení trvalosti pro pracovní postupy a služby pracovních postupů](how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** a **hostitele služby pracovního postupu** použití v úložišti instancí, které jsou k nim má přiřazené k povolení uchování instance pracovního postupu do trvalého úložiště a načtení instance pracovního postupu do paměť podle data instance pracovního postupu, který je uložen v úložišti stálost.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Se dodává s **SqlWorkflowInstanceStore** třídu, která umožňuje trvalost dat a metadata o instance pracovního postupu do databáze serveru SQL Server 2005 nebo SQL Server 2008. Zobrazit [Store Instance pracovního postupu SQL](sql-workflow-instance-store.md) další podrobnosti.  
  
 K ukládání a načítání dat specifické pro aplikaci společně s informace související s instancí pracovního postupu, můžete vytvořit účastníci trvalosti, které rozšiřují <xref:System.Activities.Persistence.PersistenceParticipant> třídy. Trvalého účastníka se účastní procesu trvalost uložit vlastní serializovat data do trvalého úložiště, načtení dat z úložiště instancí do paměti a provádět žádná další logika v rámci transakce trvalosti. Další informace najdete v tématu [účastníci trvalosti](persistence-participants.md).  
  
 Windows Server App Fabric zjednodušuje proces konfigurace trvalosti. Další informace najdete v tématu [koncepty trvalosti pomocí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Implicitní body trvalosti  
 Následující seznam obsahuje příklady podmínek, na kterých je trvalá pracovního postupu při úložiště instance je přiřazen pracovní postup.  
  
- Když **TransactionScope** dokončení aktivity nebo **TransactedReceiveScope** dokončení aktivity.  
  
- Jakmile se instance pracovního postupu změní nečinnosti a **WorkflowIdleBehavior** je nastavena na hostitele pracovního postupu. K tomu dojde, například při použití zasílání zpráv aktivity nebo **zpoždění** aktivity.  
  
- Když aplikace WorkflowApplication změní na nečinnosti a **PersistableIdle** aplikace je nastavena na **PersistableIdleAction.Persist**.  
  
- Pokud hostitelská aplikace je nastaven na zachovat nebo uvolnit instance pracovního postupu.  
  
- Když instance pracovního postupu je ukončen nebo dokončení.  
  
- Když **trvalého** aktivity spustí.  
  
- Instance pracovního postupu vyvinuté pomocí předchozí verze Windows Workflow Foundation Pokud nalezne bod trvalost během interoperabilní provádění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
- [Úložiště instancí pracovních postupů SQL](sql-workflow-instance-store.md)  
  
- [Úložiště instancí](instance-stores.md)  
  
- [Účastníci trvalosti](persistence-participants.md)  
  
- [Osvědčené postupy pro trvalost](persistence-best-practices.md)  
  
- [Netrvalé instance pracovních postupů](non-persisted-workflow-instances.md)  
  
- [Pozastavení a obnovení pracovního postupu](pausing-and-resuming-a-workflow.md)
