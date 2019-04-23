---
title: COR_PRF_FINALIZER_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5037f335e8d66c341d70d91d955a1ac7571b823
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123757"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="94436-102">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="94436-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="94436-103">Popisuje finalizační metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="94436-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94436-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94436-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="94436-105">Členové</span><span class="sxs-lookup"><span data-stu-id="94436-105">Members</span></span>  
  
|<span data-ttu-id="94436-106">Člen</span><span class="sxs-lookup"><span data-stu-id="94436-106">Member</span></span>|<span data-ttu-id="94436-107">Popis</span><span class="sxs-lookup"><span data-stu-id="94436-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="94436-108">Finalizační metoda je velmi důležité.</span><span class="sxs-lookup"><span data-stu-id="94436-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94436-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94436-109">Remarks</span></span>  
 <span data-ttu-id="94436-110">`COR_PRF_FINALIZER_FLAGS` Výčet je používán [icorprofilercallback2::finalizeableobjectqueued –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) metoda k popisu finalizační metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="94436-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94436-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94436-111">Requirements</span></span>  
 <span data-ttu-id="94436-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94436-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94436-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94436-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94436-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94436-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94436-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94436-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94436-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94436-116">See also</span></span>

- [<span data-ttu-id="94436-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="94436-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
