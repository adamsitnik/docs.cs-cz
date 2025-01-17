---
title: IMetaDataImport::GetParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9d2c74adecdfb0201f9f0c08998feba674f9e0f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778921"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps – metoda
Získá metadata hodnot pro parametr odkazuje zadaný ParamDef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] ParamDef token, který představuje parametr a vrátit metadata pro.  
  
 `pmd`  
 [out] Ukazatel na token MethodDef představující metodu, která přebírá parametr.  
  
 `pulSequence`  
 [out] Pořadové číslo pozice parametru v seznamu argumentů metody.  
  
 `szName`  
 [out] Vyrovnávací paměti, která bude uchovávat název parametru.  
  
 `cchName`  
 [in] Požadovaná velikost v širokých znaků `szName`.  
  
 `pchName`  
 [out] Velikost vrácené v širokých znaků `szName`.  
  
 `pdwAttr`  
 [out] Ukazatel na libovolný atribut příznaky spojené s parametrem. To je bitová maska z `CorParamAttr` hodnoty.  
  
 `pdwCPlusTypeFlag`  
 [out] Ukazatel na příznak určující, který je parametr <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Ukazatel na konstantní řetězec vrácený funkcí parametru.  
  
 `pcchValue`  
 [out] Velikost `ppValue` v široké znaky, nebo nula, pokud `ppValue` neobsahuje řetězec.  
  
## <a name="remarks"></a>Poznámky

Pořadí hodnot v `pulSequence` začínají znakem 1 pro parametry. Návratová hodnota má pořadové číslo 0.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
