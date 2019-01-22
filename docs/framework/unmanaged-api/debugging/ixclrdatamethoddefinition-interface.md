---
title: IXCLRDataMethodDefinition rozhraní
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4265db62b11453d9fc087928adb0cc0c05c052ca
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416087"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="2efaa-102">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="2efaa-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="2efaa-103">Poskytuje metody pro dotazování na informace o definici metody.</span><span class="sxs-lookup"><span data-stu-id="2efaa-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="2efaa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2efaa-104">Methods</span></span>

<span data-ttu-id="2efaa-105">Některé metody, která je k dispozici v rozhraní jsou tyto metody.</span><span class="sxs-lookup"><span data-stu-id="2efaa-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="2efaa-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2efaa-106">Method</span></span>                                                                                                                          | <span data-ttu-id="2efaa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2efaa-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="2efaa-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="2efaa-108">StartEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="2efaa-109">Poskytuje popisovač pro výčet metodu instance danou `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="2efaa-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="2efaa-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="2efaa-110">EnumInstance</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="2efaa-111">Vytvoří výčet instancí definici této metody.</span><span class="sxs-lookup"><span data-stu-id="2efaa-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="2efaa-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="2efaa-112">EndEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="2efaa-113">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="2efaa-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="2efaa-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2efaa-114">Remarks</span></span>

<span data-ttu-id="2efaa-115">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="2efaa-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="2efaa-116">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="2efaa-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="2efaa-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2efaa-117">Requirements</span></span>

<span data-ttu-id="2efaa-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2efaa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2efaa-119">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="2efaa-119">**Header:** None</span></span>  
<span data-ttu-id="2efaa-120">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="2efaa-120">**Library:** None</span></span>  
<span data-ttu-id="2efaa-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2efaa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2efaa-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2efaa-122">See Also</span></span>

- [<span data-ttu-id="2efaa-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="2efaa-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2efaa-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2efaa-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)