---
title: COR_ARRAY_LAYOUT – struktura
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: f37bf545553045b9737b7057feed78e1f06ace4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099468"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT – struktura
Poskytuje informace o rozložení objektu pole v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`componentID`|Identifikátor typu objektů, které pole obsahuje.|  
|`componentType`|Hodnota výčtu CorElementType –, která určuje, zda je komponenta odkaz na uvolňování paměti, třídu hodnot nebo primitivní.|  
|`firstElementOffset`|Posun k prvnímu prvku v poli.|  
|`elementSize`|Velikost každého prvku.|  
|`countOffset`|Posun k počtu prvků v poli.|  
|`rankSize`|Velikost rozměru (v bajtech).|  
|`numRanks`|Počet pořadí v poli.|  
|`rankOffset`|Posun, ve kterém je začátek pořadí.|  
  
## <a name="remarks"></a>Poznámky  
 Pole `rankSize` určuje velikost rozměru v multidimenzionálním poli. Je přesně pro jednorozměrná pole.  
  
 Hodnota `numRanks` je 1 pro jednorozměrné pole a `N` v multidimenzionálním poli dimenzí `N`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
