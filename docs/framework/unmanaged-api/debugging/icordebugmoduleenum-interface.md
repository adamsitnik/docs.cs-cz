---
title: ICorDebugModuleEnum – rozhraní 1
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6086d0a6e915915e8df115dc8b4c4218e77da601
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582328"
---
# <a name="icordebugmoduleenum-interface1"></a><span data-ttu-id="c2523-102">ICorDebugModuleEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="c2523-102">ICorDebugModuleEnum Interface1</span></span>
<span data-ttu-id="c2523-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="c2523-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2523-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c2523-104">Methods</span></span>  
  
|<span data-ttu-id="c2523-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2523-105">Method</span></span>|<span data-ttu-id="c2523-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2523-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2523-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c2523-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="c2523-108">Získá zadaný počet `ICorDebugModule` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="c2523-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2523-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2523-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2523-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="c2523-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2523-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2523-111">Requirements</span></span>  
 <span data-ttu-id="c2523-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2523-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2523-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2523-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2523-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2523-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2523-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2523-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2523-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2523-116">See also</span></span>
- [<span data-ttu-id="c2523-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c2523-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
