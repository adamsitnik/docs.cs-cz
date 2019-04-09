---
title: Funkce SpawnDerivedClass (referenční dokumentace nespravovaného rozhraní API)
description: Funkce SpawnDerivedClass vytvoří nový objekt, který je odvozen z objektu.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f4d5219865bf7f7c9e6d284d74d0c249729dfc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194419"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="ef3bb-103">SpawnDerivedClass – funkce</span><span class="sxs-lookup"><span data-stu-id="ef3bb-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="ef3bb-104">Vytvoří objekt nově odvozené třídy ze zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ef3bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef3bb-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="ef3bb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef3bb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ef3bb-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ef3bb-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="ef3bb-109">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-109">[in] Reserved.</span></span> <span data-ttu-id="ef3bb-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="ef3bb-111">[out] Přijímá ukazatel na nový objekt definice třídy.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="ef3bb-112">Pokud dojde k chybě, není objekt vrácen, a `ppNewClass` je bez jakýchkoli úprav vlevo.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="ef3bb-113">Jeho hodnota nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ef3bb-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ef3bb-114">Return value</span></span>

<span data-ttu-id="ef3bb-115">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ef3bb-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ef3bb-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ef3bb-116">Constant</span></span>  |<span data-ttu-id="ef3bb-117">Value</span><span class="sxs-lookup"><span data-stu-id="ef3bb-117">Value</span></span>  |<span data-ttu-id="ef3bb-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ef3bb-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="ef3bb-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ef3bb-119">0x80041001</span></span> | <span data-ttu-id="ef3bb-120">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="ef3bb-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="ef3bb-121">0x80041016</span></span> | <span data-ttu-id="ef3bb-122">Neplatná operace, jako je například vytvoření třídy z instance, byl požadován.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="ef3bb-123">Zdrojovou třídu se není úplně definované nebo zaregistrován prostřednictvím služby Windows Management, tak novou odvozenou třídu není povolený.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ef3bb-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ef3bb-124">0x80041006</span></span> | <span data-ttu-id="ef3bb-125">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ef3bb-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ef3bb-126">0x80041008</span></span> | `ppNewClass` <span data-ttu-id="ef3bb-127">is `null`.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-127">is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ef3bb-128">0</span><span class="sxs-lookup"><span data-stu-id="ef3bb-128">0</span></span> | <span data-ttu-id="ef3bb-129">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ef3bb-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef3bb-130">Remarks</span></span>

<span data-ttu-id="ef3bb-131">Tato funkce zalamuje volání na [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

`ptr` <span data-ttu-id="ef3bb-132">musí být definice třídy, která se stává nadřazené třídu vytvořenému objektu.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-132">must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="ef3bb-133">Vrácený objekt se stane podtřídu aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="ef3bb-134">Nový objekt vrácený v `ppNewClass` automaticky stane podtřídu aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="ef3bb-135">Toto chování nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="ef3bb-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="ef3bb-136">Neexistuje žádná další metoda, podle kterého je možné vytvořit podtřídy (odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="ef3bb-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef3bb-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef3bb-137">Requirements</span></span>  
 <span data-ttu-id="ef3bb-138">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef3bb-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef3bb-139">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ef3bb-139">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="ef3bb-140">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ef3bb-140">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef3bb-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef3bb-141">See also</span></span>

- [<span data-ttu-id="ef3bb-142">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ef3bb-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
