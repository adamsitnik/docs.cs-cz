---
title: ICorDebugClass::GetModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 205b7670bac55d428d7458b7accaee5e00b00b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745580"
---
# <a name="icordebugclassgetmodule-method"></a>ICorDebugClass::GetModule – metoda
Získá modul, který definuje tuto třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pModule`  
 [out] Ukazatel na adresu icordebugmodule – objekt, který představuje modul, ve které tato třída je definována.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
