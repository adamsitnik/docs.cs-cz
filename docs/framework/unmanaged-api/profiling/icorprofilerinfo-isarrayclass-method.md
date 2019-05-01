---
title: ICorProfilerInfo::IsArrayClass – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 350221ae205636cef82581f3fe11367006dd8b2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968074"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="11fc0-102">ICorProfilerInfo::IsArrayClass – metoda</span><span class="sxs-lookup"><span data-stu-id="11fc0-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="11fc0-103">Určuje, zda dané třídy je třída pole.</span><span class="sxs-lookup"><span data-stu-id="11fc0-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11fc0-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11fc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11fc0-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="11fc0-106">[in] ID třídy prověřit.</span><span class="sxs-lookup"><span data-stu-id="11fc0-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="11fc0-107">[out] Ukazatel na hodnotu corelementtype – výčet, který označuje typ prvků pole.</span><span class="sxs-lookup"><span data-stu-id="11fc0-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="11fc0-108">[out] Ukazatel na ID třídy prvků pole, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="11fc0-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="11fc0-109">[out] Ukazatel na celé číslo označující pořadí (to znamená, počet rozměrů) v poli.</span><span class="sxs-lookup"><span data-stu-id="11fc0-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11fc0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11fc0-110">Remarks</span></span>  
 <span data-ttu-id="11fc0-111">Pokud dané třídy je třída pole, `IsArrayClass` metoda vrátí hodnotu S_OK HRESULT a hodnoty pro všechny nenulové výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="11fc0-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="11fc0-112">V opačném případě vrátí S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="11fc0-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11fc0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11fc0-113">Requirements</span></span>  
 <span data-ttu-id="11fc0-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11fc0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11fc0-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11fc0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11fc0-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11fc0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11fc0-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11fc0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fc0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11fc0-118">See also</span></span>

- [<span data-ttu-id="11fc0-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11fc0-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
