---
title: ICorDebugModule3::CreateReaderForInMemorySymbols – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 2655151d34275b1b0fdc5d0903dd57fcea646014
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137307"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols – metoda
Vytvoří čtečku symbolů ladění pro dynamický modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>Parametry  
 riid  
 pro IID rozhraní modelu COM, které má být vráceno. Obvykle se jedná o [rozhraní ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 mimo Ukazatel na ukazatel na vrácené rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Čtecí modul se úspěšně vytvořil.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Modul není v paměti nebo dynamickém modulu.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Aplikace nedodala symboly nebo ještě nejsou k dispozici.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Nelze vytvořit čtecí modul.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda může být také použita k vytvoření objektu čtečky symbolů pro moduly v paměti (nedynamické), ale pouze po prvním zpřístupnění symbolů (označeno zpětným voláním [metody UpdateModuleSymbols –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) ).  
  
 Tato metoda vrací novou instanci čtenáře pokaždé, když je volána (například [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). Proto by měl ladicí program uložit výsledek do mezipaměti a požádat o novou instanci pouze v případě, že došlo ke změně podkladových dat (tj. při přijetí zpětného volání [metody LoadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).  
  
 Dynamické moduly nemají k dispozici žádné symboly, dokud není načten první typ (jak je uvedeno v zpětném volání [metody LoadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
