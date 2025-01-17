---
title: ICorProfilerCallback::ObjectsAllocatedByClass – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4229332ef3a079a5a294e27b624dde0e1fb46691
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782954"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass – metoda
Informuje o počtu instancí každé zadané třídy, které byly vytvořeny od posledního shromažďování dat paměti profilerem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cClassCount`  
 [in] Velikost `classIds` a `cObjects` pole.  
  
 `classIds`  
 [in] Pole ID, kde každé ID Určuje třídu s jednu nebo víc instancí tříd.  
  
 `cObjects`  
 [in] Pole celých čísel, kde každé celé číslo určuje počet instancí pro odpovídající třídu v `classIds` pole.  
  
## <a name="remarks"></a>Poznámky  
 `classIds` a `cObjects` pole jsou paralelní pole. Například `classIds[i]` a `cObjects[i]` odkazovat na stejnou třídu. Pokud od předchozí uvolňování paměti kolekce byla vytvořena žádná instance třídy, třída je vynechán. `ObjectsAllocatedByClass` Zpětné volání, nebudou podávat objekty přidělené ve velkých objektových haldách.  
  
 Čísla hlášených `ObjectsAllocatedByClass` jsou pouze odhady. Přesný počet, použijte [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 `classIds` Pole může obsahovat jeden nebo více položky s hodnotou null, pokud odpovídající `cObjects` pole obsahuje typy, které jsou uvolnění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
