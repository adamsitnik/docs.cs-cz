---
title: ICorDebugMutableDataTarget::ContinueStatusChanged Method
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52b5c63f35732655834768eb5b914406203d423c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135613"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="2d56f-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span><span class="sxs-lookup"><span data-stu-id="2d56f-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="2d56f-103">Změní stav pokračování pro zbývající ladění události u zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d56f-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d56f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d56f-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d56f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d56f-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="2d56f-106">Identifikátor vlákna operačního systému definovaný.</span><span class="sxs-lookup"><span data-stu-id="2d56f-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="2d56f-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje novou požadovaný stav pokračování.</span><span class="sxs-lookup"><span data-stu-id="2d56f-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d56f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d56f-108">Remarks</span></span>  
 <span data-ttu-id="2d56f-109">Volání ladicího programu `ContinueStatusChanged` metody volá metodu icordebug –, který vyžaduje aktuální ladicí událost zpracovávat tak, aby se potenciálně liší od způsobu, ve kterém je obvykle zpracovává.</span><span class="sxs-lookup"><span data-stu-id="2d56f-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="2d56f-110">Například, pokud dojde k výjimce nezpracovaných a ladicí program vyžaduje operace, která by zrušit výjimku (například [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo `FuncEval`), toto rozhraní API slouží k vyžádání, že se výjimka bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="2d56f-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d56f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d56f-111">Requirements</span></span>  
 <span data-ttu-id="2d56f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d56f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d56f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d56f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d56f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d56f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d56f-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d56f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d56f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d56f-116">See also</span></span>

- [<span data-ttu-id="2d56f-117">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d56f-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="2d56f-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2d56f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
