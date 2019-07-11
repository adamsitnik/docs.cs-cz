---
title: IAssemblyCache::CreateAssemblyCacheItem – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4432b17e5d9aa875d8346b3329cd618e15222040
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771018"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="d180b-102">IAssemblyCache::CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="d180b-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="d180b-103">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="d180b-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d180b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d180b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d180b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d180b-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d180b-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="d180b-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="d180b-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d180b-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="d180b-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="d180b-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="d180b-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="d180b-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d180b-110">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d180b-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d180b-111">`pvReserved` musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d180b-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="d180b-112">[out] Vrácený `IAssemblyCacheItem` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="d180b-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d180b-113">[in, volitelné] Uncanonicalized, oddělené čárkami `name=value` dvojice.</span><span class="sxs-lookup"><span data-stu-id="d180b-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d180b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d180b-114">Requirements</span></span>  
 <span data-ttu-id="d180b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d180b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d180b-116">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d180b-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d180b-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d180b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d180b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d180b-118">See also</span></span>

- [<span data-ttu-id="d180b-119">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d180b-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="d180b-120">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d180b-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
