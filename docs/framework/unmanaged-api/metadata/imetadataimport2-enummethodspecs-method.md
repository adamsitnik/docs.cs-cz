---
title: IMetaDataImport2::EnumMethodSpecs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3641fcda33a497293dbf87b419c8606847dc296
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049840"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="a02eb-102">IMetaDataImport2::EnumMethodSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="a02eb-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="a02eb-103">Získá enumerátor pro celou řadu MethodSpec tokeny přidružené k zadaným MethodDef nebo MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="a02eb-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a02eb-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a02eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a02eb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a02eb-106">[out v] Ukazatel na enumerátor pro `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="a02eb-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="a02eb-107">[in] Token MemberRef či MethodDef, který představuje metodu, jejíž metoda MethodSpec tokeny jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="a02eb-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="a02eb-108">Pokud hodnota `tk` je 0 (nula), se vytvořil výčet všech MethodSpec tokenů v oboru.</span><span class="sxs-lookup"><span data-stu-id="a02eb-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="a02eb-109">[out] Pole MethodSpec tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="a02eb-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a02eb-110">[in] Maximální požadovaný počet tokenů, které mají být umístěny `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="a02eb-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="a02eb-111">[out] Vrácený počet tokenů umístit v `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="a02eb-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a02eb-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a02eb-112">Return Value</span></span>  
  
|<span data-ttu-id="a02eb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a02eb-113">HRESULT</span></span>|<span data-ttu-id="a02eb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a02eb-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a02eb-115">`EnumMethodSpecs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a02eb-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a02eb-116">`phEnum` nemá žádné elementy člena.</span><span class="sxs-lookup"><span data-stu-id="a02eb-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="a02eb-117">V takovém případě `pcMethodSpecs` je nastavena na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="a02eb-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a02eb-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a02eb-118">Requirements</span></span>  
 <span data-ttu-id="a02eb-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a02eb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02eb-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a02eb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a02eb-121">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a02eb-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a02eb-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02eb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02eb-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a02eb-123">See also</span></span>

- [<span data-ttu-id="a02eb-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a02eb-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="a02eb-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a02eb-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
