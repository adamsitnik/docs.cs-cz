---
title: StrongNameSignatureVerificationEx2 – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aab3b697a0bb2f58258816ce4f8133009b26f54a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220588"
---
# <a name="strongnamesignatureverificationex2-method"></a>StrongNameSignatureVerificationEx2 – metoda
Ověří podpis sestavení se silným názvem a poskytuje mapování z klíče ECMA skutečné klíče.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Cesta k přenositelný spustitelný soubor (.exe nebo .dll) soubor pro sestavení, který se má ověřit.  
  
 `fForceVerification`  
 [in] `true` provádět ověřování, i když je potřeba přepsat nastavení registru; v opačném případě `false`.  
  
 `pbEcmaPublicKey`  
 [in] Ukazatel na mapování z veřejného klíče ECMA skutečné klíče používané pro ověřování.  
  
 `cbEcmaPublicKey`  
 [in] Délka skutečné ECMA veřejný klíč.  
  
 `pfWasVerified`  
 [out] `true` Pokud byl podpis silného názvu ověřené; v opačném případě `false`. Tento parametr je také nastavena na `false` Pokud bude ověření úspěšné z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud bude ověření úspěšné; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureVerification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
