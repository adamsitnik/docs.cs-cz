---
title: IMetaDataEmit::SetEventProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 271ecd7e757340becccb7bf52362487a2b277299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737191"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps – metoda
Nastaví nebo aktualizuje zadanou funkci události definované v předchozím volání [imetadataemit::defineevent –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ev`  
 [in] Token, který událost.  
  
 `dwEventFlags`  
 [in] Příznaky událostí. To je bitová maska z `CorEventAttr` hodnoty.  
  
 `tkEventType`  
 [in] Token pro třídy události. Je to `mdTypeDef` nebo `mdTypeRef` token.  
  
 `mdAddOn`  
 [in] Metoda použitá k přihlášení k odběru událostí, nebo hodnotu null.  
  
 `mdRemoveOn`  
 [in] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.  
  
 `mdFire`  
 [in] Metoda použitá pro vyvolání události (prostřednictvím odvozené třídy).  
  
 `rmdOtherMethods[]`  
 [in] Pole tokenů pro jiné metody přidružené k události. Poslední element pole musí být `mdMethodDefNil`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
