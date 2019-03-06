---
title: Funkce PutInstanceWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce PutInstanceWmi vytvoří nebo aktualizuje instance existující třídy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19f657fd76f73c4016824511079e6f037bc3bc53
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359370"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="7e257-103">PutInstanceWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="7e257-103">PutInstanceWmi function</span></span>

<span data-ttu-id="7e257-104">Vytvoří nebo aktualizuje instance existující třídy.</span><span class="sxs-lookup"><span data-stu-id="7e257-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="7e257-105">Instance se zapisují do úložiště služby WMI.</span><span class="sxs-lookup"><span data-stu-id="7e257-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7e257-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e257-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="7e257-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e257-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="7e257-108">[in] Ukazatel na instance, která má být zapsána.</span><span class="sxs-lookup"><span data-stu-id="7e257-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="7e257-109">[in] Kombinace příznaků, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="7e257-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="7e257-110">Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="7e257-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7e257-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7e257-111">Constant</span></span>  |<span data-ttu-id="7e257-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7e257-112">Value</span></span>  |<span data-ttu-id="7e257-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7e257-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="7e257-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="7e257-114">0x20000</span></span> | <span data-ttu-id="7e257-115">Pokud nastavíte, WMI neukládá všechny kvalifikátory s **Amended** charakter.</span><span class="sxs-lookup"><span data-stu-id="7e257-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="7e257-116">Pokud není sada, předpokládá se, že tento objekt není lokalizována, a všechny kvalifikátory jsou uloženy s touto instancí.</span><span class="sxs-lookup"><span data-stu-id="7e257-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="7e257-117">0</span><span class="sxs-lookup"><span data-stu-id="7e257-117">0</span></span> | <span data-ttu-id="7e257-118">Vytvořte instanci, pokud ho neexistuje, nebo ho přepíše, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="7e257-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="7e257-119">1</span><span class="sxs-lookup"><span data-stu-id="7e257-119">1</span></span> | <span data-ttu-id="7e257-120">Aktualizace instance.</span><span class="sxs-lookup"><span data-stu-id="7e257-120">Update the instance.</span></span> <span data-ttu-id="7e257-121">Instance musí existovat volání k dosažení úspěchu.</span><span class="sxs-lookup"><span data-stu-id="7e257-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="7e257-122">2</span><span class="sxs-lookup"><span data-stu-id="7e257-122">2</span></span> | <span data-ttu-id="7e257-123">Vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="7e257-123">Create the instance.</span></span> <span data-ttu-id="7e257-124">Volání selže, pokud instanci již existuje.</span><span class="sxs-lookup"><span data-stu-id="7e257-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="7e257-125">0x10</span><span class="sxs-lookup"><span data-stu-id="7e257-125">0x10</span></span> | <span data-ttu-id="7e257-126">Příznak způsobí, že volání semisynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="7e257-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="7e257-127">[in] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="7e257-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="7e257-128">V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="7e257-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="7e257-129">[out] Pokud `null`, tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7e257-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="7e257-130">Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí hodnotu okamžitě s `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="7e257-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="7e257-131">`ppCallResult` Parametr přijímá ukazatel na novou [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) objektu.</span><span class="sxs-lookup"><span data-stu-id="7e257-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e257-132">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7e257-132">Return value</span></span>

