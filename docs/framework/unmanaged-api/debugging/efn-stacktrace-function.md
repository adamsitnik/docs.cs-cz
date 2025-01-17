---
title: _EFN_StackTrace – funkce
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
ms.openlocfilehash: 272856c7eedbdc577158edcc463535a7946bb060
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122993"
---
# <a name="_efn_stacktrace-function"></a>\_EFN\_funkce trasování zásobníku
Poskytuje textovou reprezentaci spravovaného trasování zásobníku a pole `CONTEXT` záznamů, jednu pro každý přechod mezi nespravovaným a spravovaným kódem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Client`  
 pro Probíhá ladění klienta.  
  
 `wszTextOut`  
 mimo Textová reprezentace trasování zásobníku.  
  
 `puiTextLength`  
 mimo Ukazatel na počet znaků v `wszTextOut`.  
  
 `pTransitionContexts`  
 mimo Pole kontextů přechodu.  
  
 `puiTransitionContextCount`  
 mimo Ukazatel na počet kontextů přechodu v poli.  
  
 `uiSizeOfContext`  
 pro Velikost struktury kontextu.  
  
 `Flags`  
 pro Nastavte na hodnotu 0 nebo SOS_STACKTRACE_SHOWADDRESSES (0x01), abyste zobrazili registr EBP a zadáte ukazatel zásobníku (ESP) před každým `module!functionname` řádkem.  
  
## <a name="remarks"></a>Poznámky  
 Strukturu `_EFN_StackTrace` lze volat z programového programu WinDbg. Parametry se používají takto:  
  
- Pokud je `wszTextOut` null a `puiTextLength` není null, funkce vrátí délku řetězce v `puiTextLength`.  
  
- Pokud `wszTextOut` není null, funkce ukládá text v `wszTextOut` až do umístění označeného `puiTextLength`. Pokud byla ve vyrovnávací paměti dostatek místa, vrátí se úspěšně, nebo pokud vyrovnávací paměť není dost velká, vrátí E_OUTOFMEMORY.  
  
- Přechodová část funkce je ignorována, pokud `pTransitionContexts` a `puiTransitionContextCount` jsou obě hodnoty null. V tomto případě funkce poskytuje volajícím textový výstup pouze názvů funkcí.  
  
- Pokud je `pTransitionContexts` null a `puiTransitionContextCount` není null, funkce vrátí potřebný počet kontextových položek v `puiTransitionContextCount`.  
  
- Pokud `pTransitionContexts` není null, funkce ji zpracuje jako pole struktury délky `puiTransitionContextCount`. Velikost struktury je dána `uiSizeOfContext`a musí se jednat o velikost [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) nebo `CONTEXT` architektury.  
  
- `wszTextOut` je zapsán v následujícím formátu:  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Pokud je posun v šestnáctkové soustavě 0x0, není zapsán žádný posun.  
  
- Pokud není ve vlákně aktuálně v kontextu žádný spravovaný kód, funkce vrátí SOS_E_NOMANAGEDCODE.  
  
- Parametr `Flags` je buď 0, nebo SOS_STACKTRACE_SHOWADDRESSES, aby se zobrazily EBP a ESP před každým řádkem `module!functionname`. Ve výchozím nastavení má hodnotu 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** SOS_Stacktrace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
