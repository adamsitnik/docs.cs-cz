---
title: GetTypeLibInfo – funkce
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d12cbb66464baba4ee706ccb076764fbf025fc5f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148535"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="bbde8-102">GetTypeLibInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="bbde8-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="bbde8-103">Vrátí informace o zadané knihovny typů prozkoumáním jeho [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) struktury.</span><span class="sxs-lookup"><span data-stu-id="bbde8-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbde8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbde8-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbde8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbde8-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="bbde8-106">[in] Název souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bbde8-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="bbde8-107">[out] Identifikátor GUID knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bbde8-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="bbde8-108">[out] ID lokalizace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bbde8-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="bbde8-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) příznak, který identifikuje cílový operační systém pro knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="bbde8-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="bbde8-110">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="bbde8-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="bbde8-111">[out] Číslo hlavní verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bbde8-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="bbde8-112">Například pro verzi *x.y*, je číslo hlavní verze *x*.</span><span class="sxs-lookup"><span data-stu-id="bbde8-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="bbde8-113">[out] Číslo podverze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bbde8-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="bbde8-114">Například pro verzi *x.y*, je číslo podverze *y*.</span><span class="sxs-lookup"><span data-stu-id="bbde8-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbde8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbde8-115">Remarks</span></span>  
 <span data-ttu-id="bbde8-116">`GetTypeLibInfo` Funkce je volána [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="bbde8-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="bbde8-117">Tento nástroj generuje knihovnu typů popisující typy v sestavení common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="bbde8-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="bbde8-118">Pokud libovolný parametr má hodnotu null, funkce vrátí `HRESULT` z `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="bbde8-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="bbde8-119">V opačném případě vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="bbde8-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbde8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bbde8-120">Requirements</span></span>  
 <span data-ttu-id="bbde8-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbde8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbde8-122">**Záhlaví:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="bbde8-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="bbde8-123">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="bbde8-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="bbde8-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbde8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbde8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbde8-125">See also</span></span>

- [<span data-ttu-id="bbde8-126">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="bbde8-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="bbde8-127">LoadTypeLibEx – funkce</span><span class="sxs-lookup"><span data-stu-id="bbde8-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
