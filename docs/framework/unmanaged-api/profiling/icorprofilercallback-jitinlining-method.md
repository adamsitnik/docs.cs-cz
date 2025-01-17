---
title: ICorProfilerCallback::JITInlining – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82af06837ead9a00923c23d4ce145015308fbbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782807"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining – metoda
Oznámí profileru, že kompilátor just-in-time (JIT) Chystáte se vložit funkci v jiné funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parametry  
 `callerId`  
 [in] ID funkce, do kterého `calleeId` vloží funkce.  
  
 `calleeId`  
 [in] ID funkce má být vložen.  
  
 `pfShouldInline`  
 [out] `true` vkládání dojde k; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Profiler může nastavit `pfShouldInline` k `false` zabránit `calleeId` funkce nebude vložen do `callerId` funkce. Navíc můžete profiler globálně zakázat vložení vložené pomocí COR_PRF_DISABLE_INLINING hodnotu [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.  
  
 Vložené funkce vloženy nevyvolávejte události pro zadání nebo byste museli opustit. Proto musíte nastavit profiler `pfShouldInline` k `false` cílem vytvořit přesný graf volání. Nastavení `pfShouldInline` k `false` ovlivní výkon, protože vložený vkládání obvykle zvyšuje rychlost a snižuje počet samostatných události kompilace JIT pro vložené metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
