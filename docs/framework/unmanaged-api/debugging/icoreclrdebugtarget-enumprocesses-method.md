---
title: ICoreClrDebugTarget::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 4d1404e3f7565ee26edd94e059b7f01f8edd4dd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121847"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses – metoda
Vytvoří výčet procesů, které jsou spuštěny na vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcProcs`  
 mimo Počet procesů vrácených v `ppProcs`. Tato hodnota může být 0 (nula).  
  
 `ppProcs`  
 mimo Pole struktur [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) , které reprezentují procesy běžící na vzdáleném počítači.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Nástup.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppProcs`.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Další chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget:: FreeMemory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICoreClrDebugTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
