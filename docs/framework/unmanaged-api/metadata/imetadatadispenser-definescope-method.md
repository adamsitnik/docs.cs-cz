---
title: IMetaDataDispenser::DefineScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1763f9341af2d90cf465cb554bf7f282a4d92058
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777811"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope – metoda
Vytvoří nové oblasti v paměti, ve kterém můžete vytvořit nová metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rclsid`  
 [in] Identifikátor CLSID verzi struktury metadat, který má být vytvořen Tato hodnota musí být CLSID_CorMetaDataRuntime pro rozhraní .NET Framework verze 2.0.  
  
 `dwCreateFlags`  
 [in] Příznaky, které určují možnosti. Tato hodnota musí být nula pro rozhraní .NET Framework 2.0.  
  
 `riid`  
 [in] Identifikátor IID rozhraní požadované metadat má být vrácen. volající pomocí rozhraní vytvořit nová metadata.  
  
 Hodnota `riid` musíte zadat jedno z rozhraní "generování". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit nebo IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 [out] Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 `DefineScope` Vytvoří sadu tabulek metadat v paměti, generuje jedinečný identifikátor GUID (identifikátor verze modulu nebo identifikátor MVID) pro metadata a vytvoří záznam v tabulce modulu pro jednotku kompilace probíhá emitovány.  
  
 Atributy můžete připojit k oboru metadat jako celek s použitím [imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) nebo [imetadataemit::definecustomattribute –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) metoda podle potřeby.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
