---
title: CorDebugInterfaceVersion – výčet
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df57cd5a2121c216fc23b9c608de091b002147e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101761"
---
# <a name="cordebuginterfaceversion-enumeration"></a>CorDebugInterfaceVersion – výčet
Určuje rozhraní, verze rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve kterém byl zaveden rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo   
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot   
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a>Členové  
 Následující tabulka obsahuje odkazy od všech hodnot výčtu na odpovídající rozhraní. Kromě toho v tabulce označuje první verze, který rozhraní je podporován v rozhraní .NET Framework.  
  
|Člen|Určuje|Verze rozhraní .NET Framework|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|Verze rozhraní .NET Framework je neplatná.|-|  
|`CorDebugVersion_1_0`|Verze rozhraní .NET Framework, včetně všech jeho aktualizace service Pack, je 1.0.|1.0|  
|`CorDebugVersion_1_1`|Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 1.1.|1.1|  
|`CorDebugVersion_2_0`|Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 2.0.|2.0|  
|`CorDebugVersion_4_0`|Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 4.|4|  
|`CorDebugVersion_4_5`|Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 4.5.|4.5|  
|`ver_ICorDebugManagedCallback`|[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebugUnmanagedCallback`|[ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebug`|[Icordebug –](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|1.0|  
|`ver_ICorDebugController`|[Icordebugcontroller –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|1.0|  
|`ver_ICorDebugAppDomain`|[ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|1.0|  
|`ver_ICorDebugAssembly`|[Icordebugassembly –](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|1.0|  
|`ver_ICorDebugProcess`|[ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|1.0|  
|`ver_ICorDebugBreakpoint`|[Icordebugbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugFunctionBreakpoint`|[ICorDebugFunctionBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugModuleBreakpoint`|[ICorDebugModuleBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugValueBreakpoint`|[ICorDebugValueBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugStepper`|[ICorDebugStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|1.0|  
|`ver_ICorDebugRegisterSet`|[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|1.0|  
|`ver_ICorDebugThread`|[ICorDebugThread](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|1.0|  
|`ver_ICorDebugChain`|[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|1.0|  
|`ver_ICorDebugFrame`|[Icordebugframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|1.0|  
|`ver_ICorDebugILFrame`|[ICorDebugILFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|1.0|  
|`ver_ICorDebugNativeFrame`|[ICorDebugNativeFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|1.0|  
|`ver_ICorDebugModule`|[Icordebugmodule –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|1.0|  
|`ver_ICorDebugFunction`|[ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|1.0|  
|`ver_ICorDebugCode`|[Icordebugcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|1.0|  
|`ver_ICorDebugClass`|[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|1.0|  
|`ver_ICorDebugEval`|[Icordebugeval –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|1.0|  
|`ver_ICorDebugValue`|[ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|1.0|  
|`ver_ICorDebugGenericValue`|[ICorDebugGenericValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|1.0|  
|`ver_ICorDebugReferenceValue`|[Icordebugreferencevalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|1.0|  
|`ver_ICorDebugHeapValue`|[ICorDebugHeapValue](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|1.0|  
|`ver_ICorDebugObjectValue`|[Icordebugobjectvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|1.0|  
|`ver_ICorDebugBoxValue`|[Icordebugboxvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|1.0|  
|`ver_ICorDebugStringValue`|[ICorDebugStringValue](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|1.0|  
|`ver_ICorDebugArrayValue`|[ICorDebugArrayValue](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|1.0|  
|`ver_ICorDebugContext`|[ICorDebugContext](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|1.0|  
|`ver_ICorDebugEnum`|[Icordebugenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|1.0|  
|`ver_ICorDebugObjectEnum`|[Icordebugobjectenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|1.0|  
|`ver_ICorDebugBreakpointEnum`|[Icordebugbreakpointenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|1.0|  
|`ver_ICorDebugStepperEnum`|[Icordebugstepperenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|1.0|  
|`ver_ICorDebugProcessEnum`|[ICorDebugProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|1.0|  
|`ver_ICorDebugThreadEnum`|[ICorDebugThreadEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|1.0|  
|`ver_ICorDebugFrameEnum`|[Icordebugframeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|1.0|  
|`ver_ICorDebugChainEnum`|[ICorDebugChainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|1.0|  
|`ver_ICorDebugModuleEnum`|[ICorDebugModuleEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|1.0|  
|`ver_ICorDebugValueEnum`|[ICorDebugValueEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|1.0|  
|`ver_ICorDebugCodeEnum`|[Icordebugcodeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|1.0|  
|`ver_ICorDebugTypeEnum`|[Icordebugtypeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|1.0|  
|`ver_ICorDebugErrorInfoEnum`|[ICorDebugErrorInfoEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|1.0|  
|`ver_ICorDebugAppDomainEnum`|[ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|1.0|  
|`ver_ICorDebugAssemblyEnum`|[Icordebugassemblyenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[ICorDebugEditAndContinueErrorInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueSnapshot`|[ICorDebugEditAndContinueSnapshot](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|1.0|  
|`ver_ICorDebugManagedCallback2`|[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|2.0|  
|`ver_ICorDebugAppDomain2`|[ICorDebugAppDomain2](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|2.0|  
|`ver_ICorDebugProcess2`|[ICorDebugProcess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|2.0|  
|`ver_ICorDebugStepper2`|[ICorDebugStepper2](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|2.0|  
|`ver_ICorDebugRegisterSet2`|[ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|2.0|  
|`ver_ICorDebugThread2`|[ICorDebugThread2](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|2.0|  
|`ver_ICorDebugILFrame2`|[ICorDebugILFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|2.0|  
|`ver_ICorDebugModule2`|[ICorDebugModule2](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|2.0|  
|`ver_ICorDebugFunction2`|[ICorDebugFunction2](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|2.0|  
|`ver_ICorDebugCode2`|[ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|2.0|  
|`ver_ICorDebugClass2`|"ICorDebugClass2"|2.0|  
|`ver_ICorDebugValue2`|Icordebugvalue2 "–"|2.0|  
|`ver_ICorDebugEval2`|Icordebugeval2 "–".|2.0|  
|`ver_ICorDebugObjectValue2`|Icordebugobjectvalue2 "–"|2.0|  
|`ver_ICorDebugThread3`|[ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|4|  
|`ver_ICorDebugThread4`|[ICorDebugThread4](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|4|  
|`ver_ICorDebugStackWalk`|[Icordebugstackwalk –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|4|  
|`ver_ICorDebugNativeFrame2`|[ICorDebugNativeFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|4|  
|`ver_ICorDebugInternalFrame2`|[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|4|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[ICorDebugRuntimeUnwindableFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|4|  
|`ver_ICorDebugHeapValue3`|[ICorDebugHeapValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|4|  
|`ver_ICorDebugBlockingObjectEnum`|[ICorDebugBlockingObjectEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|4|  
|`ver_ICorDebugValue3`|[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|4|  
|`ver_ICorDebugComObjectValue`|[ICorDebugComObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|4.5|  
|`ver_ICorDebugAppDomain3`|[ICorDebugAppDomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|4.5|  
|`ver_ICorDebugCode3`|[ICorDebugCode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|4.5|  
|`ver_ICorDebugILFrame3`|[ICorDebugILFrame3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|4.5|  
|`CorDebugLatestVersion`|Verze rozhraní .NET Framework, včetně všech jeho aktualizace service Pack, je na nejnovější verzi.|-|  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program můžete použít `CorDebugInterfaceVersion` výčtu v [createdebugginginterfacefromversion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkce k zadání nejvyšší verze rozhraní .NET Framework, který ladicí program podporuje.  
  
## <a name="interface-names"></a>Názvy rozhraní  
 Číslo, které se zobrazí na konci názvů rozhraní v rozhraní API pro ladění (například "3" v `ICorDebugThread3`) určuje verzi rozhraní, nikoli na verzi rozhraní .NET Framework. Názvy všech rozhraní v rozhraní API pro ladění obsahují čísla verzí s výjimkou rozhraní, která byla zavedena v rozhraní .NET Framework verze 1. Jakékoli propojeni rozhraní verze číslice čísla verzí and.NET Framework je náhodný.  
  
-   Rozhraní, která byla zavedena v rozhraní .NET Framework verze 1.0 nezahrnují čísel, protože jsou implicitně všechny verze 1.  
  
-   Rozhraní .NET Framework verze 1.1 používá verzi 1.0 rozhraní a ne provádět žádné nové ladění rozhraní.  
  
-   14. ladění rozhraní zavedené v rozhraní .NET Framework verze 2.0 jsou logické rozšíření jejich verze 1 protějšky a obsahovat číslo "2" v názvu.  
  
-   Verze rozhraní .NET Framework 3.0 a 3.5 použít existující rozhraní .NET Framework 2.0 a ne provádět žádné nové rozhraní.  
  
-   [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Představuje kombinaci různých verzí rozhraní. Například obě `ICorDebugThread3` a `ICorDebugThread4` zobrazí jako třetí a čtvrtý verze `ICorDebugThread` rozhraní. [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Také představuje první verzi `ICorDebugStackWalk` rozhraní a druhou verzi `ICorDebugNativeFrame` rozhraní (`ICorDebugNativeFrame2`).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
