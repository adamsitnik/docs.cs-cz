---
title: ICorDebugThread::GetID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: 48d2af96b50bf77347256b3d5860405e460a09d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133452"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="07ebe-102">ICorDebugThread::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="07ebe-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="07ebe-103">Načte aktuální identifikátor operačního systému aktivní části tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="07ebe-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ebe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07ebe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07ebe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07ebe-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="07ebe-106">mimo Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="07ebe-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07ebe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07ebe-107">Remarks</span></span>  
 <span data-ttu-id="07ebe-108">Identifikátor operačního systému může potenciálně změnit během provádění procesu a může být jinou hodnotou pro různé části vlákna.</span><span class="sxs-lookup"><span data-stu-id="07ebe-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ebe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07ebe-109">Requirements</span></span>  
 <span data-ttu-id="07ebe-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ebe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ebe-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="07ebe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07ebe-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="07ebe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07ebe-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07ebe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
