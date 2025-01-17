---
title: IMetaDataImport::EnumUserStrings – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea144784f82c192f41f68394eb2ccdf443db54c2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782557"
---
# <a name="imetadataimportenumuserstrings-method"></a>IMetaDataImport::EnumUserStrings – metoda
Vytvoří výčet řetězec tokeny představující pevně zakódované řetězce v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor. První volání této metody musí mít hodnotu NULL.  
  
 `rStrings`  
 [out] Pole pro ukládání tokenů řetězec.  
  
 `cMax`  
 [in] Maximální velikost `rStrings` pole.  
  
 `pcStrings`  
 [out] Počet tokenů řetězec vrácený v `rStrings`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumUserStrings` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny se vytvořit výčet. V takovém případě `pcStrings` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Řetězec tokeny jsou vytvářeny [imetadataemit::defineuserstring –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody. Tato metoda je určena pro použití podle Prohlížeč metadat, nikoli podle kompilátoru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
