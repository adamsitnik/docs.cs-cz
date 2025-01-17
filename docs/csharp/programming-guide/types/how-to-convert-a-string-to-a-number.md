---
title: 'Postupy: převod řetězce na číslo- C# programový průvodce'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: c39602afbece4faaf6599a5c76f5746defffe03a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417636"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Postupy: Převedení řetězce na číslo (Průvodce programováním v C#)

Můžete převést [řetězec](../../language-reference/builtin-types/reference-types.md) na číslo voláním metody `Parse` nebo `TryParse`, která se nachází na různých číselných typech (`int`, `long`, `double`atd.), nebo pomocí metod ve třídě <xref:System.Convert?displayProperty=nameWithType>.  
  
 Pokud máte řetězec, je poněkud efektivnější a jednoduše zavolejte metodu `TryParse` (například [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) nebo metodu `Parse` (například [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).  Použití metody <xref:System.Convert> je užitečnější pro obecné objekty, které implementují <xref:System.IConvertible>.  
  
 Můžete použít metody `Parse` nebo `TryParse` na číselném typu, který řetězec obsahuje, například typ <xref:System.Int32?displayProperty=nameWithType>.  Metoda <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> používá <xref:System.Int32.Parse%2A> interně.  Metoda `Parse` vrátí převedený počet; Metoda `TryParse` vrací hodnotu <xref:System.Boolean>, která označuje, zda byl převod úspěšný, a vrátí převedený počet v [parametru`out`](../../language-reference/keywords/out.md). Pokud řetězec nemá platný formát, `Parse` vyvolá výjimku, zatímco `TryParse` vrátí [false](../../language-reference/keywords/false-literal.md). Při volání metody `Parse` byste měli vždy použít zpracování výjimek k zachycení <xref:System.FormatException> v případě, že operace analýzy neproběhne úspěšně.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Volání metod Parse a TryParse

Metody `Parse` a `TryParse` ignorují prázdné znaky na začátku a na konci řetězce, ale všechny ostatní znaky musí být znaky, které tvoří příslušný číselný typ (`int`, `long`, `ulong`, `float`, `decimal`atd.).  Jakékoli prázdné místo v řetězci, které tvoří číslo, způsobí chybu.  Můžete například použít `decimal.TryParse` k analýze "10", "10,3" nebo "10", ale tuto metodu nelze použít k analýze 10 z "10X", "1 0" (Všimněte si vloženého prostoru), "10 .3" (poznámení s vloženým prostorem), "10E1" (`float.TryParse` funguje zde) a tak dále. Kromě toho řetězec, jehož hodnota je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, se nepodařilo úspěšně analyzovat. Před pokusem o jeho analýzu můžete vyhledat voláním metody <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> a zadat hodnotu null nebo prázdný řetězec. 

Následující příklad ukazuje úspěšné i neúspěšné volání `Parse` a `TryParse`.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Následující příklad ilustruje jeden z přístupů k analýze řetězce, který by měl obsahovat úvodní číselné znaky (včetně hexadecimálních znaků) a koncových znaků, které nejsou číselné. Před voláním metody <xref:System.Int32.TryParse%2A> přiřadí platné znaky od začátku řetězce k novému řetězci. Vzhledem k tomu, že řetězce, které mají být analyzovány, obsahují malý počet znaků, příklad volá metodu <xref:System.String.Concat%2A?displayProperty=nameWithType> pro přiřazení platných znaků novému řetězci. Pro větší řetězec lze místo toho použít třídu <xref:System.Text.StringBuilder>. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Volání metod Convert

V následující tabulce jsou uvedeny některé z metod <xref:System.Convert> třídy, které lze použít k převodu řetězce na číslo.  
  
|Číselný typ|Metoda|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 Následující příklad volá metodu <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> pro převod vstupního řetězce na typ [int](../../language-reference/builtin-types/integral-numeric-types.md). Příklad zachytí dvě nejběžnější výjimky, které mohou být vyvolány touto metodou, <xref:System.FormatException> a <xref:System.OverflowException>. Pokud je možné výsledné číslo zvýšit bez překročení <xref:System.Int32.MaxValue?displayProperty=nameWithType>, příklad přidá 1 k výsledku a zobrazí výstup.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Typy](./index.md)
- [Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Ukázka: nástroj formátování WinForms pro .NET CoreC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
