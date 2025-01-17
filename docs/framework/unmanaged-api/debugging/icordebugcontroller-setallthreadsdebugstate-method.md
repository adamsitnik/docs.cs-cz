---
title: ICorDebugController::SetAllThreadsDebugState – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: 1190f83e2671216cf1627eeb710ba576e4b2ec93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125359"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState – metoda
Nastaví stav ladění pro všechna spravovaná vlákna v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `state`  
 pro Hodnota výčtu "CorDebugThreadState –", která určuje stav vlákna pro ladění.  
  
 `pExceptThisThread`  
 pro Ukazatel na objekt "ICorDebugThread", který představuje vlákno, které má být vyloučeno z nastavení stavu ladění. Pokud je tato hodnota null, nezbavuje se žádné vlákno.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `SetAllThreadsDebugState` může ovlivnit vlákna, která nejsou viditelná prostřednictvím [metody EnumerateThreads –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), takže vlákna, která byla pozastavená metodou `SetAllThreadsDebugState`, bude nutné obnovit pomocí metody `SetAllThreadsDebugState`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
