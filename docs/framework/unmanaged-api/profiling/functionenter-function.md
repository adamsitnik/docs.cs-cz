---
title: FunctionEnter – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 354736890a4b042a8da5e747a0ab6ea3777e398e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952907"
---
# <a name="functionenter-function"></a>FunctionEnter – funkce
Upozorňuje profileru, že řízení je předáno funkci.  
  
> [!NOTE]
> `FunctionEnter` Funkce je zastaralá ve verzi .NET Framework 2,0 a její použití bude mít za následek snížení výkonu. Místo toho použijte funkci [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcID`  
 pro Identifikátor funkce, do které je ovládací prvek předán.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionEnter` Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec`atribut třídy úložiště`naked`().  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionEnter` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud `FunctionEnter` se nevrátí.  
  
 `FunctionEnter` Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
