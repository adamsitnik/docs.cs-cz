---
title: PublicKeyBlob – struktura
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 245d9dc6147f4140e823b79c3816b9bc567ad712
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732684"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob – struktura
Představuje veřejného klíče dvojice veřejného/soukromého klíče v binárním formátu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`SigAlgId`|Identifikátor pro algoritmus podpisu (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.|  
|`HashAlgId`|Identifikátor algoritmu hash (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.|  
|`cbPublicKey`|Délka klíče v bajtech.|  
|`PublicKey`|Proměnné délky bajtové pole obsahující hodnotu klíče ve formátu vrácený rozhraní CryptoAPI.|  
  
## <a name="remarks"></a>Poznámky  
 `PublicKeyBlob` Struktura používá [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)a další funkce silným názvem k reprezentaci veřejného klíče dvojice veřejného/soukromého klíče.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [StrongNameGetPublicKey – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
- [Struktury pro silné názvy](https://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
