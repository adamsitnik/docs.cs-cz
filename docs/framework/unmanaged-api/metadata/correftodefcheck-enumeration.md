---
title: CorRefToDefCheck – výčet
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ae87dd4538a9a8e88591f498c0ce77b51bfa852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781624"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck – výčet
Určuje příznaky do ovládacího prvku odkazované položky, které jsou převedeny na jejich definice, aby bylo možné optimalizovat kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDRefToDefDefault`|Určuje typ odkazy a odkazy na členy mají být převedeny do definic. Toto je výchozí hodnota (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Určuje, zda všechny odkazované položky mají být převedeny na definice.|  
|`MDRefToDefNone`|Určuje, že žádné odkazované položky, které mají být převedeny na definice.|  
|`MDTypeRefToDef`|Určuje, že by měl pouze odkazy na typ převést na typ definice.|  
|`MDMemberRefToDef`|Určuje, že pouze odkazy na členy mají být převedeny na definice. To znamená odkazy na členy mají být převedeny na definice metod nebo definice pole.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
