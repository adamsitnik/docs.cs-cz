---
title: CorDebugGuidToTypeMapping – struktura
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49290a37ca7ea101e3c8b458a5daa4995cb3beee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610042"
---
# <a name="cordebugguidtotypemapping-structure"></a>CorDebugGuidToTypeMapping – struktura
Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID na jeho odpovídající objekt ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`iid`|Identifikátor GUID v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.|  
|`pType`|Ukazatel na objekt ICorDebugType, který poskytuje informace o typu v mezipaměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
