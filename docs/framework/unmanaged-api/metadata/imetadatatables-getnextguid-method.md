---
title: IMetaDataTables::GetNextGuid – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 345c43b5a6e3c185b5e8070e9d6e1c1443673149
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781457"
---
# <a name="imetadatatablesgetnextguid-method"></a>IMetaDataTables::GetNextGuid – metoda
Získá index další hodnota identifikátoru GUID v aktuálním sloupci tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixGuid`  
 [in] Hodnota indexu ze sloupce tabulky identifikátor GUID.  
  
 `pNext`  
 [out] Ukazatel na index další hodnota identifikátoru GUID.  
  
## <a name="remarks"></a>Poznámky  
 Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky. Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Definice metadat a sémantika". Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
