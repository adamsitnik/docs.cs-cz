---
title: Rozhraní ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 496959ecac5b16f1faa138aec90c5194d15cb105
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973750"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="ed6f1-102">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="ed6f1-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="ed6f1-103">Podtřída [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) , která poskytuje metody pro úpravu Il funkce, dotazování na informace z modulu runtime a pozastavení a obnovení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ed6f1-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="ed6f1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ed6f1-104">Methods</span></span>  

| <span data-ttu-id="ed6f1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ed6f1-105">Method</span></span>|<span data-ttu-id="ed6f1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ed6f1-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="ed6f1-107">Metoda EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="ed6f1-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="ed6f1-108">Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="ed6f1-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="ed6f1-109">Metoda IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="ed6f1-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="ed6f1-110">V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ed6f1-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="ed6f1-111">Metoda GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="ed6f1-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="ed6f1-112">Získá hodnotu nakonfigurované prahové hodnoty LOH.</span><span class="sxs-lookup"><span data-stu-id="ed6f1-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="ed6f1-113">Metoda RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="ed6f1-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="ed6f1-114">ReJITs požadované metody, jakož i všechny zažádané metody.</span><span class="sxs-lookup"><span data-stu-id="ed6f1-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="ed6f1-115">Metoda SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="ed6f1-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="ed6f1-116">Pozastaví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="ed6f1-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="ed6f1-117">Metoda ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="ed6f1-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="ed6f1-118">Obnoví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="ed6f1-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="ed6f1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed6f1-119">Requirements</span></span>  
<span data-ttu-id="ed6f1-120">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="ed6f1-120">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="ed6f1-121">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed6f1-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="ed6f1-122">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed6f1-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 
## <a name="see-also"></a><span data-ttu-id="ed6f1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed6f1-123">See also</span></span>
- [<span data-ttu-id="ed6f1-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ed6f1-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)