---
title: ICorProfilerThreadEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c394c2b17404351bd0813ab1eb21230a1edd9de
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781092"
---
# <a name="icorprofilerthreadenumskip-method"></a>ICorProfilerThreadEnum::Skip – metoda
Posune kurzor čítače výčtu ze své aktuální pozici pro přeskočení zadaný počet prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerThreadEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
