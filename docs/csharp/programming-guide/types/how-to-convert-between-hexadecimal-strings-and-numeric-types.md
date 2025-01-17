---
title: 'Postupy: převod mezi hexadecimálními řetězci a číselnými typy C# – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: e5013891db827e27b3cda55135fff4ee287cfcb4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423134"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Postupy: Převod mezi hexadecimálními řetězci a číselnými typy (Průvodce programováním v C#)
Tyto příklady vám ukážou, jak provádět následující úlohy:  
  
- Získá hexadecimální hodnotu každého znaku v [řetězci](../../language-reference/builtin-types/reference-types.md).  
  
- Získejte [znak](../../language-reference/keywords/char.md) , který odpovídá každé hodnotě v šestnáctkovém řetězci.  
  
- Převeďte hexadecimální `string` na [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Převést hexadecimální `string` na typ [float](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Převeďte [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na hexadecimální `string`.  
  
## <a name="example"></a>Příklad  
 Tento příklad vypíše hexadecimální hodnotu každého znaku v `string`. Nejprve analyzuje `string` na pole znaků. Pak volá <xref:System.Convert.ToInt32%28System.Char%29> u každého znaku a získá tak číselnou hodnotu. Nakonec formátuje číslo jako šestnáctkové vyjádření v `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Příklad  
 Tento příklad analyzuje `string` hexadecimálních hodnot a vypíše znak odpovídající každé hexadecimální hodnotě. Nejprve volá metodu [Split (Char\[\])](xref:System.String.Split(System.Char[])) k získání každé hexadecimální hodnoty jako jednotlivé `string` v poli. Poté volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> pro převod hexadecimální hodnoty na desítkovou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby získání znaku odpovídajícího kódu znaku. První technika používá <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, která vrací znak odpovídající celočíselnému argumentu jako `string`. Druhá technika je explicitně přetypování `int` na [znak](../../language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje jiný způsob, jak převést šestnáctkovou `string` na celé číslo, voláním metody <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést šestnáctkovou `string` na typ [float](../../language-reference/builtin-types/floating-point-numeric-types.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy a metody <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na šestnáctkový řetězec pomocí třídy <xref:System.BitConverter?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
