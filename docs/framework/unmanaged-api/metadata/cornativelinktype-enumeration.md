---
title: CorNativeLinkType – výčet
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 944c641c39ddef7add0e9f382dc7d35068668455
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781718"
---
# <a name="cornativelinktype-enumeration"></a>CorNativeLinkType – výčet
Obsahuje hodnoty, které označují typ propojené v nativním kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`nltNone`|Označuje, že jsou zadána žádná klíčová slova.|  
|`nltAnsi`|Určuje, zda je zadán ANSI – klíčové slovo.|  
|`nltUnicode`|Určuje, zda je zadán Unicode – klíčové slovo|  
|`nltAuto`|Určuje, zda je zadán klíčovým slovem auto.|  
|`nltOle`|Označuje, zda je zadán klíčovým slovem OLE.|  
|`nltMaxValue`|Nepoužívá se.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
