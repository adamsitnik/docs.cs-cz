---
title: RUNTIME_INFO_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9483cf8671b7d3ad5430081d93925af30b3d8368
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215682"
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="bba7b-102">RUNTIME_INFO_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="bba7b-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="bba7b-103">Obsahuje hodnoty, které označují, jaké informace o common language runtime (CLR) má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="bba7b-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bba7b-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="bba7b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="bba7b-105">Members</span></span>  
  
|<span data-ttu-id="bba7b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="bba7b-106">Member</span></span>|<span data-ttu-id="bba7b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bba7b-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="bba7b-108">Označuje, že informace o adresáři by neměl být zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="bba7b-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="bba7b-109">Označuje, že by neměl být zahrnuty informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="bba7b-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="bba7b-110">Určuje, že dialogové okno chyby by neměl být zobrazeny nebude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="bba7b-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="bba7b-111">Označuje, že efekty volání [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkce s příznakem SEM_FAILCRITICALERRORS by měla být potlačena.</span><span class="sxs-lookup"><span data-stu-id="bba7b-111">Indicates that the effects of calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="bba7b-112">To znamená dialogové okno instalace, které mají být zobrazeny po selhání, místo potlačeny.</span><span class="sxs-lookup"><span data-stu-id="bba7b-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="bba7b-113">Označuje žádost o informace o AMD-64kompatibilní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bba7b-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="bba7b-114">Označuje žádost o informace o IA-64kompatibilní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bba7b-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="bba7b-115">Označuje žádost o informace o x86 kompatibilní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bba7b-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="bba7b-116">Označuje, že informace o upgradu verze by měly být zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="bba7b-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bba7b-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bba7b-117">Remarks</span></span>  
 <span data-ttu-id="bba7b-118">Následující příznaky Architektura platformy může být zadaný jenom jeden po druhém a nelze kombinovat:</span><span class="sxs-lookup"><span data-stu-id="bba7b-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="bba7b-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="bba7b-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="bba7b-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="bba7b-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="bba7b-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="bba7b-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba7b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bba7b-122">Requirements</span></span>  
 <span data-ttu-id="bba7b-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bba7b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba7b-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bba7b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bba7b-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bba7b-125">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="bba7b-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bba7b-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bba7b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bba7b-127">See also</span></span>

- [<span data-ttu-id="bba7b-128">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="bba7b-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
