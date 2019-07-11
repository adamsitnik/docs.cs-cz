---
title: ICLRStrongName::GetHashFromFileW – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a5b5eb587a4739cf3481c76ef73ebc62f0a9d20
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748165"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="03cea-102">ICLRStrongName::GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="03cea-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="03cea-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězce v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="03cea-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03cea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03cea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="03cea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03cea-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="03cea-106">[in] Kódování Unicode název souboru, který má hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="03cea-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="03cea-107">[out v] Algoritmus použitého při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="03cea-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="03cea-108">Platné algoritmy jsou těmi definovanými ve Win32 rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="03cea-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="03cea-109">Pokud `piHashAlg` je nastavena na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="03cea-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="03cea-110">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="03cea-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="03cea-111">[in] Maximální velikost vyrovnávací paměti, na které odkazuje `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="03cea-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="03cea-112">[out] Velikost v bajtech, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="03cea-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03cea-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03cea-113">Return Value</span></span>  
 <span data-ttu-id="03cea-114">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="03cea-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03cea-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03cea-115">Remarks</span></span>  
 <span data-ttu-id="03cea-116">Tato metoda je stejné jako [iclrstrongname::gethashfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metody, s tím rozdílem, že specifikace název souboru je Unicode místo ANSI.</span><span class="sxs-lookup"><span data-stu-id="03cea-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03cea-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03cea-117">Requirements</span></span>  
 <span data-ttu-id="03cea-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03cea-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03cea-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="03cea-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03cea-120">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03cea-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03cea-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03cea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03cea-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03cea-122">See also</span></span>

- [<span data-ttu-id="03cea-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="03cea-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="03cea-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03cea-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
