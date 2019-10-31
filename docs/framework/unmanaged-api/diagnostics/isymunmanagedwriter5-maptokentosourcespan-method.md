---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 876804e7b825443116b1f44a02a685a73153915c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121628"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="05715-102">ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="05715-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="05715-103">Mapuje daný token metadat na zadaný rozsah řádku zdroje v zadaném zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="05715-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="05715-104">Musí být volána mezi voláním [metody openmaptokenstosourcespans –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [metodou closemaptokenstosourcespans –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="05715-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05715-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05715-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05715-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="05715-106">Parameters</span></span>  
  
|<span data-ttu-id="05715-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="05715-107">Parameter</span></span>|<span data-ttu-id="05715-108">Popis</span><span class="sxs-lookup"><span data-stu-id="05715-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="05715-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05715-109">Return Value</span></span>  
 <span data-ttu-id="05715-110">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="05715-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05715-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05715-111">Requirements</span></span>  
 <span data-ttu-id="05715-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="05715-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05715-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05715-113">See also</span></span>

- [<span data-ttu-id="05715-114">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05715-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
