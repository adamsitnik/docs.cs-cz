---
title: ICorDebugChain::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: d9430c5a1f37a0507b383ea5437f7d7fed706c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123866"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="54660-102">ICorDebugChain::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="54660-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="54660-103">Získá rozsah adres segmentu zásobníku pro tento řetěz.</span><span class="sxs-lookup"><span data-stu-id="54660-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54660-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54660-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54660-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54660-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="54660-106">mimo Ukazatel na hodnotu `CORDB_ADDRESS`, která je počáteční adresou segmentu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="54660-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="54660-107">mimo Ukazatel na hodnotu `CORDB_ADDRESS`, která je koncovou adresou segmentu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="54660-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54660-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54660-108">Remarks</span></span>  
 <span data-ttu-id="54660-109">Číselný rozsah má smysl pouze pro porovnání umístění rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="54660-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="54660-110">Nemůžete dělat žádné předpoklady o tom, co je ve skutečnosti uložené v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="54660-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54660-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54660-111">Requirements</span></span>  
 <span data-ttu-id="54660-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54660-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54660-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54660-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54660-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="54660-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54660-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54660-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
