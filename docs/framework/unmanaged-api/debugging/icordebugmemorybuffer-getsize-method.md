---
title: ICorDebugMemoryBuffer::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5984addb41c33468068f7ad24a15533f75dc367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714721"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="69771-102">ICorDebugMemoryBuffer::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="69771-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="69771-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="69771-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69771-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69771-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69771-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69771-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="69771-106">[out] Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="69771-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69771-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69771-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69771-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="69771-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69771-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69771-109">Requirements</span></span>  
 <span data-ttu-id="69771-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69771-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69771-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69771-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69771-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69771-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69771-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69771-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69771-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69771-114">See also</span></span>
- [<span data-ttu-id="69771-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69771-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="69771-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="69771-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
