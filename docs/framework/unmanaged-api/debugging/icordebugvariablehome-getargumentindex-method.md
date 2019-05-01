---
title: ICorDebugVariableHome::GetArgumentIndex – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986788"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="a6783-102">ICorDebugVariableHome::GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="a6783-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="a6783-103">Získá index argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="a6783-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6783-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6783-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="a6783-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6783-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="a6783-106">[out] Ukazatel na index argumentu.</span><span class="sxs-lookup"><span data-stu-id="a6783-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="a6783-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a6783-107">Return Value</span></span>

<span data-ttu-id="a6783-108">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a6783-108">The method returns the following values.</span></span>

|<span data-ttu-id="a6783-109">Value</span><span class="sxs-lookup"><span data-stu-id="a6783-109">Value</span></span>|<span data-ttu-id="a6783-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a6783-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="a6783-111">Volání metody, které vrátí index platný argument.</span><span class="sxs-lookup"><span data-stu-id="a6783-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="a6783-112">Aktuální [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance představuje místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="a6783-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6783-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6783-113">Remarks</span></span>

<span data-ttu-id="a6783-114">Argument index je možné načíst metadata pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="a6783-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6783-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6783-115">Requirements</span></span>

<span data-ttu-id="a6783-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6783-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a6783-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6783-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a6783-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6783-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a6783-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6783-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a6783-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6783-120">See also</span></span>

- [<span data-ttu-id="a6783-121">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6783-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
