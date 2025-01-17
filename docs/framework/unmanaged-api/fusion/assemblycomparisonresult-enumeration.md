---
title: AssemblyComparisonResult – výčet
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: 3d3fd88a2c1ac90f823b23d8d2bcb5b177a625c3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109015"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult – výčet
Označuje ekvivalent dvou identit sestavení, jak je určeno funkcí [CompareAssemblyIdentity –](compareassemblyidentity-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Označuje, že všechna pole sestavení v porovnání se shodují.|  
|`ACR_EquivalentFXUnified`|Označuje, že sestavení jsou považována za ekvivalentní na základě verze modulu CLR (Common Language Runtime) z sjednocení čísel verzí sestavení v .NET Framework verze 2,0.|  
|`ACR_EquivalentPartialFXUnified`|Označuje částečnou shodu sestavení založenou na sjednocení CLR čísel verzí sestavení v .NET Framework 2,0.|  
|`ACR_EquivalentPartialMatch`|Označuje částečnou shodu sestavení.|  
|`ACR_EquivalentPartialUnified`|Označuje částečnou shodu sestavení na základě zastaralého sjednocení čísel verzí.|  
|`ACR_EquivalentPartialWeakNamed`|Označuje částečnou shodu jednoduše pojmenovaných sestavení.|  
|`ACR_EquivalentUnified`|Označuje, že sestavení jsou považována za ekvivalentní na základě sjednocení čísel verzí ve starších verzích .NET Framework v rámci CLR.|  
|`ACR_EquivalentWeakNamed`|Označuje shodu mezi dvěma jednoduše pojmenovanými sestaveními, jejichž čísla verzí byla ignorována.|  
|`ACR_NonEquivalent`|Označuje, že mezi dvěma sestaveními nedošlo k žádné shodě.|  
|`ACR_NonEquivalentPartialVersion`|Označuje, že se dvě sestavení shodují s výjimkou jejich čísel verzí, která se shodují pouze částečně.|  
|`ACR_NonEquivalentVersion`|Označuje, že se dvě sestavení shodují s výjimkou jejich čísel verzí, která se neshodují.|  
|`ACR_Unknown`|Označuje, že důvod nerovnocennosti není znám.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CompareAssemblyIdentity – funkce](compareassemblyidentity-function.md)
- [Výčty pro fúze](fusion-enumerations.md)
