---
title: ICorDebugAppDomain::GetId – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0aefc19ca0c255c9c8ea40fcc12fc5cba1b00f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996252"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="a5f06-102">ICorDebugAppDomain::GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="a5f06-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="a5f06-103">Získá jedinečný identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5f06-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5f06-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5f06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5f06-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="a5f06-106">[out] Jedinečný identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5f06-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5f06-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5f06-107">Remarks</span></span>  
 <span data-ttu-id="a5f06-108">Identifikátor pro doménu aplikace je jedinečný v rámci nadřazeného procesu.</span><span class="sxs-lookup"><span data-stu-id="a5f06-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5f06-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5f06-109">Requirements</span></span>  
 <span data-ttu-id="a5f06-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5f06-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5f06-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5f06-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5f06-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5f06-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5f06-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5f06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
