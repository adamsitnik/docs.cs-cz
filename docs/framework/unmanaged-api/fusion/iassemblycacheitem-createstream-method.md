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
ms.openlocfilehash: 5af7dc4e1694b66fc4a5ce37e515c71e9fa3db49
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796741"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream – metoda

Vytvoří datový proud se zadaným názvem a formátem.

## <a name="syntax"></a>Syntaxe

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

## <a name="parameters"></a>Parametry

`dwFlags`\
pro Příznaky definované v Fusion. idl

`pszStreamName`\
pro Název streamu, který se má vytvořit

`dwFormat`\
pro Formát souboru, který se má streamovat

`dwFormatFlags`\
pro Příznaky specifické pro formát definované v Fusion. idl.

`ppIStream`\
mimo Ukazatel na adresu vrácené instance [IStream](/windows/desktop/api/objidl/nn-objidl-istream) .

`puliMaxSize`\
[in, volitelné] Maximální velikost datového proudu, na který odkazuje `ppIStream`.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** Fusion. h

**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IAssemblyCacheItem – rozhraní](iassemblycacheitem-interface.md)
