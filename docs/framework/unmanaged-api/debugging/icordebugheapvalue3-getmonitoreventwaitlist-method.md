---
title: ICorDebugHeapValue3::GetMonitorEventWaitList – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: 0fbff178efd4d0dff3593907b3d40e946be2ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121295"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList – metoda
Poskytuje uspořádaný seznam vláken, která jsou zařazená do fronty pro událost přidruženou ke zámku monitoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThreadEnum`  
 mimo Enumerátor ICorDebugThreadEnum, který poskytuje uspořádaný seznam vláken.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Seznam není prázdný.|  
|S_FALSE|Seznam je prázdný.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Prvním vláknem v seznamu je první vlákno, které je vydané při příštím volání <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Další vlákno v seznamu se uvolní při následujícím volání, a tak dále.  
  
 Pokud seznam není prázdný, vrátí tato metoda hodnotu S_OK. Pokud je seznam prázdný, vrátí metoda S_FALSE; v tomto případě je výčet stále platný, i když je prázdný.  
  
 V obou případech je rozhraní výčtu použitelné pouze pro dobu trvání aktuálního synchronizovaného stavu. Nicméně rozhraní vlákna, která jsou z něj, jsou platná až do ukončení vlákna.  
  
 Pokud `ppThreadEnum` není platný ukazatel, výsledek není definován.  
  
 Pokud dojde k chybě, kterou nelze určit, který z nich, pokud nějaká existuje, čeká na monitorování, metoda vrátí hodnotu HRESULT, která označuje selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
