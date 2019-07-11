---
title: IHostTask::SetCLRTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 884fedd6e8c2d79e895591e38b59cd3abb27275e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764390"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="79b9c-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="79b9c-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="79b9c-103">Přidruží `ICLRTask` instance s aktuálním [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="79b9c-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79b9c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79b9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79b9c-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="79b9c-106">[in] Ukazatel rozhraní k `ICLRTask` instance má být spojen s aktuálním `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="79b9c-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79b9c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="79b9c-107">Return Value</span></span>  
  
|<span data-ttu-id="79b9c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79b9c-108">HRESULT</span></span>|<span data-ttu-id="79b9c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="79b9c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79b9c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="79b9c-110">S_OK</span></span>|<span data-ttu-id="79b9c-111">`SetCLRTask` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="79b9c-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="79b9c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79b9c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79b9c-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="79b9c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79b9c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79b9c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79b9c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="79b9c-115">The call timed out.</span></span>|  
|<span data-ttu-id="79b9c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79b9c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79b9c-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="79b9c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79b9c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79b9c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79b9c-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="79b9c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79b9c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79b9c-120">E_FAIL</span></span>|<span data-ttu-id="79b9c-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="79b9c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79b9c-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="79b9c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79b9c-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="79b9c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79b9c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79b9c-124">Remarks</span></span>  
 <span data-ttu-id="79b9c-125">Volání CLR `SetCLRTask` pro přidružení `ICLRTask` instance s aktuálním `IHostTask` instance, který byl vytvořen voláním [ihosttaskmanager::createtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="79b9c-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79b9c-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79b9c-126">Requirements</span></span>  
 <span data-ttu-id="79b9c-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79b9c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b9c-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79b9c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79b9c-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79b9c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79b9c-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b9c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b9c-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79b9c-131">See also</span></span>

- [<span data-ttu-id="79b9c-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79b9c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="79b9c-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79b9c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="79b9c-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79b9c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="79b9c-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79b9c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
