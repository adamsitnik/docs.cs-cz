---
title: ICorProfilerInfo::GetFunctionInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4b39e53af7abaf25cc4a563bfbec8450b1e57d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780657"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>ICorProfilerInfo::GetFunctionInfo – metoda
Získá nadřazené třídu a metadata token pro zadanou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, pro které se získat token nadřazené třídu a metadata.  
  
 `pClassId`  
 [out] Ukazatel na nadřazené třídy funkce.  
  
 `pModuleId`  
 [out] Ukazatel na modul, ve kterém je definována funkce nadřazené třídy.  
  
 `pToken`  
 [out] Ukazatel na token metadat pro funkci.  
  
## <a name="remarks"></a>Poznámky  
 Profiler kódu může volat [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získání metadat rozhraní pro daný modul. Token metadat, který je vrácen do umístění odkazuje `pToken` lze použít k přístupu k metadatům pro funkci.  
  
 `ClassID` Funkce na obecné třídě nemusí být dosažitelný bez další kontextové informace o použití funkce. V takovém případě `pClassId` bude 0. Profiler kódu používejte [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) s hodnotou COR_PRF_FRAME_INFO poskytnout další kontext.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
