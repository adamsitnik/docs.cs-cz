---
title: IMetaDataAssemblyImport::GetAssemblyRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6c550ff7af2dda8bc06afd771024fe290339904
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089780"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="5734b-102">IMetaDataAssemblyImport::GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5734b-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="5734b-103">Získá sadu vlastností pro odkaz na sestavení s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="5734b-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5734b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5734b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5734b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5734b-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="5734b-106">[in] `mdAssemblyRef` Token metadat, který představuje odkaz na sestavení, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5734b-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="5734b-107">[out] Ukazatel na veřejný klíč nebo token metadat.</span><span class="sxs-lookup"><span data-stu-id="5734b-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="5734b-108">[out] Počet bajtů vrácených veřejný klíč nebo token.</span><span class="sxs-lookup"><span data-stu-id="5734b-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="5734b-109">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="5734b-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5734b-110">[in] Velikost v široké znaky z `szName`.</span><span class="sxs-lookup"><span data-stu-id="5734b-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5734b-111">[out] Ukazatel na počet skutečně vrácených v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="5734b-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5734b-112">[out] Ukazatel na assemblymetadata – struktura, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="5734b-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="5734b-113">[out] Ukazatel na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="5734b-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="5734b-114">Toto je hodnota hash pomocí algoritmu SHA-1 z `PublicKey` vlastnost sestavení odkazuje, není-li arfFullOriginator příznak [assemblyrefflags –](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) výčtu je nastavena.</span><span class="sxs-lookup"><span data-stu-id="5734b-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="5734b-115">[out] Počet široké znaky v hodnotě vrácené hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="5734b-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="5734b-116">[out] Ukazatel na příznaky, které popisují metadata použité u sestavení.</span><span class="sxs-lookup"><span data-stu-id="5734b-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="5734b-117">Hodnota příznaků je kombinace jedné nebo více [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5734b-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5734b-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5734b-118">Return Value</span></span>  
 <span data-ttu-id="5734b-119">Tato metoda vrátí hodnotu S_OK Pokud neproběhne úspěšně. v opačném případě vrátí jednu z kódy chyb, které jsou definovány v souboru hlaviček Winerror.h.</span><span class="sxs-lookup"><span data-stu-id="5734b-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5734b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5734b-120">Requirements</span></span>  
 <span data-ttu-id="5734b-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5734b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5734b-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5734b-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5734b-123">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5734b-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5734b-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5734b-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5734b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5734b-125">See also</span></span>

- [<span data-ttu-id="5734b-126">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5734b-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
