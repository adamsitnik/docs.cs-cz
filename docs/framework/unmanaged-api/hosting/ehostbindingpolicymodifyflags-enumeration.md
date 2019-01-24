---
title: EHostBindingPolicyModifyFlags – výčet
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3aba84f1ae451ee943028d063e91ca7a6d63548
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504691"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags – výčet
Umožňuje hostiteli, chcete-li určit typ přesměrování, které modul CLR (CLR) má provést při použití změny zásad ze zdrojové sestavení do cílového sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Určuje, že modul CLR bude zřetězit hodnoty zásad zdroje sestavení na ty z cílového sestavení.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Určuje, že modul CLR provede výchozí akci.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Určuje, že modul CLR bude nastavena zásada má tyto hodnoty z cílového sestavení na maximální hodnoty.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Určuje, že modul CLR bude nahraďte hodnoty zásad z cílového sestavení u zdrojové sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrhostbindingpolicymanager::modifyapplicationpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) metoda přijímá parametr typu `EHostBindingPolicyModifyFlags`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRHostBindingPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