<span data-ttu-id="7e257-133">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="7e257-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7e257-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7e257-134">Constant</span></span>  |<span data-ttu-id="7e257-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7e257-135">Value</span></span>  |<span data-ttu-id="7e257-136">Popis</span><span class="sxs-lookup"><span data-stu-id="7e257-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="7e257-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="7e257-137">0x80041003</span></span> | <span data-ttu-id="7e257-138">Uživatel nemá oprávnění k aktualizaci instance dané třídy.</span><span class="sxs-lookup"><span data-stu-id="7e257-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="7e257-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="7e257-139">0x80041001</span></span> | <span data-ttu-id="7e257-140">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="7e257-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="7e257-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="7e257-141">0x80041010</span></span> | <span data-ttu-id="7e257-142">Třídu podporující tuto instanci není platný.</span><span class="sxs-lookup"><span data-stu-id="7e257-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="7e257-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="7e257-143">0x80041028</span></span> | <span data-ttu-id="7e257-144">`null` zadaná pro vlastnost, která nemůže být `null`, jako je ten, který je označen **indexovat** nebo **Not_Null** kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="7e257-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="7e257-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="7e257-145">0x8004100f</span></span> | <span data-ttu-id="7e257-146">Zadaná instance není platný.</span><span class="sxs-lookup"><span data-stu-id="7e257-146">The specified instance is not valid.</span></span> <span data-ttu-id="7e257-147">(Například voláním `PutInstanceWmi` s třídou vrátí tuto hodnotu.)</span><span class="sxs-lookup"><span data-stu-id="7e257-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7e257-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7e257-148">0x80041008</span></span> | <span data-ttu-id="7e257-149">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="7e257-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="7e257-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="7e257-150">0x80041019</span></span> | <span data-ttu-id="7e257-151">`WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, ale instanci již existuje.</span><span class="sxs-lookup"><span data-stu-id="7e257-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="7e257-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7e257-152">0x80041002</span></span> | <span data-ttu-id="7e257-153">`WBEM_FLAG_UPDATE_ONLY` byl zadán v `lFlags`, ale instance neexistuje.</span><span class="sxs-lookup"><span data-stu-id="7e257-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7e257-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7e257-154">0x80041006</span></span> | <span data-ttu-id="7e257-155">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="7e257-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="7e257-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="7e257-156">0x80041033</span></span> | <span data-ttu-id="7e257-157">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="7e257-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="7e257-158">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="7e257-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="7e257-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="7e257-159">0x80041015</span></span> | <span data-ttu-id="7e257-160">Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="7e257-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7e257-161">0</span><span class="sxs-lookup"><span data-stu-id="7e257-161">0</span></span> | <span data-ttu-id="7e257-162">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7e257-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7e257-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e257-163">Remarks</span></span>

<span data-ttu-id="7e257-164">Tato funkce zalamuje volání na [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) metody.</span><span class="sxs-lookup"><span data-stu-id="7e257-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="7e257-165">`PutInstanceWmi` Funkce podporuje vytváření instancí a aktualizaci instance pouze existující třídy.</span><span class="sxs-lookup"><span data-stu-id="7e257-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="7e257-166">V závislosti na tom, jak `pCtx` parametr je nastaven, některé nebo všechny vlastnosti instance se aktualizují.</span><span class="sxs-lookup"><span data-stu-id="7e257-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="7e257-167">Když instance odkazované `pInst` patří na podtřídu Windows Management volání všichni poskytovatelé za tříd, z něhož pochází podtřídy.</span><span class="sxs-lookup"><span data-stu-id="7e257-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="7e257-168">Všechny tyto zprostředkovatele musí být úspěšně pro původní `PutInstanceWmi` žádost proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="7e257-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="7e257-169">Nejprve se nazývá poskytovatele podpora nejvyšší třídy v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="7e257-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="7e257-170">Pořadí volání pokračuje podtřídou třídy nejvyšší třídy a pokračuje shora dolů, dokud nedosáhne Windows Management provider pro třídu vlastnící instanci, na které odkazuje `pInst`.</span><span class="sxs-lookup"><span data-stu-id="7e257-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="7e257-171">Správa Windows nevolá zprostředkovatele pro všechny instance podřízené třídy.</span><span class="sxs-lookup"><span data-stu-id="7e257-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="7e257-172">Pokud aplikace musí aktualizovat instance, která patří do hierarchie tříd `pInst` parametr musí odkazovat na instanci obsahující vlastnosti, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="7e257-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="7e257-173">To znamená, vezměte v úvahu cílová instance, která patří do **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="7e257-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="7e257-174">**ClassB** instance je odvozena z **ClassA**, a **ClassA** definuje vlastnost **PropA**.</span><span class="sxs-lookup"><span data-stu-id="7e257-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="7e257-175">Pokud aplikace chce provést změnu na hodnotu **PropA** v **ClassB** instance, je nutné nastavit `pInst` pro tuto instanci spíše než instance **ClassA** .</span><span class="sxs-lookup"><span data-stu-id="7e257-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="7e257-176">Volání `PutInstanceWmi` na instanci abstraktní třídy není povolený.</span><span class="sxs-lookup"><span data-stu-id="7e257-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="7e257-177">Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="7e257-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e257-178">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e257-178">Requirements</span></span>

<span data-ttu-id="7e257-179">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e257-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="7e257-180">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7e257-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="7e257-181">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7e257-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7e257-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e257-182">See also</span></span>

- [<span data-ttu-id="7e257-183">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="7e257-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)