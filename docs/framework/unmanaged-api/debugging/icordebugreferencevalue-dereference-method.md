---
title: ICorDebugReferenceValue::Dereference – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: 6bb2a6b68a3c6e981a2d6c833d3f44d4c836bd23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123998"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="cc943-102">ICorDebugReferenceValue::Dereference – metoda</span><span class="sxs-lookup"><span data-stu-id="cc943-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="cc943-103">Načte objekt, na který je odkazováno.</span><span class="sxs-lookup"><span data-stu-id="cc943-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc943-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc943-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc943-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc943-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="cc943-106">mimo Ukazatel na adresu ICorDebugValue, která představuje objekt, na který odkazuje tento objekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="cc943-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc943-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc943-107">Remarks</span></span>  
 <span data-ttu-id="cc943-108">Objekt `ICorDebugValue` je platný pouze v případě, že jeho odkaz ještě není zakázán.</span><span class="sxs-lookup"><span data-stu-id="cc943-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc943-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc943-109">Requirements</span></span>  
 <span data-ttu-id="cc943-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc943-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc943-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc943-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc943-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cc943-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc943-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc943-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
