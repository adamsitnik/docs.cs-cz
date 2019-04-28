---
title: IAssemblyCacheItem::CreateStream – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380e248c8c4e3407fff868cdd9a5c63b63e50c69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697510"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="7d9a6-102">IAssemblyCacheItem::CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="7d9a6-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="7d9a6-103">Vytvoří datový proud se zadaným názvem a formát.</span><span class="sxs-lookup"><span data-stu-id="7d9a6-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d9a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d9a6-104">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="7d9a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d9a6-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="7d9a6-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="7d9a6-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="7d9a6-107">[in] Název datového proudu, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7d9a6-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="7d9a6-108">[in] Formát souboru, který má být datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="7d9a6-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="7d9a6-109">[in] Příznaky formátu konkrétní definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="7d9a6-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="7d9a6-110">[out] Ukazatel na adresu vráceného [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span><span class="sxs-lookup"><span data-stu-id="7d9a6-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="7d9a6-111">[in, volitelné] Maximální velikost datového proudu odkazuje `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="7d9a6-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d9a6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d9a6-112">Requirements</span></span>

<span data-ttu-id="7d9a6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d9a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="7d9a6-114">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7d9a6-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="7d9a6-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d9a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7d9a6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d9a6-116">See also</span></span>

- [<span data-ttu-id="7d9a6-117">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d9a6-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)