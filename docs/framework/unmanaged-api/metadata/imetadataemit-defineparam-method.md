---
title: IMetaDataEmit::DefineParam – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d64a1ef21cd4fa4224609c7cd415c1611313769
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777544"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam – metoda
Vytvoří definici parametru se zadaným podpisem pro metodu odkazuje zadaný token a získá token pro tuto definici parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `md`  
 [in] Token pro metodu, jejíž parametr se zrovna definuje.  
  
 `ulParamSeq`  
 [in] Pořadové číslo parametru.  
  
 `szName`  
 [in] Název parametru v kódování Unicode.  
  
 `dwParamFlags`  
 [in] Příznaky pro parametr. To je bitová maska z `CorParamAttr` hodnoty.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** pro konstantní hodnoty.  
  
 `pValue`  
 [in] Konstantní hodnota parametru.  
  
 `cchValue`  
 [in] Velikost v znaky Unicode z `pValue`.  
  
 `ppd`  
 [out] `mdParamDef` Token přiřazený.  
  
## <a name="remarks"></a>Poznámky  
 Pořadí hodnot v `ulParamSeq` začínají znakem 1 pro parametry. Návratová hodnota má pořadové číslo 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
