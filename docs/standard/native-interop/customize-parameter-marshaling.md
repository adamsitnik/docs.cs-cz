---
title: Přizpůsobení parametrů zařazování – .NET
description: Zjistěte, jak přizpůsobit, jak .NET zařazuje parametry nativní reprezentace.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 877eb00c18c9108fe6bcfb50104ff5ed813e85f3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065468"
---
# <a name="customizing-parameter-marshaling"></a>Přizpůsobení zařazování parametru

Pokud modul .NET runtime výchozí chování zařazování parametru neumí, co chcete, můžete použít použití <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atribut přizpůsobit, jak zařadit parametry.

## <a name="customizing-string-parameters"></a>Přizpůsobení parametrů řetězce

.NET nabízí různé formáty pro zařazování řetězce. Tyto metody jsou rozděleny do různých částí na řetězce ve stylu jazyka C a zaměřené na Windows formáty řetězců.

### <a name="c-style-strings"></a>Řetězce ve stylu jazyka C

Každá z těchto formátů předá řetězec zakončený hodnotou null do nativního kódu. Se liší podle kódování nativního řetězce.

| `System.Runtime.InteropServices.UnmanagedType` Hodnota | Kódování |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 | 
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> Formát se mírně liší. Stejně jako `LPWStr`, zařazuje řetězec, který má nativní C-style řetězec zakódovaný ve formátu UTF-16. Ale spravovaný podpis má předat do řetězce podle odkazu a odpovídající nativní podpis přebírá řetězec podle hodnoty. Toto rozlišení umožňuje používat nativní rozhraní API, které přijímá řetězec podle hodnoty a změní ho místně bez nutnosti použití `StringBuilder`. Nedoporučujeme ručně pomocí tohoto formátu, protože je náchylný k záměně se podpisy neshodují nativní a spravované.

### <a name="windows-centric-string-formats"></a>Formáty řetězce zaměřené na Windows

Při interakci s rozhraními COM nebo OLE, pravděpodobně zjistíte, že nativní funkce přijímají řetězce jako `BSTR` argumenty. Můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> nespravovaného typu řetězec jako `BSTR`.

Pokud jste při interakci s rozhraními API WinRT, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> formát zařazování řetězce jako `HSTRING`.

## <a name="customizing-array-parameters"></a>Přizpůsobení pole parametrů

.NET také poskytuje několik způsobů zařazování pole parametrů. Pokud voláte rozhraní API, která přijímá pole stylu C, použijte <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> nespravovaného typu. Pokud hodnoty v poli potřebovat vlastní zařazování, můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> pole na `[MarshalAs]` atribut, který.

Pokud používáte rozhraní API modelu COM, bude pravděpodobně nutné zařazení parametry pole jako `SAFEARRAY*`s. Uděláte to tak, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> nespravovaného typu. Výchozí typ elementů `SAFEARRAY` můžete zobrazit v tabulce na [přizpůsobení `object` pole](./customize-struct-marshaling.md#marshaling-systemobjects). Můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> polí pro přizpůsobení elementu přesný typ `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Přizpůsobení parametrů logická nebo desetinné číslo

Informace o zařazování parametry logická nebo desetinné číslo, naleznete v tématu [přizpůsobení struktura zařazování](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Přizpůsobení parametry objektu (jen Windows)

Modul runtime rozhraní .NET na Windows, poskytuje několik různých způsobů, jak zařadit parametry objektu do nativního kódu.

### <a name="marshaling-as-specific-com-interfaces"></a>Zařazování jako konkrétní rozhraní modelu COM

Pokud vaše rozhraní API bere ukazatel na objekt modelu COM, můžete použít některý z následujících `UnmanagedType` formáty na `object`-zadali parametr předat jako tato konkrétní rozhraní .NET:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Kromě toho pokud váš typ je označen `[ComVisible(true)]` nebo při zařazování `object` typ, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> formát zařazování objektu jako obálka volatelná aplikacemi COM pro zobrazení modelu COM typu.

### <a name="marshaling-to-a-variant"></a>Zařazování do `VARIANT`

Pokud vaše nativní rozhraní API trvá Win32 `VARIANT`, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> formátovat při vaší `object` parametr k zařazování objekty jako `VARIANT`s. Naleznete v dokumentaci [přizpůsobení `object` pole](customize-struct-marshaling.md#marshaling-systemobjects) pro mapování mezi typy rozhraní .NET a `VARIANT` typy.

### <a name="custom-marshalers"></a>Vlastní zařazování

Pokud chcete projekt nativní rozhraní modelu COM do různých spravovaného typu, můžete použít `UnmanagedType.CustomMarshaler` formátu a implementaci <xref:System.Runtime.InteropServices.ICustomMarshaler> poskytnout vlastní zařazování kód.
