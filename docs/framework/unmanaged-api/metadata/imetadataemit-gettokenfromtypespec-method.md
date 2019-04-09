---
title: IMetaDataEmit::GetTokenFromTypeSpec – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09256deafdb42847f369664ec8c4bc96d72424d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177603"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="eca25-102">IMetaDataEmit::GetTokenFromTypeSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="eca25-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="eca25-103">Získá token metadat pro typ s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="eca25-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eca25-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eca25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eca25-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="eca25-106">[in] Podpis je definována.</span><span class="sxs-lookup"><span data-stu-id="eca25-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="eca25-107">[in] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="eca25-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="eca25-108">[out] `mdTypeSpec` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="eca25-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca25-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eca25-109">Requirements</span></span>  
 <span data-ttu-id="eca25-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca25-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca25-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eca25-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eca25-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eca25-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="eca25-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="eca25-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eca25-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eca25-114">See also</span></span>

- [<span data-ttu-id="eca25-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eca25-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="eca25-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eca25-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
