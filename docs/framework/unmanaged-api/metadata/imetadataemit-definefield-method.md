---
title: IMetaDataEmit::DefineField – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8553665ba64a1c8e1cb6398d94cd1f772a566ed
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466658"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField – metoda
Vytvoří definici pro pole s podpisem Zadaná metadata a získá token pro tuto definici pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypeDef` Token pro nadřazené třídu nebo rozhraní.  
  
 `szName`  
 [in] Název pole v kódování Unicode.  
  
 `dwFieldFlags`  
 [in] Atributy pole. To je bitová maska z `CorFieldAttr` hodnoty.  
  
 `pvSigBlob`  
 [in] Podpis pole jako objekt BLOB.  
  
 `cbSigBlob`  
 [in] Počet bajtů v `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** Pro konstantní hodnoty. Jedná se `CorElementType` hodnotu. Pokud definujete není konstantní hodnotu pro pole, použijte `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] Konstantní hodnoty pro pole.  
  
 `cchValue`  
 [in] Velikost v znaky (Unicode) `pValue`.  
  
 `pmd`  
 [out] `mdFieldDef` Token přiřazený.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
