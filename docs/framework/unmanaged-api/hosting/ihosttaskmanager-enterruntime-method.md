---
title: IHostTaskManager::EnterRuntime – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 964e705376a404d3841a3d1de1f4d2a4d71ddfed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607092"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="db16b-102">IHostTaskManager::EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="db16b-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="db16b-103">Upozorňuje hostitele, že volání pro metodu nespravované, jako je na platformě vyvolat metodu, vrací řízení provádění do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="db16b-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db16b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db16b-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="db16b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db16b-105">Return Value</span></span>  
  
|<span data-ttu-id="db16b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db16b-106">HRESULT</span></span>|<span data-ttu-id="db16b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="db16b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db16b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="db16b-108">S_OK</span></span>|<span data-ttu-id="db16b-109">`EnterRuntime` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="db16b-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="db16b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db16b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db16b-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="db16b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db16b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db16b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db16b-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="db16b-113">The call timed out.</span></span>|  
|<span data-ttu-id="db16b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db16b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db16b-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="db16b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db16b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db16b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db16b-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="db16b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db16b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db16b-118">E_FAIL</span></span>|<span data-ttu-id="db16b-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="db16b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db16b-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="db16b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db16b-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db16b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="db16b-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="db16b-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="db16b-123">Nedostatek paměti nebyly k dispozici k dokončení požadované přidělení.</span><span class="sxs-lookup"><span data-stu-id="db16b-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db16b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db16b-124">Remarks</span></span>  
 <span data-ttu-id="db16b-125">`EnterRuntime` se volá se, aby upozornil hostitele, který nespravovanou funkci, pro kterou dřívějším volání [leaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) metoda bylo provedeno, byl dokončen a vrací řízení provádění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="db16b-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db16b-126">[Reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) se volá se, aby upozornil hostitele, který nespravovanou funkci, pro kterou dřívějším volání `LeaveRuntime` bylo provedeno, provádí volání do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="db16b-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db16b-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db16b-127">Requirements</span></span>  
 <span data-ttu-id="db16b-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db16b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db16b-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db16b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db16b-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db16b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db16b-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db16b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db16b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db16b-132">See also</span></span>
- [<span data-ttu-id="db16b-133">Rozšířená interoperabilita modelu COM</span><span class="sxs-lookup"><span data-stu-id="db16b-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="db16b-134">Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke</span><span class="sxs-lookup"><span data-stu-id="db16b-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="db16b-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db16b-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="db16b-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db16b-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="db16b-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db16b-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="db16b-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db16b-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="db16b-139">LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="db16b-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
