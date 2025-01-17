---
title: ICorDebugMDA – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 4201fe23bf54388510088e21471edce91809e94c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129790"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA – rozhraní
Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDescription – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Získá řetězec obsahující popis tohoto typu MDA.|  
|[GetFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Získá příznaky přidružené k tomuto MDA.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Získá řetězec obsahující název této aplikace MDA.|  
|[GetOSThreadId – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Získá identifikátor vlákna operačního systému, na kterém je tento MDA spuštěn.|  
|[GetXML – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Získá úplný datový proud XML přidružený k tomuto MDA.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
