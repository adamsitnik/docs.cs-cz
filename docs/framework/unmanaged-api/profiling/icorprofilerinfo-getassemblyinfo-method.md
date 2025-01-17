---
title: ICorProfilerInfo::GetAssemblyInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b410ef46e96f75d98ee750c760b19d2a77eec2b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780216"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo – metoda
Přijímá ID sestavení a vrátí název sestavení a ID jeho manifestu modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Identifikátor sestavení.  
  
 `cchName`  
 [in] Délka ve znacích, z `szName`.  
  
 `pcchName`  
 [out] Ukazatel na celkový počet znaků názvu sestavení.  
  
 `szName`  
 [out] Pokud volající širokého znaku vyrovnávací paměti. Po návratu funkce bude obsahovat název sestavení.  
  
 `pAppDomainId`  
 [out] Ukazatel na ID domény aplikace, který obsahuje sestavení.  
  
 `pModuleId`  
 [out] Ukazatel na ID modul manifestu sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Po návratu tato metoda je nutné ověřit, `szName` vyrovnávací paměť je dostatečně velký, aby obsahoval úplný název sestavení. K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetAssemblyInfo` znovu.  
  
 Alternativně můžete nejprve volat `GetAssemblyInfo` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť. Potom můžete upravit velikost vyrovnávací paměti na základě hodnoty vráceny v `pcchName` a volat `GetAssemblyInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
