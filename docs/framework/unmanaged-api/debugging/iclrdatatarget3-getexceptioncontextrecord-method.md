---
title: ICLRDataTarget3::GetExceptionContextRecord – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b43ab8cdeff3866bb51e8634f367cf86ee483d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089223"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord – metoda
Je voláno common language runtime (CLR) data access services k získání záznamu o kontextu souvisejícím s cílovým procesem. Například pro cíl s výpisem paměti, jde ekvivalentní k záznamu o kontextu předané prostřednictvím `ExceptionParam` argument [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) funkce ve Windows ladit knihovnu nápovědy (DbgHelp).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bufferSize`  
 [in] Velikost vstupní vyrovnávací paměti v bajtech. Toto musí být dostatečně velký, aby kontextového záznamu.  
  
 `bufferUsed`  
 [out] Ukazatel `ULONG32` typ, který přijímá počet bajtů ve skutečnosti zapsat do vyrovnávací paměti.  
  
 `buffer`  
 [out] Ukazatel do vyrovnávací paměti, která obdrží kopii kontextového záznamu. Záznam o výjimce se vrátí jako [kontextu](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) typu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kódu při selhání. `HRESULT` Kódy mohou zahrnovat, avšak nejsou omezeny na následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Kontextového záznamu byla zkopírována do výstupní vyrovnávací paměť.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Žádný záznam kontextu je přidružený k cíli.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Velikost vstupní vyrovnávací paměť není dostatečně velký, aby odpovídala kontextového záznamu.|  
  
## <a name="remarks"></a>Poznámky  
 [KONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) je specifické pro platformu struktuře definované v hlavičkách sada Windows SDK.  
  
 Tato metoda je implementováno tvůrci ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [GetExceptionRecord – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
