---
title: ICorDebugManagedCallback2::CreateConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300baeb4184bbb73704563671ab907fafbdb5284
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472626"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="ec612-102">ICorDebugManagedCallback2::CreateConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="ec612-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="ec612-103">Upozorní ladicího programu, že se vytvořila nová připojení.</span><span class="sxs-lookup"><span data-stu-id="ec612-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec612-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec612-104">Syntax</span></span>  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec612-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec612-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="ec612-106">[in] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém byla vytvořena připojení</span><span class="sxs-lookup"><span data-stu-id="ec612-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="ec612-107">[in] ID připojení tímto novým připojením.</span><span class="sxs-lookup"><span data-stu-id="ec612-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="ec612-108">[in] Ukazatel na název připojení tímto novým připojením.</span><span class="sxs-lookup"><span data-stu-id="ec612-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec612-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec612-109">Remarks</span></span>  
 <span data-ttu-id="ec612-110">A `CreateConnection` aktivuje zpětného volání v některém z následujících případech:</span><span class="sxs-lookup"><span data-stu-id="ec612-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="ec612-111">Pokud ladicí program připojí k procesu, který obsahuje připojení.</span><span class="sxs-lookup"><span data-stu-id="ec612-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="ec612-112">V takovém případě modul runtime bude generovat a odeslání `CreateConnection` událostí a [icordebugmanagedcallback2::changeconnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) události pro každé připojení v procesu.</span><span class="sxs-lookup"><span data-stu-id="ec612-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
-   <span data-ttu-id="ec612-113">Když hostitel volá [iclrdebugmanager::beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) v [API pro hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec612-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec612-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec612-114">Requirements</span></span>  
 <span data-ttu-id="ec612-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec612-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec612-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec612-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec612-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec612-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec612-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec612-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec612-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec612-119">See also</span></span>
- [<span data-ttu-id="ec612-120">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec612-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="ec612-121">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec612-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
