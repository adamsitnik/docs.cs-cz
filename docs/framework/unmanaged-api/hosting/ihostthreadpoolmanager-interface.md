---
title: IHostThreadPoolManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: 8aef78c7cf70e6b2d97af9c47d57908b86729ff7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122075"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager – rozhraní
Poskytuje metody, které umožňují, aby modul CLR (Common Language Runtime) nakonfiguroval fond vláken a zařadil pracovní položky do fondu vláken.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAvailableThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|Získá počet vláken ve fondu vláken, které aktuálně nezpracovávají pracovní položky.|  
|[GetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Získá maximální počet vláken, která hostitel udržuje souběžně ve fondu vláken.|  
|[GetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Získá minimální počet nečinných vláken, která hostitel udržuje při předvídání požadavků.|  
|[QueueUserWorkItem – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Zařadí funkci do fronty pro spuštění a poskytuje objekt obsahující data, která má funkce používat.|  
|[SetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Nastaví maximální počet vláken, která může hostitel udržovat ve fondu vláken.|  
|[SetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Nastaví minimální počet nečinných vláken, které musí hostitel uchovávat při předvídání požadavků.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel není vyžadován ke konfiguraci fondu vláken pomocí hodnot zadaných v volání metody `SetMaxThreads` a `SetMinThreads`. V takovém případě by hostitel měl z těchto metod vrátit hodnotu HRESULT E_NOTIMPL.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
