---
title: CorPEKind – výčet
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bfe30567bcd8e22a82d401e00b0a6ee50407def
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781675"
---
# <a name="corpekind-enumeration"></a>CorPEKind – výčet
Obsahuje hodnoty, které popisují soubor (PE portable executable) vrácená z volání [imetadataimport2::getpekind –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`peNot`|Označuje, že to není přenositelný Spustitelný soubor.|  
|`peILOnly`|Označuje, že tento soubor PE obsahuje pouze pro spravovaný kód.|  
|`pe32BitRequired`|Označuje, že tento soubor PE provede volání Win32.|  
|`pe32Plus`|Označuje, že tento soubor PE poběží na 64bitové platformě.|  
|`pe32Unmanaged`|Označuje, že je tento soubor PE nativního kódu.|  
|pe32BitPreferred|Označuje, že tento soubor PE je nezávislá na platformě a dává přednost mají být načteny v 32bitovém prostředí.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty je možné v bitové kombinace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
