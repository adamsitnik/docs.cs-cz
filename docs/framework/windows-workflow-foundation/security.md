---
title: Zabezpečení
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: f47b75fa1fd345869f560326861ebc31e6b5e1a9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045317"
---
# <a name="security"></a>Zabezpečení
Úložiště instance pracovního postupu SQL používá následující role zabezpečení databáze k zabezpečení přístupu k informacím o stavu instance v databázi trvalosti.  
  
- **System. Activities. DurableInstancing. InstanceStoreUsers**. Tato role má oprávnění ke čtení a zápisu pro veřejná zobrazení a práva k provádění uložených procedur, které jsou součástí vytváření, načítání a ukládání instancí.  
  
- **System. Activities. DurableInstancing. InstanceStoreObservers**. Tato role má k veřejným zobrazením přístup jen pro čtení.  
  
- **System. Activities. DurableInstancing. WorkflowActivationUsers**. Tato role má práva ke spouštění uložených procedur, které jsou součástí procesu aktivace instance. Další informace o aktivaci instance najdete v tématu [Aktivace instance](instance-activation.md). V rámci této databázové role by se měl přidat uživatelský účet, pod kterým se spustí obecný hostitel (například služba správy pracovních postupů hostujících funkcí Windows serveru AppFabricu).  
  
 Další informace o zabezpečení pro úložiště trvalosti s Windows Server App Fabric najdete v tématu [Konfigurace zabezpečení pro úložiště Persistence v App Fabric](https://go.microsoft.com/fwlink/?LinkId=201208) .  
  
> [!CAUTION]
> Klient, který má přístup ke svým vlastním datům instance v úložišti instancí, má přístup ke všem ostatním instancím ve stejném úložišti instancí. Úložiště instancí nepodporuje určení oprávnění zabezpečení na úrovni instance. Měli byste vytvořit samostatná úložiště instancí a mapovat různé skupiny/uživatele tak, aby měli přístup k různým úložištím.
