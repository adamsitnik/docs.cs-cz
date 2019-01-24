---
title: IHostControl::SetAppDomainManager – metoda
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fd0cf4f47781afb397c1fdd4b42715c710982e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580756"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="166b3-102">IHostControl::SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="166b3-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="166b3-103">Upozorňuje hostitele, vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="166b3-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="166b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166b3-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="166b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="166b3-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="166b3-106">[in] Číselný identifikátor vybraného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="166b3-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="166b3-107">[in] Ukazatel <xref:System.AppDomainManager> objekt, který implementuje hostitele jako `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="166b3-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="166b3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="166b3-108">Return Value</span></span>  
  
|<span data-ttu-id="166b3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="166b3-109">HRESULT</span></span>|<span data-ttu-id="166b3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="166b3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="166b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="166b3-111">S_OK</span></span>|<span data-ttu-id="166b3-112">`SetAppDomainManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="166b3-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="166b3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="166b3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="166b3-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="166b3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="166b3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="166b3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="166b3-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="166b3-116">The call timed out.</span></span>|  
|<span data-ttu-id="166b3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="166b3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="166b3-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="166b3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="166b3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="166b3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="166b3-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="166b3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="166b3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="166b3-121">E_FAIL</span></span>|<span data-ttu-id="166b3-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="166b3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="166b3-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="166b3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="166b3-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="166b3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="166b3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="166b3-125">Remarks</span></span>  
 <span data-ttu-id="166b3-126"><xref:System.AppDomainManager> Hostitel poskytuje mechanismus ke spuštění do spravovaného kódu a řídit vytváření a nastavení jednotlivých <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="166b3-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="166b3-127"><xref:System.AppDomainManager> Je načteno do každé <xref:System.AppDomain> při, který <xref:System.AppDomain> se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="166b3-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="166b3-128">Pokud se zvolí, modul CLR upozorňuje hostitele, že doména aplikace se vytvořila tak, že nastavíte hodnotu `pUnkAppDomainManager` parametru.</span><span class="sxs-lookup"><span data-stu-id="166b3-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="166b3-129">V jeho provádění `SetAppDomainManager` metody hostitele můžete nastavit název sestavení a typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="166b3-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="166b3-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="166b3-130">Requirements</span></span>  
 <span data-ttu-id="166b3-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="166b3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="166b3-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="166b3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="166b3-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="166b3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="166b3-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="166b3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166b3-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="166b3-135">See also</span></span>
- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="166b3-136">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="166b3-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
