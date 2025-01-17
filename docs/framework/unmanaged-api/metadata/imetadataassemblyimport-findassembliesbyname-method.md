---
title: IMetaDataAssemblyImport::FindAssembliesByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 315d9aa6f7db51342e71ba3f8fcdc091f7707743
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777977"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName – metoda
Získává pole sestavení se zadaným `szAssemblyName` parametr pomocí standardních pravidel použijí modulem common language runtime (CLR) k vyřešení odkazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szAppBase`  
 [in] Kořenový adresář, do kterého chcete vyhledat dané sestavení. Pokud tato hodnota nastavená na `null`, `FindAssembliesByName` bude vypadat pouze v globální mezipaměti sestavení pro sestavení.  
  
 `szPrivateBin`  
 [in] Seznam oddělený středníkem podadresáře (například "bin; bin2"), v kořenovém adresáři, ve kterém chcete hledat sestavení. Tyto adresáře jsou vystavovány kromě platformám zadaným v výchozí pravidla zjišťování.  
  
 `szAssemblyName`  
 [in] Název sestavení k vyhledání. Formát tohoto řetězce je definována na referenční stránce třídy pro <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Pole typu [IUnknown](/cpp/atl/iunknown) ve které chcete umístit `IMetadataAssemblyImport` ukazatele rozhraní.  
  
 `cMax`  
 [out] Maximální počet ukazatele rozhraní, které mohou být umístěny v `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Číslo vrácen ukazatele rozhraní. To znamená, počet ukazatelů rozhraní skutečně umístit v `ppIUnk`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádná sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Název sestavení, `FindAssembliesByName` metoda vyhledá sestavení pomocí následujících standardní pravidla pro překlad odkazy na sestavení. (Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volajícímu nakonfigurovat různé aspekty kontextu překladač sestavení, jako je například základní a privátní vyhledávací cestu aplikace.  
  
 `FindAssembliesByName` Metoda vyžaduje CLR v procesu inicializovat, aby bylo možné vyvolávajícími logiku sestavení řešení. Proto je nutné volat [coinitializeee –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání COINITEE_DEFAULT) před voláním `FindAssembliesByName`a pak postupujte podle voláním [couninitializecor –](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` Vrátí [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ukazatel na soubor obsahující manifest sestavení pro název sestavení, které je předáno. Pokud daný název sestavení není zadán úplně (například, pokud neobsahuje verzi), může být vrácena více sestavení.  
  
 `FindAssembliesByName` běžně používá kompilátor, který se pokusí najít odkazované sestavení v době kompilace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Jak běhové prostředí vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
