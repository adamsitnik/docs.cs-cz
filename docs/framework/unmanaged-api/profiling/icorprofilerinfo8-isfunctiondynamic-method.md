---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 71c4e749368dce65d5250b9ab78fd8713e9d61a0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973708"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="3d568-102">ICorProfilerInfo8:: IsFunctionDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="3d568-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>
  
  <span data-ttu-id="3d568-103">Určuje, jestli funkce nemá přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="3d568-103">Determines if a function does not have associated metadata.</span></span>    
  
## <a name="syntax"></a><span data-ttu-id="3d568-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d568-104">Syntax</span></span>  
  
```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d568-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d568-105">Parameters</span></span>  
 `functionId` \
  <span data-ttu-id="3d568-106">pro  `FunctionID` , Který identifikuje příslušnou funkci.</span><span class="sxs-lookup"><span data-stu-id="3d568-106">[in]  The `FunctionID` that identifies the function in question.</span></span>

  `isDynamic` \
  <span data-ttu-id="3d568-107">mimo Ukazatel na `BOOL` , který bude obsahovat hodnotu označující, zda nemá funkce žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="3d568-107">[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d568-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d568-108">Remarks</span></span>  
 <span data-ttu-id="3d568-109">Funkce je považována za Dynamic, pokud nemá žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="3d568-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="3d568-110">Některé metody, jako jsou zástupné procedury IL nebo metody LCG, nemají přidružená metadata, která lze načíst pomocí rozhraní IMetaDataImport API.</span><span class="sxs-lookup"><span data-stu-id="3d568-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="3d568-111">Tyto metody mohou být v profilerech zjištěny prostřednictvím ukazatelů instrukcí nebo naslouchat [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="3d568-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3d568-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d568-112">Requirements</span></span>  
 <span data-ttu-id="3d568-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d568-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d568-114">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d568-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d568-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d568-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d568-116">**Verze .NET Framework:** [! ZAHRNOUT[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="3d568-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d568-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d568-117">See also</span></span>
- [<span data-ttu-id="3d568-118">Rozhraní ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="3d568-118">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
