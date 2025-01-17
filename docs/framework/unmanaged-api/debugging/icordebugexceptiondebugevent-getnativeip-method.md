---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP – metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 42fedd20d7560dd84a2abf0efce227393035bc38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084749"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>ICorDebugExceptionDebugEvent:: GetNativeIP – metoda
Získá nativní ukazatel instrukcí pro tuto událost ladění výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIP`  
 mimo Ukazatel na ukazatel instrukcí pro tuto událost ladění výjimky. Další informace naleznete v části Poznámky.  
  
## <a name="remarks"></a>Poznámky  
 Význam tohoto ukazatele instrukcí závisí na typu události, jak je znázorněno v následující tabulce.  
  
|Typ události|Význam `pStackPointer` hodnoty|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Adresa instrukce pro zpracování chyb.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Adresa kódu v rámci, která je označena metodou [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) , ve které by provádění pokračovalo, pokud nebyla vyvolána žádná výjimka. Výjimka může nebo nemusí způsobit jiný kód, jako je například blok catch klauzule `try/catch/finally`, který má být proveden v tomto rámci.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Adresa kódu, kde se spuštění obslužné rutiny `catch` spustí v rámci snímku označeného metodou [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) .|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pIP` je 0.|  
  
 Typ události je k dispozici z metody [ICorDebugDebugEvent:: GetEventKind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) .  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugExceptionDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
