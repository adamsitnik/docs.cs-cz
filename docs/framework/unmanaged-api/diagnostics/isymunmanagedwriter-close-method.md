---
title: ISymUnmanagedWriter::Close – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd7131c55f9c06a8fcfc0cad859c18e410169c78
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778205"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close – metoda
Po potvrzení symbolů do úložiště symbolů zavře zapisovač symbol.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Po tomto volání zapisovač symbol stává neplatným další aktualizace. Zapisovač symbol okno zavřít bez potvrzení symboly, použijte [isymunmanagedwriter::Abort –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metoda místo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
