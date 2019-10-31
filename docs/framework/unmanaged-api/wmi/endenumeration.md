---
title: Funkce EndEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce funkce EndEnumeration ukončí výčet.
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b9fd1f094c8fb56c94421a07437aa25a3549c487
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132048"
---
# <a name="endenumeration-function"></a><span data-ttu-id="e146a-103">Funkce EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="e146a-103">EndEnumeration function</span></span>

<span data-ttu-id="e146a-104">Ukončí sekvenci výčtu spuštěnou voláním [funkce funkce BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e146a-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e146a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e146a-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="e146a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e146a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e146a-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e146a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e146a-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="e146a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="e146a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e146a-109">Return value</span></span>

<span data-ttu-id="e146a-110">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e146a-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e146a-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e146a-111">Constant</span></span>  |<span data-ttu-id="e146a-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e146a-112">Value</span></span>  |<span data-ttu-id="e146a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e146a-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e146a-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e146a-114">0x80041001</span></span> | <span data-ttu-id="e146a-115">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="e146a-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e146a-116">0,8</span><span class="sxs-lookup"><span data-stu-id="e146a-116">0</span></span> | <span data-ttu-id="e146a-117">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="e146a-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e146a-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e146a-118">Remarks</span></span>

<span data-ttu-id="e146a-119">Tato funkce zalomí volání metody [IWbemclassObject:: funkce EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="e146a-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="e146a-120">Volání funkce `EndEnumeration` není vyžadováno, ale doporučuje se, protože uvolňuje prostředky přidružené k výčtu.</span><span class="sxs-lookup"><span data-stu-id="e146a-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="e146a-121">Prostředky se ale oddělí automaticky při spuštění dalšího výčtu nebo uvolnění objektu.</span><span class="sxs-lookup"><span data-stu-id="e146a-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="e146a-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e146a-122">Requirements</span></span>

<span data-ttu-id="e146a-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e146a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e146a-124">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="e146a-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e146a-125">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e146a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e146a-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e146a-126">See also</span></span>

- [<span data-ttu-id="e146a-127">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e146a-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
