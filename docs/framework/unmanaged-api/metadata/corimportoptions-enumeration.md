---
title: CorImportOptions – výčet
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38c0937804eb82d1c96a605b55a00784ba58fe13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781830"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions – výčet
Obsahuje příznak hodnoty, které řídí chování během import sestavení mimo aktuální rozsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDImportOptionDefault`|Určuje výchozí chování, které se mají přeskočit odstraněné záznamy.|  
|`MDImportOptionAll`|Označuje, že všechna metadata ve výčtu.|  
|`MDImportOptionAllTypeDefs`|Označuje, že všechny definice TypeDef, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllMethodDefs`|Označuje, že všechny MethodDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllFieldDefs`|Označuje, že všechny FieldDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllProperties`|Označuje, že všechny PropertyDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllEvents`|Označuje, že všechny EventDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllCustomAttributes`|Označuje, že všechny vlastní atributy, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllExportedTypes`|Označuje, že všechny exportované typy, včetně odstraněné ty, které jsou ve výčtu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
