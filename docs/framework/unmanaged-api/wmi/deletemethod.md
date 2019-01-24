---
title: Funkce DeleteMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce DeleteMethod odstraní zadanou metodu z definice třídy CIM.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb7b800bca1957c8c324ddb9c11cb4eabb49cd24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628484"
---
# <a name="deletemethod-function"></a><span data-ttu-id="a290a-103">Funkce DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="a290a-103">DeleteMethod function</span></span>
<span data-ttu-id="a290a-104">Odstraní zadanou metodu z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="a290a-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a290a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a290a-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="a290a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a290a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a290a-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a290a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a290a-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="a290a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="a290a-109">[in] Název metody, která odebere z tabulky třídy.</span><span class="sxs-lookup"><span data-stu-id="a290a-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="a290a-110">`wszName` musí být ukazatel na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="a290a-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a290a-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a290a-111">Return value</span></span>

<span data-ttu-id="a290a-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="a290a-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a290a-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a290a-113">Constant</span></span>  |<span data-ttu-id="a290a-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a290a-114">Value</span></span>  |<span data-ttu-id="a290a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a290a-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="a290a-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a290a-116">0x80041002</span></span> | <span data-ttu-id="a290a-117">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="a290a-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a290a-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a290a-118">0x80041006</span></span> | <span data-ttu-id="a290a-119">Není k dispozici dostatek paměti k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="a290a-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a290a-120">0</span><span class="sxs-lookup"><span data-stu-id="a290a-120">0</span></span> | <span data-ttu-id="a290a-121">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a290a-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a290a-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a290a-122">Remarks</span></span>

<span data-ttu-id="a290a-123">Tato funkce zalamuje volání na [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) metody.</span><span class="sxs-lookup"><span data-stu-id="a290a-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="a290a-124">Metoda odstranění není podporováno pro [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ukazatele, které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="a290a-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="a290a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a290a-125">Requirements</span></span>  
 <span data-ttu-id="a290a-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a290a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a290a-127">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a290a-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a290a-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a290a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a290a-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a290a-129">See also</span></span>
- [<span data-ttu-id="a290a-130">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a290a-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
