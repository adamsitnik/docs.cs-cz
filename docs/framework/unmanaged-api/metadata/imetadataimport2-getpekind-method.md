---
title: IMetaDataImport2::GetPEKind – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91c80566ed284403ad559583a1e4f1025eb09985
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755314"
---
# <a name="imetadataimport2getpekind-method"></a>IMetaDataImport2::GetPEKind – metoda
Získá hodnotu určující druh kódu do přenosného spustitelného (PE) soubor, obvykle knihovny DLL nebo EXE souboru, která je definována v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwPEKind`  
 [out] Ukazatel na hodnotu [corpekind –](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) výčet, který popisuje soubor PE.  
  
 `pdwMachine`  
 [out] Ukazatel na hodnotu, která identifikuje architektura počítače. Naleznete v části Další možné hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota odkazuje `pdwMachine` parametr může být jedna z následujících akcí.  
  
|Hodnota|Architektura počítače|  
|-----------|--------------------------|  
|IMAGE_FILE_MACHINE_I386<br /><br /> 0x014C|x86|  
|IMAGE_FILE_MACHINE_IA64<br /><br /> 0x0200|Intel IPF|  
|IMAGE_FILE_MACHINE_AMD64<br /><br /> 0x8664|x64|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [CorPEKind – výčet](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
