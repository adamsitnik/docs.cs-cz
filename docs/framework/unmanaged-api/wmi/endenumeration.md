---
title: Funkce EndEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce EndEnumeration ukončí výčet.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f80503277d6a5d748dffa7783a19c6353b2e7f8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505117"
---
# <a name="endenumeration-function"></a><span data-ttu-id="7eca7-103">Funkce EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="7eca7-103">EndEnumeration function</span></span>
<span data-ttu-id="7eca7-104">Ukončí sekvenci výčet začít volání [funkce BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7eca7-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="7eca7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eca7-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="7eca7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7eca7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7eca7-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7eca7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7eca7-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="7eca7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="7eca7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7eca7-109">Return value</span></span>

<span data-ttu-id="7eca7-110">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="7eca7-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7eca7-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7eca7-111">Constant</span></span>  |<span data-ttu-id="7eca7-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7eca7-112">Value</span></span>  |<span data-ttu-id="7eca7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7eca7-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="7eca7-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="7eca7-114">0x80041001</span></span> | <span data-ttu-id="7eca7-115">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="7eca7-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7eca7-116">0</span><span class="sxs-lookup"><span data-stu-id="7eca7-116">0</span></span> | <span data-ttu-id="7eca7-117">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7eca7-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7eca7-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7eca7-118">Remarks</span></span>

<span data-ttu-id="7eca7-119">Tato funkce zalamuje volání na [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) metody.</span><span class="sxs-lookup"><span data-stu-id="7eca7-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="7eca7-120">Volání `EndEnumeration` funkce se nevyžaduje, ale doporučuje se, protože ho uvolní prostředky spojené s výčtem.</span><span class="sxs-lookup"><span data-stu-id="7eca7-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="7eca7-121">Resoruces však jsou automaticky uvolní, při spuštění další výčet nebo objekt uvolněn.</span><span class="sxs-lookup"><span data-stu-id="7eca7-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="7eca7-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7eca7-122">Requirements</span></span>  
 <span data-ttu-id="7eca7-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eca7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eca7-124">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7eca7-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7eca7-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7eca7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eca7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7eca7-126">See also</span></span>
- [<span data-ttu-id="7eca7-127">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="7eca7-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
