---
title: ISymUnmanagedBinder2::GetReaderForFile2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db917820de92b2e347385afc5217c0ca190825cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776830"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 – metoda
Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní, které budou číst symboly ladění, které jsou spojené s modulem.  
  
 Tato metoda poskytuje rozsáhlejší vyhledejte soubor databáze (PDB) programu, než [isymunmanagedbinder::getreaderforfile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 [in] Ukazatel na rozhraní import metadat.  
  
 `fileName`  
 [in] Ukazatel na název souboru.  
  
 `searchPath`  
 [in] Ukazatel do cesty pro hledání.  
  
 `searchPolicy`  
 [in] Hodnota [corsymsearchpolicyattributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) výčet, který určuje zásady pro použití při vyhledávání pro modul pro načítání symbolů.  
  
 `pRetVal`  
 [out] Ukazatel, který je nastaven na vrácenou [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="remarks"></a>Poznámky  
 Tato verze metody můžete vyhledat soubor PDB v oblastech než vpravo vedle modulu. Hledání zásad se dá nastavit podle kombinace [corsymsearchpolicyattributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). Například `AllowReferencePathAccess | AllowSymbolServerAccess` hledá soubor PDB vedle spustitelný soubor a na serveru symbolů, ale ne registru nebo použijte cestu ve spustitelném souboru. Pokud `searchPath` parametr zadán, budou prohledány vždy tyto adresáře.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedBinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [GetReaderForFile – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
