---
title: ISymUnmanagedWriter::DefineSequencePoints – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d3be88065d4f29020a794db30c616774db1f4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580847"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints – metoda
Definuje skupinu pořadí bodů v aktuální metodě. Každé počáteční řádek a počáteční sloupec definovat spuštění příkazu v rámci metody. Každý ukončení řádku a poslední sloupec definovat konec příkazu v rámci metody. Tato pole mají být řazeny ve vzestupném pořadí podle posunů. Posun je vždy prováděno od samého začátku metody v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `document`  
 [in] Objekt dokumentu, pro které jsou definovány body sekvence.  
  
 `spCount`  
 [in] A `ULONG32` , který označuje velikost jednotlivých `offsets`, `lines`, `columns`, `endLines`, a `endColumns` vyrovnávací paměti.  
  
 `offsets`  
 [in] Posun body sekvence měřená od začátku metody.  
  
 `lines`  
 [in] Počáteční řádek čísla body sekvence.  
  
 `columns`  
 [in] Počáteční sloupec čísla body sekvence.  
  
 `endLines`  
 [in] Koncového čísla řádku body sekvence. Tento parametr je volitelný.  
  
 `endColumns`  
 [in] Koncového čísla sloupce body sekvence. Tento parametr je volitelný.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
