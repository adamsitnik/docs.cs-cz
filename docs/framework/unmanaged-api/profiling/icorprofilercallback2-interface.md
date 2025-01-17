---
title: ICorProfilerCallback2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d36d8ef3bfdbd6a1acf787a91003e2ff3139a4d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963968"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 – rozhraní
Poskytuje metody, které jsou používány modulem CLR (Common Language Runtime) k oznamování profileru kódu, když dojde k odběru událostí, ke kterým má Profiler odběr. Rozhraní je rozšířením rozhraní ICorProfilerCallback. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) `ICorProfilerCallback2` To znamená, že poskytuje nová zpětná volání, která jsou představena ve verzi .NET Framework 2,0.  
  
> [!NOTE]
> Každá implementace metody musí vracet hodnotu HRESULT s hodnotou S_OK při úspěchu nebo E_FAIL při selhání. V současné době CLR ignoruje hodnotu HRESULT, kterou vrátí každé zpětné volání s výjimkou [ICorProfilerCallback:: objectReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FinalizeableObjectQueued – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Upozorní profiler kódu, že objekt s finalizační metodou byl zařazen do finalizačního vlákna pro provedení své `Finalize` metody.|  
|[GarbageCollectionFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Upozorní profileru, že se dokončilo uvolňování paměti a že se pro něj vystavila všechna zpětná volání uvolňování paměti.|  
|[GarbageCollectionStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Upozorní profiler kódu, že bylo zahájeno uvolňování paměti.|  
|[HandleCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Upozorní profiler kódu, že byl vytvořen popisovač uvolňování paměti.|  
|[HandleDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Upozorní profiler kódu, že byl zničen popisovač uvolňování paměti.|  
|[RootReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Oznamuje Profiler o kořenových odkazech poté, co došlo k uvolnění paměti. Tato metoda je rozšířením metody [ICorProfilerCallback:: RootReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) .|  
|[SurvivingReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Upozorní profiler na odkazy na objekty, které předržely uvolňování paměti.|  
|[ThreadNameChanged – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Upozorní profiler kódu, že se změnil název vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metodu v `ICorProfilerCallback` rozhraní (nebo `ICorProfilerCallback2`) k oznámení profileru, když dojde k odběru události, ke které se Profiler přihlásil. Toto je primární rozhraní zpětného volání, přes které CLR komunikuje s profilerem kódu.  
  
 Profiler kódu musí implementovat metody `ICorProfilerCallback` rozhraní. Pro .NET Framework 2,0 a novější verze musí Profiler také implementovat `ICorProfilerCallback2` metody. Každá implementace metody musí vracet hodnotu HRESULT s hodnotou S_OK při úspěchu nebo E_FAIL při selhání. V současné době CLR ignoruje hodnotu HRESULT, kterou vrátí každé zpětné volání s výjimkou [ICorProfilerCallback:: objectReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Profiler kódu se musí zaregistrovat v registru Microsoft Windows, jeho objekt com, který implementuje `ICorProfilerCallback` rozhraní a. `ICorProfilerCallback2` Profiler kódu se přihlašuje k odběru událostí, ke kterým chce dostávat oznámení voláním [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)v profileru. Profiler je pak schopný přijímat oznámení z modulu runtime, když dojde k události, která se chystá, nebo k ní došlo pouze v průběhu provádění procesu modulu runtime.  
  
> [!NOTE]
> Profiler registruje jeden objekt COM. Pokud je profiler cílen .NET Framework verze 1,0 nebo 1,1, musí objekt COM implementovat pouze metody `ICorProfilerCallback`. Pokud cílí na .NET Framework verze 2,0 a novější, musí objekt COM také implementovat metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
