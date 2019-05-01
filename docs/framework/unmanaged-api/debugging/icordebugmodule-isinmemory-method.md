---
title: ICorDebugModule::IsInMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79a8b0c3c56ffe2b8f57ec26f5942ee0d681194
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994835"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="30ec7-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="30ec7-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="30ec7-103">Získá hodnotu, která označuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="30ec7-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ec7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30ec7-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30ec7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30ec7-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="30ec7-106">[out] `true` Pokud tento modul existuje pouze v paměti; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="30ec7-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30ec7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30ec7-107">Remarks</span></span>  
 <span data-ttu-id="30ec7-108">Modul CLR (CLR) podporuje načítání modulů z nezpracované datové proudy bajtů.</span><span class="sxs-lookup"><span data-stu-id="30ec7-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="30ec7-109">Tyto moduly se nazývají *moduly v paměti* a neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="30ec7-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30ec7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30ec7-110">Requirements</span></span>  
 <span data-ttu-id="30ec7-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30ec7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30ec7-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30ec7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30ec7-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30ec7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30ec7-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30ec7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ec7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30ec7-115">See also</span></span>
