---
title: ICorDebugGuidToTypeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: f6f190cd5b2f208df5a4ed88b650af671f2e6c5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138517"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="19976-102">ICorDebugGuidToTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="19976-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="19976-103">Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.</span><span class="sxs-lookup"><span data-stu-id="19976-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19976-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19976-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19976-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19976-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="19976-106">pro Počet objektů mapování typu GUID na typ, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="19976-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="19976-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , který MAPUJE prostředí Windows Runtime GUID na odpovídající objekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="19976-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="19976-108">mimo Ukazatel na počet [CorDebugGuidToTypeMapping –ch](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objektů, které jsou ve skutečnosti vráceny v `values`.</span><span class="sxs-lookup"><span data-stu-id="19976-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19976-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19976-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19976-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19976-110">Requirements</span></span>  
 <span data-ttu-id="19976-111">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="19976-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="19976-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19976-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19976-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="19976-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19976-114">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19976-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19976-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19976-115">See also</span></span>

- [<span data-ttu-id="19976-116">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19976-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="19976-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="19976-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
