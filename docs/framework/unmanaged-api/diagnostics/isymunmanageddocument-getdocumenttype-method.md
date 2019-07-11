---
title: ISymUnmanagedDocument::GetDocumentType – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ae3575b759d8b6191f0b5e5cd557a6f6e56323fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776737"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="69dcc-102">ISymUnmanagedDocument::GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="69dcc-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="69dcc-103">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="69dcc-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69dcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69dcc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69dcc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69dcc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="69dcc-106">[out] Ukazovat na proměnnou, která přijímá typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="69dcc-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69dcc-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="69dcc-107">Return Value</span></span>  
 <span data-ttu-id="69dcc-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="69dcc-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69dcc-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69dcc-109">See also</span></span>

- [<span data-ttu-id="69dcc-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69dcc-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
