---
title: GetErrorInfo – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetErrorInfo – načte informace o chybě z předchozího volání funkce.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2df4b87016394d1998ef90abe2e3eeb911886ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217495"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo – funkce
Načte informace o chybě z předchozího volání funkce.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a>Návratová hodnota

Ukazatel na [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) objektu, pokud bude volání funkce úspěšné, nebo `null` Pokud selže.
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.def  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
