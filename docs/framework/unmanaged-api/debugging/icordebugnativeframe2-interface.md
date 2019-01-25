---
title: ICorDebugNativeFrame2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc664d308d4db3e97597d785eda159e32255fa54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520370"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="ab4d1-102">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab4d1-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="ab4d1-103">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="ab4d1-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab4d1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab4d1-104">Methods</span></span>  
  
|<span data-ttu-id="ab4d1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab4d1-105">Method</span></span>|<span data-ttu-id="ab4d1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ab4d1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab4d1-107">IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="ab4d1-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="ab4d1-108">Určuje, zda aktuální rámec je podřízený blok.</span><span class="sxs-lookup"><span data-stu-id="ab4d1-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="ab4d1-109">IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="ab4d1-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="ab4d1-110">Určuje, zda zadaného rámce je nadřazeného člena aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="ab4d1-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="ab4d1-111">GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="ab4d1-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="ab4d1-112">Vrátí celková velikost parametry do zásobníku na x86 operačních systémů.</span><span class="sxs-lookup"><span data-stu-id="ab4d1-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab4d1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab4d1-113">Remarks</span></span>  
 <span data-ttu-id="ab4d1-114">Toto rozhraní rozšiřuje logicky "icordebugnativeframe –" rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ab4d1-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab4d1-115">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="ab4d1-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab4d1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab4d1-116">Requirements</span></span>  
 <span data-ttu-id="ab4d1-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab4d1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab4d1-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab4d1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab4d1-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab4d1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab4d1-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab4d1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4d1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab4d1-121">See also</span></span>

- [<span data-ttu-id="ab4d1-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ab4d1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ab4d1-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="ab4d1-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
