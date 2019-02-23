---
title: ICorDebugProcess4 Interface
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221375"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="3583d-102">ICorDebugProcess4 Interface</span><span class="sxs-lookup"><span data-stu-id="3583d-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="3583d-103">Poskytuje podporu pro mimo proces řízení provádění.</span><span class="sxs-lookup"><span data-stu-id="3583d-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="3583d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3583d-104">Methods</span></span>

| <span data-ttu-id="3583d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3583d-105">Method</span></span>                                                                 | <span data-ttu-id="3583d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3583d-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="3583d-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="3583d-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="3583d-108">Upozorní ICorDebug kanálu, že je vzdálený ladicí program procesu pokračovat v provádění od laděného objektu.</span><span class="sxs-lookup"><span data-stu-id="3583d-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3583d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3583d-109">Remarks</span></span>

<span data-ttu-id="3583d-110">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="3583d-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="3583d-111">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="3583d-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="3583d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3583d-112">Requirements</span></span>

<span data-ttu-id="3583d-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3583d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="3583d-114">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3583d-114">**Header:** None</span></span>

<span data-ttu-id="3583d-115">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3583d-115">**Library:** None</span></span>

<span data-ttu-id="3583d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3583d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3583d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3583d-117">See also</span></span>

- [<span data-ttu-id="3583d-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3583d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3583d-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="3583d-119">Debugging</span></span>](index.md)