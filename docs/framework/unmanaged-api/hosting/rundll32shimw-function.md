---
title: RunDll32ShimW – funkce
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
ms.openlocfilehash: e661bd82ecf6d804e852cca4a4478084edf303c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141498"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="a51ef-102">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="a51ef-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="a51ef-103">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="a51ef-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="a51ef-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a51ef-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a51ef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a51ef-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a51ef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a51ef-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="a51ef-107">pro Popisovač okna, ve kterém se zobrazí výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="a51ef-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="a51ef-108">pro Popisovač knihovny, která obsahuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="a51ef-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="a51ef-109">pro Řetězec, který určuje příkaz, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="a51ef-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="a51ef-110">pro Celé číslo, které určuje režim zobrazení okna výstup.</span><span class="sxs-lookup"><span data-stu-id="a51ef-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a51ef-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a51ef-111">Requirements</span></span>  
 <span data-ttu-id="a51ef-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a51ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a51ef-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a51ef-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a51ef-114">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a51ef-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a51ef-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a51ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a51ef-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a51ef-116">See also</span></span>

- [<span data-ttu-id="a51ef-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="a51ef-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
