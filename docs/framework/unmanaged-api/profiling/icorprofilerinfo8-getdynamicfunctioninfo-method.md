---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 45a40d49cea2dd5f881fbd47cc2fb4bd96e8f9ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243986"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo – metoda

Načte informace o dynamických metodách.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a>Parametry

`functionId` \
pro ID funkce, pro kterou mají být načteny informace

`moduleId` \
pro Ukazatel na modul, ve kterém je definována nadřazená třída funkce.

`ppvSig` \
mimo Ukazatel na signaturu funkce.

`pbSig` \
mimo Ukazatel na počet bajtů pro podpis funkce.

`cchName` \
pro Maximální velikost `wszName` pole.

`pcchName` \
mimo Počet znaků v `wszName` poli.

`wszName` \
mimo Pole `WCHAR` , které je názvem funkce, pokud existuje.

## <a name="remarks"></a>Poznámky

Některé metody, jako jsou zástupné procedury IL nebo LCG, nemají přidružená metadata, která lze načíst pomocí rozhraní API [IMetaDataImport](../metadata/imetadataimport-interface.md) a [IMetaDataImport2](../metadata/imetadataimport2-interface.md) . Tyto metody mohou být v profilerech zjištěny prostřednictvím ukazatelů instrukcí nebo naslouchat [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

Toto rozhraní API je možné použít k načtení informací o dynamických metodách, včetně popisného názvu, pokud je k dispozici.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlaviček** CorProf.idl, CorProf.h

**Knihovna** CorGuids.lib

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
