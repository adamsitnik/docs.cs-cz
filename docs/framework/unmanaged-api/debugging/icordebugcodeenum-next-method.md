---
title: ICorDebugCodeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3aeae294d92a6dc9effc7f3baa51a35e4f2b544
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476630"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="363fa-102">ICorDebugCodeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="363fa-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="363fa-103">Získá zadaný počet instancí "ICorDebugCode" z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="363fa-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="363fa-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="363fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="363fa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="363fa-106">[in] Počet `ICorDebugCode` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="363fa-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="363fa-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugCode` objektu.</span><span class="sxs-lookup"><span data-stu-id="363fa-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="363fa-108">[out] Ukazatel na počet `ICorDebugCode` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="363fa-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="363fa-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="363fa-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="363fa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="363fa-110">Requirements</span></span>  
 <span data-ttu-id="363fa-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="363fa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="363fa-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="363fa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="363fa-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="363fa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="363fa-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="363fa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363fa-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="363fa-115">See also</span></span>


