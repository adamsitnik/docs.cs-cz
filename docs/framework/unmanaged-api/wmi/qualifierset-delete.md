---
title: QualifierSet_Delete – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_Delete odstraní kvalifikátor podle názvu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e7bedcb5c56f9976f8dfd2619081971075d0d809
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127299"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete – funkce
Odstraní zadaný kvalifikátor podle názvu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`   
pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`   
pro Název kvalifikátoru, který se má odstranit

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr `wszName` není platný. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Odstranění tohoto kvalifikátoru je neplatné. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný kvalifikátor nebyl nalezen. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Místní přepsání bylo odstraněno a původní kvalifikátor z nadřazeného objektu má obnovený rozsah. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet::D dstranit](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .

Z důvodu pravidel šíření kvalifikátoru mohl být určitý kvalifikátor zděděný z jiného objektu a pouze přepsán v aktuální třídě nebo instanci. V tomto případě metoda `QualifierSet_Delete` resetuje kvalifikátor na původní zděděnou hodnotu. Funkce v tomto případě vrátí stavový kód `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
