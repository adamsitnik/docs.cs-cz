---
title: ICeeGen::GetString – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce015713ca7ed26c97348aa39f8170a85c8aa93c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745915"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="6253f-102">ICeeGen::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="6253f-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="6253f-103">Získá řetězec uložen na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="6253f-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="6253f-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="6253f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6253f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6253f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6253f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6253f-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="6253f-107">[in] Relativní virtuální adresa řetězec, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="6253f-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="6253f-108">[out] Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="6253f-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6253f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6253f-109">Requirements</span></span>  
 <span data-ttu-id="6253f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6253f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6253f-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6253f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6253f-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6253f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6253f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6253f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6253f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6253f-114">See also</span></span>

- [<span data-ttu-id="6253f-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6253f-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
