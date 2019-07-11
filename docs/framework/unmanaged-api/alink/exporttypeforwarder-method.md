---
title: ExportTypeForwarder – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f97f46595f43c7576c499c6b9944f7e3509662fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742002"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="02542-102">ExportTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="02542-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="02542-103">Předávání typů přidá do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="02542-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02542-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02542-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="02542-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02542-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="02542-106">Odkaz na sestavení, na který odkazuje předávání typů.</span><span class="sxs-lookup"><span data-stu-id="02542-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="02542-107">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="02542-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="02542-108">`ComType` označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="02542-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="02542-109">Tato hodnota může být předán [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="02542-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="02542-110">Přijme token exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="02542-110">Receives the token of the exported type.</span></span> <span data-ttu-id="02542-111">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="02542-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02542-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="02542-112">Return Value</span></span>  
 <span data-ttu-id="02542-113">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="02542-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02542-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02542-114">Requirements</span></span>  
 <span data-ttu-id="02542-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="02542-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02542-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02542-116">See also</span></span>

- [<span data-ttu-id="02542-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02542-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="02542-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02542-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="02542-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="02542-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
