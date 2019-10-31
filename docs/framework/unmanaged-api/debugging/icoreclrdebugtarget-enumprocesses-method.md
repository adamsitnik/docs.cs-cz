---
title: ICoreClrDebugTarget::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 4d1404e3f7565ee26edd94e059b7f01f8edd4dd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121847"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="dae75-102">ICoreClrDebugTarget::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="dae75-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="dae75-103">Vytvoří výčet procesů, které jsou spuštěny na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="dae75-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dae75-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dae75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dae75-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="dae75-106">mimo Počet procesů vrácených v `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="dae75-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="dae75-107">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="dae75-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="dae75-108">mimo Pole struktur [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) , které reprezentují procesy běžící na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="dae75-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dae75-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dae75-109">Return Value</span></span>  
 <span data-ttu-id="dae75-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dae75-110">S_OK</span></span>  
 <span data-ttu-id="dae75-111">Nástup.</span><span class="sxs-lookup"><span data-stu-id="dae75-111">Success.</span></span>  
  
 <span data-ttu-id="dae75-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dae75-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="dae75-113">Nelze přidělit dostatek paměti pro `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="dae75-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="dae75-114">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="dae75-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="dae75-115">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="dae75-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dae75-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dae75-116">Remarks</span></span>  
 <span data-ttu-id="dae75-117">Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget:: FreeMemory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dae75-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dae75-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dae75-118">Requirements</span></span>  
 <span data-ttu-id="dae75-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae75-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae75-120">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="dae75-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="dae75-121">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="dae75-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="dae75-122">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="dae75-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae75-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dae75-123">See also</span></span>

- [<span data-ttu-id="dae75-124">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dae75-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
