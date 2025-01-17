---
title: ICorProfilerCallback3::ProfilerAttachComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 26c9c85f22f9d8201214dc56f32718e055a97801
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779261"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete – metoda
Volá se, modulem common language runtime (CLR), která označuje, že profiler nyní volat [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) a [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) můžete projít metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `ProfilerAttachComplete` Zpětného volání je vydané po [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda je volána. Označuje následující:  
  
- Zpětná volání, které bylo vyžádáno profilerem v `InitializeForAttach` aktivaci.  
  
- Profiler teď můžete provádět zachytávání přidružené identifikátory bez obavy z chybějícího upozornění.  
  
 Modul CLR bude ignorovat návratovou hodnotu z této zpětné volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
