---
title: StrongNameCompareAssemblies – funkce
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: adde52dddb63b83dcd7ff10703a43928d9601c92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140617"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="5c1ed-102">StrongNameCompareAssemblies – funkce</span><span class="sxs-lookup"><span data-stu-id="5c1ed-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="5c1ed-103">Určuje, zda se dvě sestavení liší pouze signaturami silného názvu.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="5c1ed-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-104">This function has been deprecated.</span></span> <span data-ttu-id="5c1ed-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameCompareAssemblies –](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5c1ed-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c1ed-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c1ed-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c1ed-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c1ed-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="5c1ed-108">pro Cesta k prvnímu sestavení</span><span class="sxs-lookup"><span data-stu-id="5c1ed-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="5c1ed-109">pro Cesta k druhému sestavení</span><span class="sxs-lookup"><span data-stu-id="5c1ed-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="5c1ed-110">mimo Jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="5c1ed-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="5c1ed-111">`SN_CMP_DIFFERENT` (0) – určuje, že sestavení obsahují odlišná data.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="5c1ed-112">`SN_CMP_IDENTICAL` (1) – určuje, že sestavení jsou přesně stejná, včetně jejich podpisů a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="5c1ed-113">`SN_CMP_SIGONLY` (2) – určuje, že se sestavení liší pouze pomocí signatury a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c1ed-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c1ed-114">Return Value</span></span>  
 <span data-ttu-id="5c1ed-115">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c1ed-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c1ed-116">Requirements</span></span>  
 <span data-ttu-id="5c1ed-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c1ed-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c1ed-118">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="5c1ed-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5c1ed-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5c1ed-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c1ed-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c1ed-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c1ed-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c1ed-121">Remarks</span></span>  
 <span data-ttu-id="5c1ed-122">Podpis silného názvu sestavení se skládá z textového názvu sestavení, verze, jazykové verze a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="5c1ed-123">Pokud se funkce `StrongNameCompareAssemblies` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="5c1ed-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1ed-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c1ed-124">See also</span></span>

- [<span data-ttu-id="5c1ed-125">StrongNameCompareAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="5c1ed-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="5c1ed-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c1ed-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
