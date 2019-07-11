---
title: ICorRuntimeHost::CreateEvidence – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3b17ca32051cd5fc0673ef26124b855a66f9785
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779980"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="388e3-102">ICorRuntimeHost::CreateEvidence – metoda</span><span class="sxs-lookup"><span data-stu-id="388e3-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="388e3-103">Získá ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, který umožňuje hostiteli vytvořit legitimace zabezpečení k předání do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="388e3-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="388e3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="388e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="388e3-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="388e3-106">[out] Ukazatel rozhraní <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance použitý k vytvoření legitimace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="388e3-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="388e3-107">Je zadán ukazatel this `IUnknown`, aby volající by měl obvykle zavolat `QueryInterface` na tomto rozhraní pro získání ukazatele na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="388e3-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="388e3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="388e3-108">Return Value</span></span>  
  
|<span data-ttu-id="388e3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="388e3-109">HRESULT</span></span>|<span data-ttu-id="388e3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="388e3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="388e3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="388e3-111">S_OK</span></span>|<span data-ttu-id="388e3-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="388e3-112">The operation was successful.</span></span>|  
|<span data-ttu-id="388e3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="388e3-113">S_FALSE</span></span>|<span data-ttu-id="388e3-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="388e3-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="388e3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="388e3-115">E_FAIL</span></span>|<span data-ttu-id="388e3-116">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="388e3-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="388e3-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="388e3-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="388e3-118">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="388e3-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="388e3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="388e3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="388e3-120">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="388e3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="388e3-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="388e3-121">Remarks</span></span>  
 <span data-ttu-id="388e3-122">Tato metoda vrátí prázdnou kolekci, která nelze naplnit z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="388e3-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="388e3-123">Měli byste použít <xref:System.Security.Policy.Evidence> metoda místo.</span><span class="sxs-lookup"><span data-stu-id="388e3-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="388e3-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="388e3-124">Requirements</span></span>  
 <span data-ttu-id="388e3-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="388e3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="388e3-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="388e3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="388e3-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="388e3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="388e3-128">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="388e3-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388e3-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="388e3-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="388e3-130">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="388e3-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
