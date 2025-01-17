---
title: IMetaDataImport::EnumTypeSpecs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81592b6da7fa7cdf275e9fa5b4b82ef0a15061c0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782571"
---
# <a name="imetadataimportenumtypespecs-method"></a>IMetaDataImport::EnumTypeSpecs – metoda
Vytvoří výčet token TypeSpec tokeny definované v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor. Tato hodnota musí mít hodnotu NULL pro první volání této metody.  
  
 `rTypeSpecs`  
 [out] Pole pro ukládání tokenů token TypeSpec.  
  
 `cMax`  
 [in] Maximální velikost `rTypeSpecs` pole.  
  
 `pcTypeSpecs`  
 [out] Počet tokenů token TypeSpec vrácené v `rTypeSpecs`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeSpecs` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny se vytvořit výčet. V takovém případě `pcTypeSpecs` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Token TypeSpec tokeny jsou vytvářeny [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
