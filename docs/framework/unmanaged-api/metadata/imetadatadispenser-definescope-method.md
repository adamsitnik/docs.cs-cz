---
title: IMetaDataDispenser::DefineScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76a439effad9cb3f6dcdd232590cf2196ee7ab99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044388"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="96f30-102">IMetaDataDispenser::DefineScope – metoda</span><span class="sxs-lookup"><span data-stu-id="96f30-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="96f30-103">Vytvoří nové oblasti v paměti, ve kterém můžete vytvořit nová metadata.</span><span class="sxs-lookup"><span data-stu-id="96f30-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96f30-104">Syntax</span></span>  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96f30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96f30-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="96f30-106">[in] Identifikátor CLSID verzi struktury metadat, který má být vytvořen</span><span class="sxs-lookup"><span data-stu-id="96f30-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="96f30-107">Tato hodnota musí být CLSID_CorMetaDataRuntime pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="96f30-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="96f30-108">[in] Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="96f30-108">[in] Flags that specify options.</span></span> <span data-ttu-id="96f30-109">Tato hodnota musí být nula pro rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="96f30-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="96f30-110">[in] Identifikátor IID rozhraní požadované metadat má být vrácen. volající pomocí rozhraní vytvořit nová metadata.</span><span class="sxs-lookup"><span data-stu-id="96f30-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="96f30-111">Hodnota `riid` musíte zadat jedno z rozhraní "generování".</span><span class="sxs-lookup"><span data-stu-id="96f30-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="96f30-112">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit nebo IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="96f30-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="96f30-113">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96f30-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96f30-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96f30-114">Remarks</span></span>  
 <span data-ttu-id="96f30-115">`DefineScope` Vytvoří sadu tabulek metadat v paměti, generuje jedinečný identifikátor GUID (identifikátor verze modulu nebo identifikátor MVID) pro metadata a vytvoří záznam v tabulce modulu pro jednotku kompilace probíhá emitovány.</span><span class="sxs-lookup"><span data-stu-id="96f30-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="96f30-116">Atributy můžete připojit k oboru metadat jako celek s použitím [imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) nebo [imetadataemit::definecustomattribute –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) metoda podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="96f30-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96f30-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96f30-117">Requirements</span></span>  
 <span data-ttu-id="96f30-118">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96f30-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96f30-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96f30-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96f30-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96f30-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96f30-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96f30-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f30-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96f30-122">See also</span></span>

- [<span data-ttu-id="96f30-123">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96f30-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="96f30-124">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96f30-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="96f30-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96f30-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="96f30-126">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96f30-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="96f30-127">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96f30-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
