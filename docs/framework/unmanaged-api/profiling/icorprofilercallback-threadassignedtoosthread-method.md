---
title: ICorProfilerCallback::ThreadAssignedToOSThread – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51c7235b4018fabb2ecf9c0db2800d5d9e54b327
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747137"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a>ICorProfilerCallback::ThreadAssignedToOSThread – metoda
Oznámí profileru, že spravovaným vláknem se implementuje pomocí vlákno konkrétní operační systém.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a>Parametry  
 `managedThreadId`  
 [in] Identifikátor spravované vlákno.  
  
 `osThreadId`  
 [in] Identifikátor vlákna operačního systému.  
  
## <a name="remarks"></a>Poznámky  
 `ThreadAssignedToOSThread` Zpětného volání existuje tak, že profiler může udržovat přesné mapování mezi vlákna vlákna operačního systému na spravovaná vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
