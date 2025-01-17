---
title: ICorProfilerCallback4::ReJITError – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b01f38fbcf1cb0439b82a933b37971515b06ac4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758157"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError – metoda
Oznámí profileru, že kompilátor just-in-time (JIT) došlo k chybě v procesu opětovnou kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] `ModuleID` Ve které byl proveden pokus o opětovnou kompilaci se nezdařilo.  
  
 `methodId`  
 [in] `MethodDef` Metody, na kterém byl proveden pokus o opětovnou kompilaci se nezdařilo.  
  
 `functionId`  
 [in] Instance funkce, která se znovu kompilovaný nebo metodu označenou pro opětovnou kompilaci. Tato hodnota může být `NULL` -li k selhání došlo na základě za metoda místo základ instance (například pokud profiler zadaný token neplatná metadata pro metodu překompilovat).  
  
 `hrStatus`  
 [in] HRESULT označující podstatu tohoto selhání. V části stav HRESULTS seznam hodnot.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty v tomto zpětném volání jsou ignorovány.  
  
## <a name="status-hresults"></a>HRESULT – stav  
  
|Stav pole HRESULT|Popis|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` Nebo `methodDef` token je `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modul dosud není zcela načteno, nebo je právě uvolňován.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Zadaný modul se generuje dynamicky (třeba podle `Reflection.Emit`) a proto není podporována touto metodou.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Metoda je vytvořena instance na kolekční sestavení a není tedy možné zopakovat. Všimněte si, že typy a funkce definované v kontextu jiných reflexe (například `List<MyCollectibleStruct>`) může být vytvořena na kolekční sestavení.|  
|E_OUTOFMEMORY|Modul CLR má nedostatek paměti při pokusu označit zadanou metodu pro rekompilace JIT.|  
|Ostatní|Operační systém vrátil chybu mimo ovládací prvek CLR. Například pokud selže volání systému ke změně ochrany přístupu k paměti stránky, se zobrazí chyba operačního systému.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
