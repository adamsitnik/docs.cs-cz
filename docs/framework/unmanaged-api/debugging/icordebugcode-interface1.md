---
title: ICorDebugCode – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75cc8ea9d88dda42362f50b519864b1a78e1a64b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960791"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="0e854-102">ICorDebugCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e854-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="0e854-103">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0e854-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e854-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e854-104">Methods</span></span>  
  
|<span data-ttu-id="0e854-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-105">Method</span></span>|<span data-ttu-id="0e854-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0e854-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e854-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="0e854-108">Vytvoří zarážku v zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="0e854-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="0e854-109">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="0e854-110">Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="0e854-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="0e854-111">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="0e854-112">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="0e854-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="0e854-113">Tato metoda je zastaralá. místo toho použijte [ICorDebugCode2:: getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0e854-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="0e854-114">GetEnCRemapSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="0e854-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="0e854-115">Not implemented.</span></span>|  
|[<span data-ttu-id="0e854-116">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="0e854-117">Načte "ICorDebugFunction" spojený s tímto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="0e854-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="0e854-118">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="0e854-119">Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunů MSIL na nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="0e854-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="0e854-120">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="0e854-121">Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="0e854-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="0e854-122">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="0e854-123">Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="0e854-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="0e854-124">IsIL – metoda</span><span class="sxs-lookup"><span data-stu-id="0e854-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="0e854-125">Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="0e854-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e854-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e854-126">Remarks</span></span>  
 <span data-ttu-id="0e854-127">Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód.</span><span class="sxs-lookup"><span data-stu-id="0e854-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="0e854-128">Objekt "ICorDebugFunction", který představuje kód jazyka MSIL, může mít k němu `ICorDebugCode` přidružené buď nula, nebo jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="0e854-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="0e854-129">K objektu "ICorDebugFunction", který představuje nativní kód, může být přidružen `ICorDebugCode` libovolný počet objektů.</span><span class="sxs-lookup"><span data-stu-id="0e854-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e854-130">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0e854-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e854-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e854-131">Requirements</span></span>  
 <span data-ttu-id="0e854-132">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e854-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e854-133">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0e854-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e854-134">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e854-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e854-135">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e854-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e854-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e854-136">See also</span></span>

- [<span data-ttu-id="0e854-137">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e854-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="0e854-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0e854-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
