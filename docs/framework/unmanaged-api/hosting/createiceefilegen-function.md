---
title: CreateICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57163ccfcc6dff343a8bbc7d63564ae6b57b5ff6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490500"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="25433-102">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="25433-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="25433-103">Vytvoří [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="25433-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="25433-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="25433-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25433-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25433-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25433-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="25433-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="25433-107">[out] Ukazatel na novou adresu `ICeeFileGen` objektu.</span><span class="sxs-lookup"><span data-stu-id="25433-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25433-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="25433-108">Return Value</span></span>  
 <span data-ttu-id="25433-109">Tato metoda vrací standardní kódy chyb COM.</span><span class="sxs-lookup"><span data-stu-id="25433-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25433-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25433-110">Remarks</span></span>  
 <span data-ttu-id="25433-111">`ICeeFileGen` Objektu se používá k vytvoření common language runtime (CLR) souborů (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="25433-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="25433-112">Volání [destroyiceefilegen –](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) funkce zrušení `ICeeFileGen` objekt po dokončení.</span><span class="sxs-lookup"><span data-stu-id="25433-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25433-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25433-113">Requirements</span></span>  
 <span data-ttu-id="25433-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25433-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25433-115">**Záhlaví:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="25433-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="25433-116">**Knihovna:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="25433-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="25433-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25433-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25433-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25433-118">See also</span></span>

- [<span data-ttu-id="25433-119">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="25433-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
