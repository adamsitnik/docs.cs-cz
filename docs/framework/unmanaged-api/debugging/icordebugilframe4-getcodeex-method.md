---
title: ICorDebugILFrame4::GetCodeEx – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: 9a74fd64e046ab3a8943e9a975e4de808c662677
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090949"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá ukazatel na kód, který tento rámec zásobníku provádí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 pro Člen výčtu [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , který určuje, zda je do rámce zahrnut převodní jazyk (IL) definovaný požadavkem ReJIT profileru.  
  
 `ppCode`  
 mimo Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který tento rámec zásobníku provádí.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná metodě [ICorDebugFrame:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) s tím rozdílem, že volitelně přistupuje k kódu definovanému požadavkem ReJIT profileru. Volání této metody s hodnotou `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání metody [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je metoda instrumentovaná, její IL nebude přístupná. `ILCODE_REJIT_IL` umožňuje ladicímu programu přístup k IL definovanému požadavkem ReJIT profileru. Pokud úroveň IL není instrumentovaná, `ppCode` je **null**a metoda vrátí `S_OK`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Průvodce](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
