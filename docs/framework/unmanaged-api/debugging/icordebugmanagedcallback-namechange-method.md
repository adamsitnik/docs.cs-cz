---
title: ICorDebugManagedCallback::NameChange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 975353403a82956912fa41047253bb0dbf138502
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124121"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="63601-102">ICorDebugManagedCallback::NameChange – metoda</span><span class="sxs-lookup"><span data-stu-id="63601-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="63601-103">Upozorní ladicího programu, že došlo ke změně názvu domény aplikace nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="63601-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63601-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63601-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63601-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63601-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="63601-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který měl buď změnit název nebo, který obsahuje vlákna, která měla změnit název.</span><span class="sxs-lookup"><span data-stu-id="63601-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="63601-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, které měly změnu názvu.</span><span class="sxs-lookup"><span data-stu-id="63601-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63601-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63601-108">Requirements</span></span>  
 <span data-ttu-id="63601-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63601-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63601-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63601-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63601-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63601-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63601-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63601-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63601-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63601-113">See also</span></span>

- [<span data-ttu-id="63601-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63601-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
