---
title: Funkce GetPropertyHandle (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetPropertyHandle vrátí popisovač jedinečných identit, že bude vlastnost.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 902414ca96d9b4bf888608bd9ad267777da92e32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742312"
---
# <a name="getpropertyhandle-function"></a>Funkce GetPropertyHandle
Vrátí jedinečný popisovač identifikující vlastnosti.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.

`wszPropertyName`  
[in] Řetězec zakončený hodnotou null kódování UTF16 characaters, který obsahuje název vlastnosti.   

`pType`  
[out] Ukazatel [ `CIMTYPE` ](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) člen výčtu, který představuje typ CIM vlastnosti.

`pHandle`   
[out] Ukazatel na celé číslo, které obsahuje popisovač vlastnosti.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný název vlastnosti nebyla nalezena. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | Požadovaná vlastnost je typu jsou `CIM_OBJECT` nebo `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) metody.

Pomocí tohoto úchytu můžete identifikovat vlastnosti při použití [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) metody pro čtení nebo zápis hodnot vlastností.

Obslužné rutiny mohou být získána pro vlastnosti všech datových typů jiných než `CIM_OBJECT` a `CIM_ARRAY`. Vrátí popisovače práce napříč všemi instancemi třídy.

## <a name="requirements"></a>Požadavky  
**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:
- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
