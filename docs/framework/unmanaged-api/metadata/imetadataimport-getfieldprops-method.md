---
title: IMetaDataImport::GetFieldProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 574ac706a07e7fcd701ab04f923d5171bea6f64a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782380"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps – metoda
Získá metadata spojená s polem odkazuje zadaný FieldDef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 [in] FieldDef token, který představuje získat související metadata pro pole.  
  
 `pClass`  
 [out] Ukazatel na token TypeDef, který představuje typ třídy, která patří pole.  
  
 `szField`  
 [out] Název pole.  
  
 `cchField`  
 [in] Velikost vyrovnávací paměti pro široké znaky *szField*.  
  
 `pchField`  
 [out] Skutečná velikost vyrovnávací paměti pro vrácený.  
  
 `pdwAttr`  
 [out] Příznaky spojené se pole metadat.  
  
 `ppvSigBlob`  
 [in] Ukazatel na hodnotu binární metadata popisující pole.  
  
 `pcbSigBlob`  
 [out] Velikost v bajtech `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak, který určuje typ hodnoty pole.  
  
 `ppValue`  
 [out] Konstantní hodnota pro pole.  
  
 `pcchValue`  
 [out] Velikost znaků z `ppValue`, nebo nula, pokud neexistuje žádný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
