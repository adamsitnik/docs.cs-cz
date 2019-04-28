---
title: PUT – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce Put přiřadí novou hodnotu s názvem vlastnosti.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02c8ab3aa7fcc603b76fb4b1d09e7e73d04494be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749017"
---
# <a name="put-function"></a><span data-ttu-id="14434-103">PUT – funkce</span><span class="sxs-lookup"><span data-stu-id="14434-103">Put function</span></span>

<span data-ttu-id="14434-104">Pojmenovanou vlastnost nastaví na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="14434-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="14434-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14434-105">Syntax</span></span>

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a><span data-ttu-id="14434-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="14434-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="14434-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="14434-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="14434-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="14434-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="14434-109">[in] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="14434-109">[in] The name of the property.</span></span> <span data-ttu-id="14434-110">Tento parametr nemůže mít `null`.</span><span class="sxs-lookup"><span data-stu-id="14434-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="14434-111">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="14434-111">[in] Reserved.</span></span> <span data-ttu-id="14434-112">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="14434-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="14434-113">[in] Ukazatel na platný `VARIANT` , který se stane hodnota nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="14434-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="14434-114">Pokud `pVal` je `null` nebo odkazuje `VARIANT` typu `VT_NULL`, je nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="14434-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="14434-115">[in] Typ `VARIANT` odkazované `pVal`.</span><span class="sxs-lookup"><span data-stu-id="14434-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="14434-116">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="14434-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="14434-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="14434-117">Return value</span></span>

<span data-ttu-id="14434-118">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="14434-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="14434-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="14434-119">Constant</span></span>  |<span data-ttu-id="14434-120">Value</span><span class="sxs-lookup"><span data-stu-id="14434-120">Value</span></span>  |<span data-ttu-id="14434-121">Popis</span><span class="sxs-lookup"><span data-stu-id="14434-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="14434-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="14434-122">0x80041001</span></span> | <span data-ttu-id="14434-123">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="14434-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="14434-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="14434-124">0x80041008</span></span> | <span data-ttu-id="14434-125">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="14434-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="14434-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="14434-126">0x8004102a</span></span> | <span data-ttu-id="14434-127">Typ vlastnosti nebyl rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="14434-127">The property type is not recognized.</span></span> <span data-ttu-id="14434-128">Tato hodnota se vrátí při vytváření instance třídy, pokud třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="14434-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="14434-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="14434-129">0x80041006</span></span> | <span data-ttu-id="14434-130">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="14434-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="14434-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="14434-131">0x80041005</span></span> | <span data-ttu-id="14434-132">Pro instance: Označuje, že `pVal` odkazuje `VARIANT` nesprávného typu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="14434-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="14434-133">Definice třídy: Vlastnost již existuje v nadřazené třídě a nový typ modelu COM se liší od původní modelu COM typu.</span><span class="sxs-lookup"><span data-stu-id="14434-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="14434-134">0</span><span class="sxs-lookup"><span data-stu-id="14434-134">0</span></span> | <span data-ttu-id="14434-135">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="14434-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="14434-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14434-136">Remarks</span></span>

<span data-ttu-id="14434-137">Tato funkce zalamuje volání na [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.</span><span class="sxs-lookup"><span data-stu-id="14434-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="14434-138">Tato funkce vždy přepíše aktuální hodnota vlastnosti nové.</span><span class="sxs-lookup"><span data-stu-id="14434-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="14434-139">Pokud [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na definici třídy `Put` vytvoří nebo aktualizuje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="14434-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="14434-140">Když [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na instanci CIM `Put` aktualizuje hodnotu vlastnosti. `Put` nelze vytvořit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="14434-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="14434-141">`__CLASS` Vlastnost systému zapisovatelnou pouze při vytváření třídy, když ji nemůže být ponecháno prázdné.</span><span class="sxs-lookup"><span data-stu-id="14434-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="14434-142">Všechny ostatní vlastnosti systému jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="14434-142">All other system properties are read-only.</span></span>

<span data-ttu-id="14434-143">Uživatele nelze vytvořit vlastnosti s názvy, které začínat ani končit znakem podtržítka ("_").</span><span class="sxs-lookup"><span data-stu-id="14434-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="14434-144">To je vyhrazen pro systémové třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="14434-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="14434-145">Pokud vlastnost nastavil `Put` funkce existuje v nadřazené třídě, výchozí hodnota vlastnosti je změnit, dokud se tento typ vlastnosti neodpovídá typu nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="14434-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="14434-146">Pokud vlastnost neexistuje a není v případě nesouladu typů, se vytvoří vlastnost.</span><span class="sxs-lookup"><span data-stu-id="14434-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="14434-147">Použití `vtType` parametr jenom při vytvoření nové vlastnosti v definici třídy CIM a `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="14434-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="14434-148">V takovém případě `vType` parametr určuje typ CIM vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="14434-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="14434-149">V každém případě `vtType` musí být 0.</span><span class="sxs-lookup"><span data-stu-id="14434-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="14434-150">`vtType` musí také být 0, pokud je podkladový objekt instancí (i v případě `Val` je `null`) vzhledem k tomu, že typ vlastnosti je pevná a nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="14434-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="14434-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="14434-151">Example</span></span>

<span data-ttu-id="14434-152">Příklad najdete v tématu [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.</span><span class="sxs-lookup"><span data-stu-id="14434-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="14434-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14434-153">Requirements</span></span>

<span data-ttu-id="14434-154">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14434-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="14434-155">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="14434-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="14434-156">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="14434-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="14434-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14434-157">See also</span></span>

- [<span data-ttu-id="14434-158">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="14434-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)