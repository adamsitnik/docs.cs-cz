---
title: ICorProfilerInfo2::GetRVAStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc7b6d1a27faf7bde46305f9c98d98351e6261b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782263"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a>ICorProfilerInfo2::GetRVAStaticAddress – metoda
Získá adresu statické pole zadanou relativní virtuální adresu (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] ID třídy, která obsahuje požadovaná pole statickou adresu RVA.  
  
 `fieldToken`  
 [in] Token metadat pro požadované pole statickou adresu RVA.  
  
 `ppAddress`  
 [out] Ukazatel na adresu RVA statické pole.  
  
## <a name="remarks"></a>Poznámky  
 `GetRVAStaticAddress` Metoda může vrátit jednu z následujících akcí:  
  
- CORPROF_E_DATAINCOMPLETE HRESULT, pokud daný statické pole nebyla přiřazena adresa v zadaném kontextu.  
  
- Adresy objektů, které mohou být v haldě uvolňování paměti. Tyto adresy mohou stát neplatnými po uvolnění paměti, takže po uvolnění paměti, profilovací programy by neměl se předpokládá, že jsou platné.  
  
 Před dokončením konstruktoru třídy třídy `GetRVAStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechny jeho statická pole, i když některé z statická pole může být již inicializován a může být kořenová objekty uvolnění paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
