---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 532052aa4f869861fbdb40ba0126bfd800eba942
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121866"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="953b5-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="953b5-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="953b5-103">Poskytuje metody, které vám pomůžou při odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="953b5-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="953b5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="953b5-104">Methods</span></span>  
  
|<span data-ttu-id="953b5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="953b5-105">Method</span></span>|<span data-ttu-id="953b5-106">Name</span><span class="sxs-lookup"><span data-stu-id="953b5-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="953b5-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="953b5-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="953b5-108">Získá aktuální kontext tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="953b5-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="953b5-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="953b5-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="953b5-110">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="953b5-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="953b5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="953b5-111">Remarks</span></span>  
 <span data-ttu-id="953b5-112">Členy rozhraní `ICorDebugVirtualUnwinder` jsou implementovány pomocí ladicího programu, aby bylo možné v zásobníku převinout zpět.</span><span class="sxs-lookup"><span data-stu-id="953b5-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="953b5-113">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="953b5-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="953b5-114">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="953b5-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="953b5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="953b5-115">Requirements</span></span>  
 <span data-ttu-id="953b5-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="953b5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="953b5-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="953b5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="953b5-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="953b5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="953b5-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="953b5-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="953b5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="953b5-120">See also</span></span>

- [<span data-ttu-id="953b5-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="953b5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="953b5-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="953b5-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
