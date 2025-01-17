---
title: IMetaDataImport::GetCustomAttributeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c714915651d8660a739d8ee6518fc3814af4c08d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782412"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps – metoda
Získá hodnotu vlastní atribut zadaný svůj token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cv`  
 [in] Token metadat, který představuje vlastní atribut, který se má načíst.  
  
 `ptkObj`  
 [out, volitelné] Token metadat představující objekt, který upravuje vlastního atributu. Tato hodnota může být libovolný typ tokenu metadat s výjimkou `mdCustomAttribute`.  
  
 `ptkType`  
 [out, volitelné] `mdMethodDef` Nebo `mdMemberRef` představující token metadat <xref:System.Type> vrácené vlastního atributu.  
  
 `ppBlob`  
 [out, volitelné] Ukazatel na pole dat, která je hodnota vlastního atributu.  
  
 `pcbSize`  
 [out, volitelné] Velikost v bajtech dat vrácených v *`ppBlob`.  
  
## <a name="remarks"></a>Poznámky  
 Vlastní atribut je uložena jako pole dat, formát, který je srozumitelné pro modul metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
