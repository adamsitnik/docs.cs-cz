---
title: ICorProfilerInfo::GetCodeInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cc587edf763a352501a0d9097bdab2c54658d98
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762840"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo – metoda
Vrátí rozsah nativního kódu přidružené k ID zadanou funkci.  
  
 Tato metoda je zastaralá. Použití [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, ke kterému je přidružen nativní kód.  
  
 `pStart`  
 [out] Ukazatel na pole bajtů, které tvoří nativního kódu funkce.  
  
 `pcSize`  
 [out] Ukazatel na celé číslo, které určuje velikost v bajtech nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Za účelem optimalizace výkonu modulu runtime v rozhraní .NET Framework verze 2.0 rozdělí předkompilované nativního kódu funkce do několika oblastí. V důsledku toho `GetCodeInfo` metoda je zastaralé v rozhraní .NET Framework 2.0, protože není schopen zpracovat rozsah nativního kódu funkce. Profilovací programy by měl přepnout na použití obecnější `ICorProfilerInfo2::GetCodeInfo2` metoda místo.  
  
 Tato funkce využívá volající – přidělené vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
