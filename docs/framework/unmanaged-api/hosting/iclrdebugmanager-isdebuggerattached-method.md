---
title: ICLRDebugManager::IsDebuggerAttached – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30159748c1103cbc8efaf8929387052bbe5c3ec7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773134"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="d1b53-102">ICLRDebugManager::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="d1b53-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="d1b53-103">Získá hodnotu určující, zda je připojen ladicí program k procesu.</span><span class="sxs-lookup"><span data-stu-id="d1b53-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1b53-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1b53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1b53-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d1b53-106">[out] `true` Pokud ladicí program je připojené k procesu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="d1b53-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1b53-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d1b53-107">Return Value</span></span>  
  
|<span data-ttu-id="d1b53-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1b53-108">HRESULT</span></span>|<span data-ttu-id="d1b53-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d1b53-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1b53-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1b53-110">S_OK</span></span>|<span data-ttu-id="d1b53-111">`IsDebuggerAttached` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d1b53-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="d1b53-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1b53-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1b53-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d1b53-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1b53-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1b53-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1b53-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d1b53-115">The call timed out.</span></span>|  
|<span data-ttu-id="d1b53-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1b53-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1b53-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d1b53-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1b53-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1b53-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1b53-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d1b53-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1b53-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1b53-120">E_FAIL</span></span>|<span data-ttu-id="d1b53-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d1b53-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1b53-122">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d1b53-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1b53-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d1b53-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1b53-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1b53-124">Remarks</span></span>  
 <span data-ttu-id="d1b53-125">`IsDebuggerAttached` umožňuje hostiteli zjistit CLR k určení, zda je připojen ladicí program k procesu.</span><span class="sxs-lookup"><span data-stu-id="d1b53-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1b53-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1b53-126">Requirements</span></span>  
 <span data-ttu-id="d1b53-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1b53-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1b53-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1b53-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1b53-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1b53-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1b53-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1b53-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b53-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1b53-131">See also</span></span>

- [<span data-ttu-id="d1b53-132">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1b53-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d1b53-133">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1b53-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="d1b53-134">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1b53-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
