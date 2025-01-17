---
title: FormatFromRawValue – funkce (Reference nespravovaného rozhraní API)
description: Funkce FormatFromRawValue převede nezpracovaná data výkonu do určeného formátu.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5097cfe43ae785461a1e2af1217bcbd5e8c4b79c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120290"
---
# <a name="formatfromrawvalue-function"></a>Funkce FormatFromRawValue
Převede jednu nezpracovaná hodnota dat výkonu na určený formát nebo dvě nezpracované hodnoty dat výkonu, pokud je převod formátu založený na čase. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a>Parametry

`dwCounterType`\
pro Typ čítače. Seznam typů čítačů najdete v tématu [typy čítačů výkonu služby WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` může být jakýkoli typ čítače s výjimkou `PERF_LARGE_RAW_FRACTION` a `PERF_LARGE_RAW_BASE`. 

`dwFormat`\
pro Formát, ve kterém mají být převedena nezpracovaná data výkonu. Může to být jedna z následujících hodnot:

|Konstanta  |Hodnota  |Popis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Vrátí počítanou hodnotu jako hodnotu s dvojitou přesností s plovoucí desetinnou čárkou. | 
| `PDH_FMT_LARGE` | 0x00000400 | Vrátí počítanou hodnotu jako celé číslo 64. |
| `PDH_FMT_LONG` | 0x00000100 | Vrátí počítanou hodnotu jako celé číslo 32. |

Jedna z předchozích hodnot může být ORed s jedním z následujících příznaků škálování:

|Konstanta  |Hodnota  |Popis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Nepoužívejte faktory škálování čítače. |
| `PDH_FMT_1000` | 0x00002000 | Vynásobte konečnou hodnotu hodnotou 1 000. | 

`pTimeBase`\
pro Ukazatel na časový základ, je-li to nutné pro převod formátu. Pokud informace o časovém základu není pro převod formátu nutná, hodnota tohoto parametru je ignorována.

`pRawValue1`\ [in] ukazatel na strukturu [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) , která představuje nezpracovaný hodnotu výkonu.

`pRawValue2`\
pro Ukazatel na strukturu [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) , která představuje druhou hodnotu nezpracovaného výkonu. Není-li druhá hodnota nezpracovaného výkonu nutná, tento parametr by měl být `null`.

`pFmtValue`\
mimo Ukazatel na strukturu [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) , která přijímá naformátovanou hodnotu výkonu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty jsou vráceny touto funkcí:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0,8 | Volání funkce je úspěšné. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Požadovaný argument chybí nebo není správný. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Popisovač není platným objektem PDH. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání funkce [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) .

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Knihovna:** Dokončení PerfCounter. dll

 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
