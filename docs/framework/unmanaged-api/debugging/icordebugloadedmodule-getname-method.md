---
title: Metoda ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e97c7c793df389dd6a8f670e985a9c9384eab639
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703741"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="dbd06-102">Metoda ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="dbd06-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="dbd06-103">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="dbd06-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbd06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbd06-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbd06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbd06-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="dbd06-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dbd06-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="dbd06-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dbd06-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="dbd06-108">[out] Pole znaků, které obsahují název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="dbd06-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbd06-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbd06-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbd06-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dbd06-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbd06-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbd06-111">Requirements</span></span>  
 <span data-ttu-id="dbd06-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbd06-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbd06-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbd06-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbd06-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbd06-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbd06-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbd06-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd06-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbd06-116">See also</span></span>
- [<span data-ttu-id="dbd06-117">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbd06-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="dbd06-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dbd06-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
