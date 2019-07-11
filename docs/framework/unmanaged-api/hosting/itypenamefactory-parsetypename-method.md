---
title: ITypeNameFactory::ParseTypeName – metoda
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a4b2314adac222279e4cf0a53897725d63da0cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768583"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="beaab-102">ITypeNameFactory::ParseTypeName – metoda</span><span class="sxs-lookup"><span data-stu-id="beaab-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="beaab-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="beaab-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beaab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beaab-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="beaab-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="beaab-105">Requirements</span></span>  
 <span data-ttu-id="beaab-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beaab-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beaab-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="beaab-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="beaab-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="beaab-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="beaab-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beaab-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beaab-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="beaab-110">See also</span></span>

- [<span data-ttu-id="beaab-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="beaab-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
