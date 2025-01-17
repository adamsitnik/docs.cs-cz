---
title: ICorProfilerCallback4::ReJITCompilationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58293929b576493d3751f9ce30ba00cec92e180c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758163"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted – metoda
Oznámí profileru, kompilátor just-in-time (JIT) byla spuštěna znovu zkompilovat funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, které kompilátor JIT začal znovu zkompilovat.  
  
 `rejitId`  
 [in] ID rekompilace novou verzi funkce.  
  
 `fIsSafeToBlock`  
 [in] `true` k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime. Hodnota `true` nepoškodí modul runtime, ale může mít vliv na výsledky profilace.  
  
## <a name="remarks"></a>Poznámky  
 Je možné přijímat více než jednu dvojici `ReJITCompilationStarted` a [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) metoda volá pro každou funkci kvůli způsobu, jakým modul runtime konstruktor třídy obslužné rutiny. Například modul runtime spustí znovu zkompilovat metoda A, ale třída konstruktor třídy B musí být spuštěn. Proto se modul runtime konstruktor třídy B se znovu zkompiluje a spustí ji. Je spuštěn konstruktoru, provede volání do metody A, což způsobí, že metoda A znovu překompilovat. V tomto scénáři je první opětovnou kompilaci metody A zastaveno. Ale i pokusí znovu zkompilovat metoda se nahlásí se rekompilace JIT – události.  
  
 Profilovací programy musí podporovat posloupnost zpětných volání rekompilace JIT v případech, kde dva vláken současně, aby zpětná volání. Například, vlákna A zavolá `ReJITCompilationStarted`; však před volání vlákna A [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), vlákno B vyvolá [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID – funkce z `ReJITCompilationStarted` zpětného volání pro vlákno A. Může se zdát, že ID funkce by neměl být ještě platný protože volání [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) nebyl dosud nebylo přijato pomocí profileru. Ale v takovém případě ID funkce je platný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
