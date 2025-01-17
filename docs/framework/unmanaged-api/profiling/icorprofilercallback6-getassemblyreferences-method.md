---
title: ICorProfilerCallback6::GetAssemblyReferences – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: d15f1b568c50cf4fca28966f94a6a4becf59e734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141636"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Upozorní profileru, že sestavení je ve fázi brzkého nasazování, pokud modul CLR provádí procházení zavřením odkazu na sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssemblyPath`  
 pro Cesta a název sestavení, jehož metadata budou změněna.  
  
 `pAsmRefProvider`  
 pro Ukazatel na adresu rozhraní [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) , které určuje odkazy na sestavení, které se mají přidat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty z tohoto zpětného volání jsou ignorovány.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání je řízeno nastavením příznaku masky události [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) při volání metody [Icorprofilercallback5 –:: SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) . Pokud profiler registruje pro metodu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , modul runtime předá cestu a název sestavení, které se má načíst, spolu s ukazatelem na [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objekt rozhraní k této metodě. Profiler pak může zavolat metodu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) s objektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` pro každé cílové sestavení, které plánuje odkazovat ze sestavení zadaného ve `GetAssemblyReferences` zpětného volání.  
  
 Použití zpětného volání `GetAssemblyReferences` pouze v případě, že Profiler musí upravit metadata sestavení pro přidání odkazů na sestavení. (Ale Všimněte si, že skutečná úprava metadat sestavení se provádí v metodě zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).) Profiler by měl implementovat metodu `GetAssemblyReferences` zpětného volání pro informování společného jazykového modulu runtime (CLR), který se přidá k odkazům na sestavení při načtení modulu.  To pomáhá zajistit, že rozhodnutí o sdílení sestavení, která provedla CLR v rámci této úvodní fáze, zůstávají platná, i když Profiler plánuje změnit odkazy na sestavení metadat později.  To se může vyhnout některým instancím, ve kterých změny metadat profileru způsobují chybu `SECURITY_E_INCOMPATIBLE_SHARE`.  
  
 Profiler používá objekt [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) poskytnutý touto metodou pro přidání odkazů na sestavení do prohlížeč ukončení odkazu sestavení CLR.  Objekt [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) by měl být použit pouze v rámci tohoto zpětného volání. Volání metody [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z tohoto zpětného volání nemají za následek změněná metadata, ale pouze v rámci upraveného procházení odkazu na sestavení. Profiler bude stále muset použít objekt [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) k explicitnímu přidání odkazů na sestavení z zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) pro referenční sestavení, i když implementuje @no__t_2 onCuePoint.  
  
 Profiler by měl být přizpůsobený tak, aby přijímal duplicitní volání tohoto zpětného volání pro stejné sestavení a měl by reagovat identicky pro každé takové duplicitní volání (provedením stejné sady [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) volání).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
