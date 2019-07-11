---
title: ICLRDebugging::CanUnloadNow – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e69957bdc5f70aba361b2574a7f6ebe26d4dd43f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738391"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="cddd0-102">ICLRDebugging::CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="cddd0-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="cddd0-103">Určuje, zda knihovnu, která byla [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní je stále používán, nebo může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="cddd0-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cddd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cddd0-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cddd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cddd0-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="cddd0-106">[in] Základní adresa modul v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="cddd0-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cddd0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cddd0-107">Return Value</span></span>  
 <span data-ttu-id="cddd0-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="cddd0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cddd0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cddd0-109">HRESULT</span></span>|<span data-ttu-id="cddd0-110">Popis</span><span class="sxs-lookup"><span data-stu-id="cddd0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cddd0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cddd0-111">S_OK</span></span>|<span data-ttu-id="cddd0-112">Modul, který je odkazován `hmodule` může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="cddd0-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="cddd0-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cddd0-113">S_FALSE</span></span>|<span data-ttu-id="cddd0-114">Modul, který je odkazován `hmodule` je stále používán.</span><span class="sxs-lookup"><span data-stu-id="cddd0-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="cddd0-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="cddd0-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="cddd0-116">Zadaný modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="cddd0-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cddd0-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="cddd0-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cddd0-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cddd0-118">Remarks</span></span>  
 <span data-ttu-id="cddd0-119">Tato metoda zkontroluje, zda mají všechny výskyty `ICorDebug*` byly vydány rozhraní a žádné vlákno je nyní v rámci volání [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cddd0-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cddd0-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cddd0-120">Requirements</span></span>  
 <span data-ttu-id="cddd0-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cddd0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cddd0-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cddd0-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cddd0-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cddd0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cddd0-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cddd0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddd0-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cddd0-125">See also</span></span>

- [<span data-ttu-id="cddd0-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cddd0-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cddd0-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="cddd0-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
