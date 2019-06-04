---
title: ICLRRuntimeHost – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba02373aae33baf77b72323fabf1f6ca1fe4eecf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490245"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="8212c-102">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8212c-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="8212c-103">Poskytuje funkce podobné [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní v rozhraní .NET Framework verze 1, s následujícími změnami:</span><span class="sxs-lookup"><span data-stu-id="8212c-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="8212c-104">Přidání [sethostcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) metody nastavte ovládací prvek rozhraní hostitele.</span><span class="sxs-lookup"><span data-stu-id="8212c-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="8212c-105">Vynechání některé metody poskytované `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="8212c-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8212c-106">Metody</span><span class="sxs-lookup"><span data-stu-id="8212c-106">Methods</span></span>  
  
|<span data-ttu-id="8212c-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-107">Method</span></span>|<span data-ttu-id="8212c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8212c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8212c-109">ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="8212c-110">Použít ve scénářích nasazení na bázi manifest ClickOnce k určení aktivovat v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="8212c-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="8212c-111">ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="8212c-112">Určuje, <xref:System.AppDomain> v, který se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="8212c-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="8212c-113">ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="8212c-114">Vyvolá zadanou metodu zadaného typu v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="8212c-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="8212c-115">GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="8212c-116">Získá ukazatel rozhraní typu [iclrcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , hostitelů můžete použít k přizpůsobení aspekty modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8212c-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="8212c-117">GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="8212c-118">Získá číselný identifikátor <xref:System.AppDomain> , který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="8212c-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="8212c-119">SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="8212c-120">Nastaví ovládací prvek rozhraní hostitele.</span><span class="sxs-lookup"><span data-stu-id="8212c-120">Sets the host control interface.</span></span> <span data-ttu-id="8212c-121">Je nutné volat `SetHostControl` před voláním `Start`.</span><span class="sxs-lookup"><span data-stu-id="8212c-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="8212c-122">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="8212c-123">Inicializuje modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="8212c-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="8212c-124">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="8212c-125">Zastaví provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="8212c-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="8212c-126">UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="8212c-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="8212c-127">Uvolní <xref:System.AppDomain> , který odpovídá zadané číselný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="8212c-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8212c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8212c-128">Remarks</span></span>  
 <span data-ttu-id="8212c-129">Od verze rozhraní .NET Framework 4, použijte [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) rozhraní získat ukazatel [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní a poté zavolejte [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)metodu k získání ukazatele na `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="8212c-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="8212c-130">V dřívějších verzích rozhraní .NET Framework, hostitel získá ukazatel `ICLRRuntimeHost` instance voláním [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="8212c-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="8212c-131">Chcete-li poskytnout implementace některého z technologie v rozhraní .NET Framework verze 2.0, je nutné použít `ICLRRuntimeHost` místo `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="8212c-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8212c-132">Nevolejte [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním metody [executeapplication –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metodu aktivace manifest aplikace.</span><span class="sxs-lookup"><span data-stu-id="8212c-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="8212c-133">Pokud `Start` metoda je volána nejprve `ExecuteApplication` volání metody se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8212c-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8212c-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8212c-134">Requirements</span></span>  
 <span data-ttu-id="8212c-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8212c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8212c-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8212c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8212c-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8212c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8212c-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8212c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8212c-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8212c-139">See also</span></span>

- [<span data-ttu-id="8212c-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="8212c-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="8212c-141">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="8212c-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="8212c-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8212c-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8212c-143">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8212c-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="8212c-144">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8212c-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="8212c-145">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="8212c-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
