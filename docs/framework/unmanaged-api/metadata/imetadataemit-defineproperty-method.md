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
ms.openlocfilehash: 69b398fa003abc0dba00ee89a9bb911a8c2dd6df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777511"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty – metoda
Vytvoří definici vlastností pro zadaný typ se zadaným `get` a `set` metoda přístupové objekty a získá token pro tuto definici vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] Token pro třídu nebo rozhraní, na kterém je definována vlastnost.  
  
 `szProperty`  
 [in] Název vlastnosti.  
  
 `dwPropFlags`  
 [in] Vlastnost příznaky.  
  
 `pvSig`  
 [in] Signatura vlastnosti.  
  
 `cbSig`  
 [in] Počet bajtů v `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [in] Typ vlastnosti na výchozí hodnotu.  
  
 `pValue`  
 [in] Výchozí hodnota pro vlastnost.  
  
 `cchValue`  
 [in] Počet (Unicode) znaky v `pValue`.  
  
 `mdSetter`  
 [in] Metoda, která nastaví hodnotu vlastnosti.  
  
 `mdGetter`  
 [in] Metoda, která vrací hodnotu vlastnosti.  
  
 `rmdOtherMethods[]`  
 [in] Pole jiné metody přidružený k vlastnosti. Ukončit pole pomocí `mdTokenNil`.  
  
 `pmdProp`  
 [out] `mdProperty` Token přiřazený.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
