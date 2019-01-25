---
title: ICorDebugProcess5::GetTypeFields – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f688993bfd8e6bef66451b075a49f31efe641cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497102"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields – metoda
Poskytuje informace o polích, které patří k typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identifikátor typu, jehož informace v poli je načten.  
  
 `celt`  
 [in] Počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, jejichž informace z pole má být načtena.  
  
 `fields`  
 [out] Pole [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, které poskytují informace o polích, které patří do typu.  
  
 `pceltNeeded`  
 [out] Ukazatel na počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objektů obsažených v `fields`.  
  
## <a name="remarks"></a>Poznámky  
 `celt` Parametr, který určuje počet polí, jejichž informace v poli Metoda používá k naplnění `fields`, by měl odpovídat hodnotě `COR_TYPE_LAYOUT::numFields` pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
