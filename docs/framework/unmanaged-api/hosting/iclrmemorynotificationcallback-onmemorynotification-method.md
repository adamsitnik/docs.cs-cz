---
title: ICLRMemoryNotificationCallback::OnMemoryNotification – metoda
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d395c7eed27893e407b1944523a2f879b56c795d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489303"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="aa869-102">ICLRMemoryNotificationCallback::OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="aa869-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="aa869-103">Zatížení paměti v počítači upozorní common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="aa869-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa869-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa869-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa869-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa869-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="aa869-106">[in] Jeden z [ememoryavailable –](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) hodnoty, která přetížení paměti v počítači je právě se registruje.</span><span class="sxs-lookup"><span data-stu-id="aa869-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa869-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa869-107">Return Value</span></span>  
  
|<span data-ttu-id="aa869-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa869-108">HRESULT</span></span>|<span data-ttu-id="aa869-109">Popis</span><span class="sxs-lookup"><span data-stu-id="aa869-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa869-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa869-110">S_OK</span></span>|<span data-ttu-id="aa869-111">`OnMemoryNotification` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="aa869-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="aa869-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa869-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa869-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="aa869-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa869-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa869-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa869-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="aa869-115">The call timed out.</span></span>|  
|<span data-ttu-id="aa869-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa869-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa869-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="aa869-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa869-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa869-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa869-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="aa869-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa869-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa869-120">E_FAIL</span></span>|<span data-ttu-id="aa869-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="aa869-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa869-122">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="aa869-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa869-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa869-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa869-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa869-124">Remarks</span></span>  
 <span data-ttu-id="aa869-125">Zaregistruje zpětné volání, aby modul CLR `OnMemoryNotification` pomocí volání [ihostmemorymanager::registermemorynotificationcallback –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="aa869-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="aa869-126">Modul runtime používá informace vrácené při zpětném volání další paměť uvolnit, když hostitele hlásí, že prostředky jsou spuštěné nízké paměti.</span><span class="sxs-lookup"><span data-stu-id="aa869-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa869-127">Volání `OnMemoryNotification` není nikdy blokována.</span><span class="sxs-lookup"><span data-stu-id="aa869-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="aa869-128">Vždy vrátí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="aa869-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa869-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa869-129">Requirements</span></span>  
 <span data-ttu-id="aa869-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa869-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa869-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa869-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa869-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa869-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa869-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa869-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa869-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa869-134">See also</span></span>
- [<span data-ttu-id="aa869-135">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa869-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="aa869-136">RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="aa869-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="aa869-137">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa869-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
