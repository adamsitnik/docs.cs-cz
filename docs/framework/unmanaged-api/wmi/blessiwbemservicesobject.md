---
title: Funkce BlessIWbemServicesObject (referenční dokumentace nespravovaného rozhraní API)
description: Funkce BlessIWbemServicesObject označuje, jestli přihlašovací údaje uživatele povolit přístup k objektu služby IWbem
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1eb6b870beabb71e340b0ec39c489cedb02128cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366631"
---
# <a name="blessiwbemservicesobject-function"></a>Funkce BlessIWbemServicesObject
Určuje, zda pověření uživatelů odkudkoli přístup k zadané [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objektu. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>Parametry

`pIWbemServices`\
[in] Ukazatel na objekt služby WMI.

`strUser`\
[in] Uživatelské jméno.

`strPassword`\
[in] Heslo přidružené k `strUser`.

`strAuthority`\
[in] Název domény uživatele. Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`impLevel`\
[in] Úroveň zosobnění.

`authnLevel`\
[in] Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WinError.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden nebo více argumentů nejsou platné. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` je `null`. | 
| `E_FAIL` | 0x80000008 | Došlo k nespecifikované chybě. |
| `E_OUTOFMEMORY` | 0x80000002 | K provedení této operace není dostatek paměti. | 
| `S_OK` | 0 | Volání funkce byla úspěšná. | 

## <a name="requirements"></a>Požadavky

 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Záhlaví:** WMINet_Utils.idl

 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)