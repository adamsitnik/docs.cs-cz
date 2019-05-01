---
title: ICorProfilerModuleEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99db173aa7c6064d9f635412d539cc2d4509b24a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040934"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="c5635-102">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5635-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="c5635-103">Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly načtené aplikace nebo profileru.</span><span class="sxs-lookup"><span data-stu-id="c5635-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5635-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c5635-104">Methods</span></span>  
  
|<span data-ttu-id="c5635-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c5635-105">Method</span></span>|<span data-ttu-id="c5635-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c5635-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5635-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="c5635-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="c5635-108">Získá ukazatel rozhraní na kopii této `ICorProfilerModuleEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c5635-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="c5635-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="c5635-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="c5635-110">Získá počet spravované moduly, které byly načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5635-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="c5635-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c5635-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="c5635-112">Získá zadaný počet souvislých moduly ze sekvenčního kolekci objektů, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="c5635-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="c5635-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="c5635-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="c5635-114">Přesune kurzor čítače výčtu na počáteční pozici pořadí.</span><span class="sxs-lookup"><span data-stu-id="c5635-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="c5635-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="c5635-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="c5635-116">Přejde z pozice kurzoru čítače výčtu tak, aby zadaný počet prvků, které se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="c5635-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5635-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5635-117">Remarks</span></span>  
 <span data-ttu-id="c5635-118">`ICorProfilerModuleEnum` Rozhraní je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="c5635-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="c5635-119">Umožňuje příjemce pole prvků o přijetí změn od odesílatele rychlostí, která je vhodná pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="c5635-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="c5635-120">Jinými slovy příjemce je explicitně řídit tok prvků pole, aby se předešlo problémy související s předání velkých polí jako parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="c5635-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5635-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5635-121">Requirements</span></span>  
 <span data-ttu-id="c5635-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5635-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5635-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5635-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5635-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5635-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5635-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5635-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5635-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5635-126">See also</span></span>

- [<span data-ttu-id="c5635-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5635-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c5635-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c5635-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c5635-129">EnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="c5635-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
