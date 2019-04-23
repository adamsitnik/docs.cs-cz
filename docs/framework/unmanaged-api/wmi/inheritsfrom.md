---
title: Funkce InheritsFrom (referenční dokumentace nespravovaného rozhraní API)
description: Funkce InheritsFrom Určuje, zda třídy nebo instance je odvozena z určité nadřazené třídy.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d2af1b41f47a3906c0e573c104847aa3ff36cf8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158428"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="325a6-103">InheritsFrom – funkce</span><span class="sxs-lookup"><span data-stu-id="325a6-103">InheritsFrom function</span></span>
<span data-ttu-id="325a6-104">Určuje, zda aktuální třídy nebo instance je odvozena od třídy zadaný nadřazený prvek.</span><span class="sxs-lookup"><span data-stu-id="325a6-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="325a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="325a6-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="325a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="325a6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="325a6-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="325a6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="325a6-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="325a6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="325a6-109">[in] Název třídy.</span><span class="sxs-lookup"><span data-stu-id="325a6-109">[in] The name of the class.</span></span> <span data-ttu-id="325a6-110">`wszAncestor` musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="325a6-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="325a6-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="325a6-111">Return value</span></span>

<span data-ttu-id="325a6-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="325a6-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="325a6-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="325a6-113">Constant</span></span>  |<span data-ttu-id="325a6-114">Value</span><span class="sxs-lookup"><span data-stu-id="325a6-114">Value</span></span>  |<span data-ttu-id="325a6-115">Popis</span><span class="sxs-lookup"><span data-stu-id="325a6-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="325a6-116">0</span><span class="sxs-lookup"><span data-stu-id="325a6-116">0</span></span> | <span data-ttu-id="325a6-117">Aktuální objekt dědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="325a6-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="325a6-118">1</span><span class="sxs-lookup"><span data-stu-id="325a6-118">1</span></span> | <span data-ttu-id="325a6-119">Aktuální objekt nedědí ze `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="325a6-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="325a6-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="325a6-120">0x80041008</span></span> | <span data-ttu-id="325a6-121">`wszAncestor` je `null`.</span><span class="sxs-lookup"><span data-stu-id="325a6-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="325a6-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="325a6-122">Remarks</span></span>

<span data-ttu-id="325a6-123">Tato funkce zalamuje volání na [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) metody.</span><span class="sxs-lookup"><span data-stu-id="325a6-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="325a6-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="325a6-124">Requirements</span></span>  
 <span data-ttu-id="325a6-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="325a6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="325a6-126">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="325a6-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="325a6-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="325a6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325a6-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="325a6-128">See also</span></span>

- [<span data-ttu-id="325a6-129">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="325a6-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
