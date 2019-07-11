---
title: ICLRStrongName::StrongNameSignatureVerification – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d269414346d8dcf4212fb5ee546cf22228cdd2b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765907"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="b0345-102">ICLRStrongName::StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="b0345-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="b0345-103">Získá hodnotu, která určuje, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu, který je ověřen podle zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="b0345-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0345-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0345-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0345-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0345-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b0345-106">[in] Cesta k přenositelný spustitelný (.dll nebo .exe) soubor pro sestavení k ověření.</span><span class="sxs-lookup"><span data-stu-id="b0345-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="b0345-107">[in] Příznaky, které upravují chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="b0345-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="b0345-108">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b0345-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="b0345-109">`SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je potřeba přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="b0345-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="b0345-110">`SN_INFLAG_INSTALL` (0x00000002) - určuje, že to je poprvé, kdy je ověřený v manifestu.</span><span class="sxs-lookup"><span data-stu-id="b0345-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="b0345-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="b0345-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="b0345-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - určuje, zda sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="b0345-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="b0345-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - určuje, že mezipaměť bude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="b0345-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="b0345-114">`SN_INFLAG_RUNTIME` (0x80000000) – vyhrazené pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="b0345-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="b0345-115">[out] Příznaky určující, zda se ověřit podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="b0345-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="b0345-116">Je podporován následující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="b0345-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="b0345-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota nastavená na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="b0345-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0345-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b0345-118">Return Value</span></span>  
 <span data-ttu-id="b0345-119">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="b0345-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0345-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0345-120">Requirements</span></span>  
 <span data-ttu-id="b0345-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0345-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0345-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b0345-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b0345-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0345-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0345-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0345-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0345-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0345-125">See also</span></span>

- [<span data-ttu-id="b0345-126">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="b0345-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="b0345-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0345-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
