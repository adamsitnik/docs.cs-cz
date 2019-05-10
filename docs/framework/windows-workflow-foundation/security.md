---
title: Zabezpečení
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: d82ad52dd24dbfcb66887693563b08c995baa63a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619497"
---
# <a name="security"></a>Zabezpečení
Store Instance SQL pracovní postup používá Tyhle role zabezpečení databázi zabezpečit přístup k informacím o stavu instance databáze trvalosti.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Tato role má ke čtení a oprávnění k zápisu do veřejné zobrazení a spuštění práva k uložené procedury, které jsou zahrnuty při vytváření, načítání a ukládání instancí.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Tato role má oprávnění jen pro čtení k veřejné zobrazení.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Tato role má práva spuštění uložené procedury, které jsou součástí procesu aktivace instance. Další informace o aktivaci instance najdete v tématu [aktivace Instance](instance-activation.md). Uživatelský účet, pod kterým obecný hostitele (jako je například služba pracovního postupu správy [!INCLUDE[dublin](../../../includes/dublin-md.md)]) spuštění měla být přidána do této databázové roli.  
  
 Další informace o zabezpečení pro úložiště trvalosti pomocí systému Windows Server App Fabric najdete v tématu [konfiguraci zabezpečení pro trvalého úložiště v prostředcích infrastruktury aplikace](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Klient, který má přístup k vlastní instance data v úložišti instancí má přístup do všech ostatních instancích ve stejném úložišti instancí. V úložišti instancí nepodporuje zadání oprávnění zabezpečení na úrovni instance. By měl vytvořit samostatnou instanci úložišť a mapovat různé skupiny/uživatele mít přístup do různých úložišť.
