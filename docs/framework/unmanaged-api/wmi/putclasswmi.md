---
title: Funkce PutClassWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce PutClassWmi vytvoří novou třídu nebo aktualizuje nějakou existující.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422de614d2e2ddb93cc1e932a8672e1e8269b2c0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636650"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="b4025-103">PutClassWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="b4025-103">PutClassWmi function</span></span>

<span data-ttu-id="b4025-104">Vytvoří novou třídu nebo aktualizuje nějakou existující.</span><span class="sxs-lookup"><span data-stu-id="b4025-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b4025-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4025-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="b4025-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4025-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="b4025-107">[in] Ukazatel na platnou definicí třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="b4025-108">To musí být správně inicializován se všemi hodnotami požadovaná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4025-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="b4025-109">[in] Kombinace příznaků, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="b4025-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="b4025-110">Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="b4025-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b4025-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b4025-111">Constant</span></span>  |<span data-ttu-id="b4025-112">Value</span><span class="sxs-lookup"><span data-stu-id="b4025-112">Value</span></span>  |<span data-ttu-id="b4025-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b4025-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="b4025-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="b4025-114">0x20000</span></span> | <span data-ttu-id="b4025-115">Pokud sada WMI neukládá všechny kvalifikátory s upravenou charakter.</span><span class="sxs-lookup"><span data-stu-id="b4025-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="b4025-116">Pokud není sada, předpokládá se, že tento objekt není lokalizována, a všechny kvalifikátory jsou uloženy s touto instancí.</span><span class="sxs-lookup"><span data-stu-id="b4025-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="b4025-117">0</span><span class="sxs-lookup"><span data-stu-id="b4025-117">0</span></span> | <span data-ttu-id="b4025-118">Vytvořte třídu, pokud ho neexistuje, nebo ho přepíše, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="b4025-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="b4025-119">1</span><span class="sxs-lookup"><span data-stu-id="b4025-119">1</span></span> | <span data-ttu-id="b4025-120">Aktualizace třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-120">Update the class.</span></span> <span data-ttu-id="b4025-121">Třída musí existovat volání k dosažení úspěchu.</span><span class="sxs-lookup"><span data-stu-id="b4025-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="b4025-122">2</span><span class="sxs-lookup"><span data-stu-id="b4025-122">2</span></span> | <span data-ttu-id="b4025-123">Vytvořte třídu.</span><span class="sxs-lookup"><span data-stu-id="b4025-123">Create the class.</span></span> <span data-ttu-id="b4025-124">Volání selže, pokud třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="b4025-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="b4025-125">0x10</span><span class="sxs-lookup"><span data-stu-id="b4025-125">0x10</span></span> | <span data-ttu-id="b4025-126">Příznak způsobí, že volání semisynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="b4025-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="b4025-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="b4025-127">0x10000</span></span> | <span data-ttu-id="b4025-128">Poskytovatelé nabízených oznámení musíte zadat Tento příznak, při volání metody `PutClassWmi` k označení, že došlo ke změně této třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="b4025-129">0</span><span class="sxs-lookup"><span data-stu-id="b4025-129">0</span></span> | <span data-ttu-id="b4025-130">Umožňuje třídy aktualizace, pokud neexistují žádné odvozené třídy a bez instance dané třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="b4025-131">Také umožňuje instalaci aktualizací ve všech případech, pokud se tato změna je to důležitý kvalifikátory, jako je například kvalifikátor popis.</span><span class="sxs-lookup"><span data-stu-id="b4025-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="b4025-132">Pokud existuje instance dané třídy nebo změny jsou důležité kvalifikátory, že se aktualizace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b4025-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="b4025-133">0x20</span><span class="sxs-lookup"><span data-stu-id="b4025-133">0x20</span></span> | <span data-ttu-id="b4025-134">Umožňuje instalaci aktualizací tříd, i když nejsou podřízené třídy za předpokladu, změna nezpůsobí žádné konflikty s podřízenými třídami.</span><span class="sxs-lookup"><span data-stu-id="b4025-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="b4025-135">Tento příznak například umožňuje nové vlastnosti a přidat základní třídu, která se již bylo zmíněno dříve v některém z podřízených tříd.</span><span class="sxs-lookup"><span data-stu-id="b4025-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="b4025-136">Pokud má třída instancí, že se aktualizace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b4025-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="b4025-137">0x40</span><span class="sxs-lookup"><span data-stu-id="b4025-137">0x40</span></span> | <span data-ttu-id="b4025-138">Vynutí aktualizace tříd, pokud existuje konfliktní podřízené třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="b4025-139">Například tento příznak vynutí aktualizaci v případě kvalifikátor třída je definována v podřízené třídy a základní třídy se pokusí přidat stejný kvalifikátor který je v konfliktu s existujícím.</span><span class="sxs-lookup"><span data-stu-id="b4025-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="b4025-140">V režimu vynucení tis konflikt vyřešit odstraněním konfliktní kvalifikátoru v podřízené třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="b4025-141">[in] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="b4025-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="b4025-142">V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="b4025-143">[out] Pokud `null`, tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b4025-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="b4025-144">Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí hodnotu okamžitě s `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="b4025-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="b4025-145">`ppCallResult` Parametr přijímá ukazatel na novou [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) objektu.</span><span class="sxs-lookup"><span data-stu-id="b4025-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="b4025-146">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4025-146">Return value</span></span>

<span data-ttu-id="b4025-147">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="b4025-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b4025-148">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b4025-148">Constant</span></span>  |<span data-ttu-id="b4025-149">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b4025-149">Value</span></span>  |<span data-ttu-id="b4025-150">Popis</span><span class="sxs-lookup"><span data-stu-id="b4025-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="b4025-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="b4025-151">0x80041003</span></span> | <span data-ttu-id="b4025-152">Uživatel nemá oprávnění k vytvoření nebo úpravě třídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="b4025-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b4025-153">0x80041001</span></span> | <span data-ttu-id="b4025-154">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="b4025-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="b4025-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="b4025-155">0x80041010</span></span> | <span data-ttu-id="b4025-156">Zadaná třída není platná.</span><span class="sxs-lookup"><span data-stu-id="b4025-156">The specified class is not valid.</span></span> <span data-ttu-id="b4025-157">Obvykle to znamená, že `pObject` určuje objekt instance.</span><span class="sxs-lookup"><span data-stu-id="b4025-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b4025-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b4025-158">0x80041008</span></span> | <span data-ttu-id="b4025-159">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="b4025-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="b4025-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="b4025-160">0x80041016</span></span> | <span data-ttu-id="b4025-161">Zadaná třída název je neplatný.</span><span class="sxs-lookup"><span data-stu-id="b4025-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="b4025-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="b4025-162">0x80041025</span></span> | <span data-ttu-id="b4025-163">Byl proveden pokus o provést změny, které by způsobily neplatnost podtřídy.</span><span class="sxs-lookup"><span data-stu-id="b4025-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="b4025-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="b4025-164">0x80041019</span></span> | <span data-ttu-id="b4025-165">`WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, ale třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="b4025-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="b4025-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="b4025-166">0x80041002</span></span> | <span data-ttu-id="b4025-167">`WBEM_FLAG_UPDATE_ONLY` byl zadán v `lFlags`, a třída nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="b4025-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="b4025-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="b4025-168">0x80041020</span></span> | <span data-ttu-id="b4025-169">Požadované vlastnosti pro třídy jsou všechny nastavené.</span><span class="sxs-lookup"><span data-stu-id="b4025-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b4025-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b4025-170">0x80041006</span></span> | <span data-ttu-id="b4025-171">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="b4025-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="b4025-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="b4025-172">0x80041033</span></span> | <span data-ttu-id="b4025-173">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="b4025-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="b4025-174">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="b4025-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b4025-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b4025-175">0x80041015</span></span> | <span data-ttu-id="b4025-176">Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="b4025-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b4025-177">0</span><span class="sxs-lookup"><span data-stu-id="b4025-177">0</span></span> | <span data-ttu-id="b4025-178">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b4025-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="b4025-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4025-179">Remarks</span></span>

<span data-ttu-id="b4025-180">Tato funkce zalamuje volání na [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) metody.</span><span class="sxs-lookup"><span data-stu-id="b4025-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="b4025-181">Uživatel nemůže vytvořit třídy s názvy, které začínat ani končit znakem podtržítka.</span><span class="sxs-lookup"><span data-stu-id="b4025-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="b4025-182">Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="b4025-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4025-183">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4025-183">Requirements</span></span>

<span data-ttu-id="b4025-184">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4025-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b4025-185">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b4025-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="b4025-186">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4025-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b4025-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4025-187">See also</span></span>

- [<span data-ttu-id="b4025-188">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="b4025-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
