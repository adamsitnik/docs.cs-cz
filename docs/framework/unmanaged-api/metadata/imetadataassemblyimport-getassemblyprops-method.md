---
title: IMetaDataAssemblyImport::GetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec04588bd1cc21e585d89c734c152a86fb835b15
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772729"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps – metoda
Získá sadu vlastností pro sestavení s podpisem Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mda`  
 [in]. `mdAssembly` Token metadat, který představuje sestavení, pro které chcete-li získat vlastnosti.  
  
 `ppbPublicKey`  
 [out] Ukazatel na veřejný klíč nebo token metadat.  
  
 `pcbPublicKey`  
 [out] Počet bajtů vrácených veřejného klíče.  
  
 `pulHashAlgId`  
 [out] Ukazatel na algoritmus použitý k vytvoření hodnoty hash souborů v sestavení.  
  
 `szName`  
 [out] Jednoduchý název sestavení.  
  
 `cchName`  
 [in] Velikost v široké znaky z `szName`.  
  
 `pchName`  
 [out] Počet skutečně vrácených v široké znaky `szName`.  
  
 `pMetaData`  
 [out] Ukazatel na assemblymetadata – struktura, která obsahuje metadata sestavení.  
  
 `pdwAssemblyFlags`  
 [out] Příznaky, které popisují metadata použité u sestavení. Tato hodnota je kombinace jedné nebo více [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
