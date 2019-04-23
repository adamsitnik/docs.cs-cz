---
title: ICLRDebugging – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6edee34c8560c989040475fee4a35c6bd2ddb3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155711"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="fc038-102">ICLRDebugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc038-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="fc038-103">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="fc038-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc038-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fc038-104">Methods</span></span>  
  
|<span data-ttu-id="fc038-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fc038-105">Method</span></span>|<span data-ttu-id="fc038-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fc038-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc038-107">OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="fc038-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="fc038-108">Získá rozhraní "ICorDebugProcess", která odpovídá common language runtime (CLR) modulu načtené v procesu.</span><span class="sxs-lookup"><span data-stu-id="fc038-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="fc038-109">CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="fc038-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="fc038-110">Určuje, zda knihovnu, která byla [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní je stále používán, nebo může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="fc038-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc038-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc038-111">Remarks</span></span>  
 <span data-ttu-id="fc038-112">Můžete získat instanci `ICLRDebugging` rozhraní pomocí [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="fc038-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc038-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc038-113">Requirements</span></span>  
 <span data-ttu-id="fc038-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc038-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc038-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc038-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc038-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc038-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc038-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc038-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc038-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc038-118">See also</span></span>

- [<span data-ttu-id="fc038-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fc038-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fc038-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="fc038-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
