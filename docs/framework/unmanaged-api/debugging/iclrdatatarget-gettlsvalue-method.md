---
title: ICLRDataTarget::GetTLSValue – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21fa9a17067f754fe9b13c4d32193856a57750ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227363"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="37e14-102">ICLRDataTarget::GetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="37e14-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="37e14-103">Získá hodnotu z úložiště thread local (TLS) ze zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="37e14-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="37e14-104">Tato metoda je volána službami common language runtime (CLR) přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="37e14-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e14-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37e14-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37e14-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37e14-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="37e14-107">[in] Operační systém identifikátor vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="37e14-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="37e14-108">[in] Index umístění.</span><span class="sxs-lookup"><span data-stu-id="37e14-108">[in] The index of the location.</span></span> <span data-ttu-id="37e14-109">Tato hodnota musí být platný index v místním úložišti ze zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="37e14-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="37e14-110">[out] Ukazatel `CLRDATA_ADDRESS` vrátil hodnotu, která určuje hodnotu z daného umístění protokolu TLS.</span><span class="sxs-lookup"><span data-stu-id="37e14-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37e14-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37e14-111">Remarks</span></span>  
 <span data-ttu-id="37e14-112">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="37e14-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37e14-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37e14-113">Requirements</span></span>  
 <span data-ttu-id="37e14-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37e14-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37e14-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="37e14-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="37e14-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37e14-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37e14-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37e14-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e14-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37e14-118">See also</span></span>

- [<span data-ttu-id="37e14-119">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37e14-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
