---
title: ICorProfilerModuleEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eecb2a5da9dddaccbab7fcc6d74af6e4c6bfb72c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775137"
---
# <a name="icorprofilermoduleenumskip-method"></a>ICorProfilerModuleEnum::Skip – metoda
Posune kurzor enumerátor z aktuálního umístění tak, aby zadaný počet prvků, které se přeskočí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Počet prvků, které mají být přeskočeny.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`celt` elementy byly vynechány.|  
|S_FALSE|Méně než `celt` prvky byly přeskočeny, což znamená, že neexistují žádné další prvky.|  
  
## <a name="remarks"></a>Poznámky  
 Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerModuleEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
