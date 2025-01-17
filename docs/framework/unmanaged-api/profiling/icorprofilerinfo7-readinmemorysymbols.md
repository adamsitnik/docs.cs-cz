---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: ae51490be96f3eb6524831c93739c3befbc30b37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132028"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Načte bajty z datového proudu symbolů v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro Identifikátor modulu, který obsahuje datový proud v paměti.  
  
 `symbolsReadOffset`  
 pro Posun v rámci proudu v paměti, ve kterém se mají začít číst bajty.  
  
 `pSymbolBytes`  
 mimo Ukazatel na vyrovnávací paměť, do které budou kopírována data. Vyrovnávací paměť by měla mít `countSymbolBytes` dostupného místa.  
  
 `countSymbolBytes`  
 pro Počet bajtů, které mají být zkopírovány.  
  
 `pCountSymbolBytesRead`  
 mimo Když metoda vrátí, obsahuje skutečný počet přečtených bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud byl přečten nenulový počet bajtů.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, pokud byl modul vytvořen pomocí <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ReadInMemorySymbols` se pokusí přečíst `countSymbolBytes` dat počínaje posunem `symbolsReadOffset` v datovém proudu v paměti. Data se zkopírují do `pSymbolBytes`, u kterých se očekává `countSymbolBytes` dostupného místa.     `pCountSymbolsBytesRead` obsahuje skutečný počet přečtených bajtů, který může být menší než `countSymbolBytes`, pokud je dosaženo konce datového proudu.  
  
> [!NOTE]
> Aktuální implementace nepodporuje reflexe. Emit. Pokud byl modul vytvořen pomocí reflexe. Emit, metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
