---
title: ICorPublish::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3af824a23d683f4d450ef6f60fd407928c41d51e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536955"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="3da7b-102">ICorPublish::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="3da7b-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="3da7b-103">Získá enumerátor pro spravované procesy v tomto počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="3da7b-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3da7b-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3da7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3da7b-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="3da7b-106">Hodnota [cor_pub_enumprocess –](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) výčet, který určuje typ procesu, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="3da7b-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="3da7b-107">V aktuální verzi je platný pouze COR_PUB_MANAGEDONLY.</span><span class="sxs-lookup"><span data-stu-id="3da7b-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="3da7b-108">Ukazatel na adresu [icorpublishprocessenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instanci, která je enumerátor procesy.</span><span class="sxs-lookup"><span data-stu-id="3da7b-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3da7b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3da7b-109">Remarks</span></span>  
 <span data-ttu-id="3da7b-110">Čítače výčtu kolekce procesů je založena na snímek procesy, které jsou spuštěny při `EnumProcesses` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="3da7b-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="3da7b-111">Enumerátor nebude obsahovat žádné procesy, které ukončí před nebo po spuštění `EnumProcesses` je volána.</span><span class="sxs-lookup"><span data-stu-id="3da7b-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="3da7b-112">`EnumProcesses` Metoda může být volána více než jednou v tomto [icorpublish –](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance má vytvořit novou kolekci aktuálních procesů.</span><span class="sxs-lookup"><span data-stu-id="3da7b-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="3da7b-113">Stávajících kolekcí nebudou vztahovat následných volání `EnumProcesses` metody.</span><span class="sxs-lookup"><span data-stu-id="3da7b-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da7b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3da7b-114">Requirements</span></span>  
 <span data-ttu-id="3da7b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3da7b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3da7b-116">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3da7b-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3da7b-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3da7b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3da7b-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da7b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da7b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3da7b-119">See also</span></span>
- [<span data-ttu-id="3da7b-120">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3da7b-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
