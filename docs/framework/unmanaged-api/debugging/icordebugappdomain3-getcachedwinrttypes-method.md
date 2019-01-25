---
title: ICorDebugAppDomain3::GetCachedWinRTTypes – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afbe368d58c96c8ddc97ccc3bb077ce768b229b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566109"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypes – metoda
Získá enumerátor pro všechny uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppGuidToTypeEnum`  
 [out] Ukazatel [icordebugguidtotypeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) objektu rozhraní, které můžete zobrazit výčet spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy aktuálně načtené v doméně aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugAppDomain3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
