---
title: ImportFile – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7fee7a91de99e2db69609cbc7c73e22d85d045f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777072"
---
# <a name="importfile-method"></a><span data-ttu-id="8ac6b-102">ImportFile – metoda</span><span class="sxs-lookup"><span data-stu-id="8ac6b-102">ImportFile Method</span></span>
<span data-ttu-id="8ac6b-103">Importuje sestavení a nevázané moduly.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ac6b-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ac6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ac6b-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="8ac6b-106">Plně kvalifikovaný název souboru, který se má importovat</span><span class="sxs-lookup"><span data-stu-id="8ac6b-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="8ac6b-107">Volitelný název výstupního souboru, který lze použít k přejmenování souboru, protože je propojen do sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="8ac6b-108">Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="8ac6b-109">Ukazatel na token, kde bude uložen jedinečný identifikátor souboru.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="8ac6b-110">Soubor může být sestavením nebo souborem.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="8ac6b-111">Přijme ukazatel na [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8ac6b-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="8ac6b-112">Pokud soubor není sestavením, může mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="8ac6b-113">Ukazatel na počet souborů nebo rozsahů, které byly naimportovány.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ac6b-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8ac6b-114">Return Value</span></span>  
 <span data-ttu-id="8ac6b-115">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac6b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ac6b-116">Requirements</span></span>  
 <span data-ttu-id="8ac6b-117">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="8ac6b-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac6b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ac6b-118">See also</span></span>

- [<span data-ttu-id="8ac6b-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ac6b-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8ac6b-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ac6b-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8ac6b-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8ac6b-121">ALink API</span></span>](index.md)
