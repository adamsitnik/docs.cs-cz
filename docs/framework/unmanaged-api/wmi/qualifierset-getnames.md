---
title: Funkce QualifierSet_GetNames (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_GetNames načte názvy kvalifikátory z objektu nebo vlastnosti.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da6321e50082c3f73477b8187cc5bf671655df21
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365942"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames function

Načte názvy všech kvalifikátory nebo určitých kvalifikátorů, které jsou k dispozici z aktuální objekt nebo vlastnost.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
[in] Tento parametr se nepoužívá.

`ptr`\
[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`lFlags`\
[in] Jeden z následujících příznaků nebo hodnoty, které určuje názvy, které chcete zahrnout do výčtu.

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|  | 0 | Vrátí názvy všech kvalifikátory. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátíte pouze názvy kvalifikátory konkrétní aktuální vlastnost nebo objekt. <br/> Pro vlastnost: Vrátí jenom v kvalifikátorech specifické pro vlastnost (včetně potlačení) a ne kvalifikátory, rozšířena z definice třídy. <br/> Pro instanci: Vrátíte pouze názvy instancí kvalifikátoru. <br/> Pro třídu: Vrátíte pouze kvalifikátory konkrétní třídy je odvozený.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Vrátit pouze názvy kvalifikátory rozšířena z jiného objektu. <br/> Pro vlastnost: Vrátit se rozšířit jenom v kvalifikátorech k této vlastnosti z definice třídy a ne ty ze samotné vlastnosti. <br/> Pro instanci: Vrátit pouze ty kvalifikátory rozšířena z definice třídy. <br/> Pro třídu: Vrátit pouze názvy kvalifikátor zděděná z nadřazené třídy. |

`pstrNames`\
[out] Nový `SAFEARRAY` , který obsahuje požadované názvy. Pole může mít 0 prvků. Pokud dojde k chybě, nový `SAFEARRAY` nevrátí.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici zahájíte nový výčet. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) metody.

Až jsme načíst názvy kvalifikátor, voláním dostanete každý kvalifikátor podle názvu [QualifierSet_Get](qualifierset-get.md) funkce.

Není chybu pro daný objekt má nulovou kvalifikátory tak počet řetězců v `pstrNames` návratu může být 0, i když funkce vrátí `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)