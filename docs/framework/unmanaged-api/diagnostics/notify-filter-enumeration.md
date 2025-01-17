---
title: NOTIFY_FILTER – výčet
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c36dd65c8a4202f13d362668f74cd9a362e35a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744365"
---
# <a name="notifyfilter-enumeration"></a>NOTIFY_FILTER – výčet
Identifikuje zpětná volání pro funkce ladicího programu. Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|Označuje, že [inotifysink2::onsynccallout –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) by měl vyvolat metodu.|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|Označuje, že [inotifysink2::onsynccallenter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) by měl vyvolat metodu.|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|Označuje, že [inotifysink2::onsynccallexit –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) by měl vyvolat metodu.|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|Označuje, že [inotifysink2::onsynccallreturn –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) by měl vyvolat metodu.|  
|`NOTIFY_FILTER_ALLSYNC`|Označuje, že všechny [inotifysink2 –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) metody by mělo být vyvoláno.|  
|`NOTIFY_FILTER_ALL`|Aktivuje všechny existující a budoucí oznámení.|  
|`NOTIFY_FILTER_NONE`|Označuje, že by měl vyvolat metody žádná oznámení.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
