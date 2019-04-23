---
title: ICLRDebugManager::SetConnectionTasks – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88078fa34910dca642eae3cf261c9e00fae4f27a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201985"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="2c8d3-102">ICLRDebugManager::SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="2c8d3-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="2c8d3-103">Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c8d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c8d3-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c8d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c8d3-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="2c8d3-106">[in] Identifikátor konkrétního hostitele pro připojení ke které chcete přidružit `ppCLRTask` pole.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="2c8d3-107">[in] Počet členů `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="2c8d3-108">Tato hodnota musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="2c8d3-109">[in] Pole `ICLRTask` ukazatele pro přidružení k připojení identifikovaný `id`.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="2c8d3-110">Toto pole musí obsahovat alespoň jeden člen.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c8d3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2c8d3-111">Return Value</span></span>  
  
|<span data-ttu-id="2c8d3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c8d3-112">HRESULT</span></span>|<span data-ttu-id="2c8d3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2c8d3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c8d3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c8d3-114">S_OK</span></span>|<span data-ttu-id="2c8d3-115">`SetConnectionTasks` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="2c8d3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c8d3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c8d3-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c8d3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c8d3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c8d3-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-119">The call timed out.</span></span>|  
|<span data-ttu-id="2c8d3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c8d3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c8d3-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c8d3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c8d3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c8d3-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c8d3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c8d3-124">E_FAIL</span></span>|<span data-ttu-id="2c8d3-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c8d3-126">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c8d3-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2c8d3-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2c8d3-128">E_INVALIDARG</span></span>|<span data-ttu-id="2c8d3-129">[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nebyla volána pomocí této hodnoty `id`, nebo `dwCount` nebo `id` se žádný nebo jeden z prvků `ppCLRTask` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c8d3-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c8d3-130">Remarks</span></span>  
 <span data-ttu-id="2c8d3-131">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, `SetConnectionTasks`, a [endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), pro seznamy úloh přidružení s identifikátory a popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2c8d3-132">Tyto tři metody musí být volána v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="2c8d3-133">`BeginConnection` je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="2c8d3-134">`SetConnectionTasks` je volána dále k poskytování sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="2c8d3-135">`EndConnection` Chcete-li odebrat přidružení seznamu úkolů a identifikátor a popisný název se nazývá poslední. Volání pro různá připojení však mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="2c8d3-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c8d3-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c8d3-136">Requirements</span></span>  
 <span data-ttu-id="2c8d3-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c8d3-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c8d3-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c8d3-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c8d3-139">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c8d3-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c8d3-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c8d3-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c8d3-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c8d3-141">See also</span></span>

- [<span data-ttu-id="2c8d3-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c8d3-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2c8d3-143">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c8d3-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="2c8d3-144">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="2c8d3-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="2c8d3-145">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="2c8d3-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="2c8d3-146">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c8d3-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
