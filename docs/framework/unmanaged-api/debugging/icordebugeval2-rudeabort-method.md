---
title: ICorDebugEval2::RudeAbort – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988920"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort – metoda
Zruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `RudeAbort` neuvolní žádné zámky, které obsahuje Chyba při vyhodnocování, tak se relace ladění zůstane ve stavu unsafe. Volání této metody s nejvyšší opatrností.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
