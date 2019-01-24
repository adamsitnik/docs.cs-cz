---
title: IMetaDataEmit::DefineProperty – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71cdfc6b05288fef020e1aed1870a9a155588d47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543078"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="a84c3-102">IMetaDataEmit::DefineProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="a84c3-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="a84c3-103">Vytvoří definici vlastností pro zadaný typ se zadaným `get` a `set` metoda přístupové objekty a získá token pro tuto definici vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a84c3-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a84c3-104">Syntax</span></span>  
  
```  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a84c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a84c3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a84c3-106">[in] Token pro třídu nebo rozhraní, na kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a84c3-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="a84c3-107">[in] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a84c3-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="a84c3-108">[in] Vlastnost příznaky.</span><span class="sxs-lookup"><span data-stu-id="a84c3-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="a84c3-109">[in] Signatura vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a84c3-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="a84c3-110">[in] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="a84c3-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="a84c3-111">[in] Typ vlastnosti na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a84c3-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="a84c3-112">[in] Výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a84c3-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="a84c3-113">[in] Počet (Unicode) znaky v `pValue`.</span><span class="sxs-lookup"><span data-stu-id="a84c3-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="a84c3-114">[in] Metoda, která nastaví hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a84c3-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="a84c3-115">[in] Metoda, která vrací hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a84c3-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="a84c3-116">[in] Pole jiné metody přidružený k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a84c3-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="a84c3-117">Ukončit pole pomocí `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="a84c3-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="a84c3-118">[out] `mdProperty` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="a84c3-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a84c3-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a84c3-119">Requirements</span></span>  
 <span data-ttu-id="a84c3-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a84c3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a84c3-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a84c3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a84c3-122">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a84c3-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a84c3-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a84c3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84c3-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a84c3-124">See also</span></span>
- [<span data-ttu-id="a84c3-125">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a84c3-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a84c3-126">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a84c3-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
