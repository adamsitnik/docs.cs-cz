---
title: LoadLibraryShim – funkce
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03bc5584d24efa790989f93426251f9f38e65904
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768533"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim – funkce
Načte zadanou verzi knihovny DLL, která je součástí Distribuovatelný balíček rozhraní .NET Framework.  
  
 Tato funkce se již nepoužívá v rozhraní .NET Framework 4. Použití [iclrruntimeinfo::LoadLibrary –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDllName`  
 [in] Ukončit nulou řetězec představující název knihovny DLL, který se má načíst z knihovny rozhraní .NET Framework.  
  
 `szVersion`  
 [in] Ukončit nulou řetězec, který představuje verzi knihovny DLL, který se má načíst. Pokud `szVersion` je null, verze vybrali pro načítání je nejnovější verzi určenou knihovnu DLL, která je nižší než verze 4. To znamená, jsou ignorovány všechny verze roven nebo větší než verze 4, pokud `szVersion` má hodnotu null, a pokud je nainstalována žádná verze a menší než verze 4, se nepodaří načíst knihovnu DLL. Tím je zajištěno, že instalace rozhraní .NET Framework 4 nemá vliv na existující aplikace nebo komponenty. Viz položka [SxS InProc a migrace s rychlým startem](https://go.microsoft.com/fwlink/?LinkId=200329) na blogu týmu CLR.  
  
 `pvReserved`  
 Vyhrazeno pro budoucí použití.  
  
 `phModDll`  
 [out] Ukazatel na popisovač modulu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|CLR_E_SHIM_RUNTIMELOAD|Načítání `szDllName` vyžaduje načítání common language runtime (CLR) a potřebnou verzi modulu CLR nelze načíst.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce slouží k načtení knihovny DLL, které jsou součástí Distribuovatelný balíček rozhraní .NET Framework. Tato možnost nenačte uživatelem generovaný knihovny DLL.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework verze 2.0, načítají se soubor Fusion.dll způsobí, že modul CLR, který se má načíst. Je to proto, že funkce v soubor Fusion.dll jsou nyní obálky, jehož implementace jsou k dispozici v modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
