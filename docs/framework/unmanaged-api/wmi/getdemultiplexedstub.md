---
title: Funkce GetDemultiplexedStub (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetDemultiplexedStub vytvoří pomáhat klientovi v přijetí byla zahájena asynchronní volání ze správy službou Windows Server pro předávání jímky objektu.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b519ea4062682a56b5b4e277de22b14799f65d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783220"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="26399-103">GetDemultiplexedStub – funkce</span><span class="sxs-lookup"><span data-stu-id="26399-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="26399-104">Vytvoří pomáhat klientovi v přijetí byla zahájena asynchronní volání ze správy službou Windows Server pro předávání jímky objektu.</span><span class="sxs-lookup"><span data-stu-id="26399-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="26399-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26399-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="26399-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="26399-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="26399-107">[in] Ukazatel na implementaci klienta v rámci procesu [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="26399-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="26399-108">[in] Příznak označující, zda je místní události (`true`); v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="26399-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="26399-109">[out] Objekt jímky předávání pomáhat klientovi v přijetí byla zahájena asynchronní volání ze správy Windows.</span><span class="sxs-lookup"><span data-stu-id="26399-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="26399-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26399-110">Return value</span></span>

<span data-ttu-id="26399-111">Pokud funkce uspěje, vrácená hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="26399-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="26399-112">Pokud funkce selže, vrácená hodnota je kód chyby.</span><span class="sxs-lookup"><span data-stu-id="26399-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="26399-113">Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="26399-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="26399-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26399-114">Requirements</span></span>  
 <span data-ttu-id="26399-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26399-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26399-116">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="26399-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="26399-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26399-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26399-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26399-118">See also</span></span>

- [<span data-ttu-id="26399-119">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="26399-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
