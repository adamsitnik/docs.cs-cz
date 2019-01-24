---
title: 'Postupy: Ruční vytváření obálek'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fba0de3f45afc199255dce93e69142724b68b0fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553032"
---
# <a name="how-to-create-wrappers-manually"></a>Postupy: Ruční vytváření obálek
Rozhodnete-li se deklarovat typy modelu COM ve spravovaném zdrojovém kódu ručně, bude nejlépe, když začnete se stávajícím souborem IDL (Interface Definition Language) nebo knihovnou typů. Nemáte-li k dispozici soubor IDL nebo nelze vygenerovat soubor knihovny typů, můžete typy modelu COM nasimulovat pomocí spravovaných deklarací a exportováním výsledného sestavení do knihovny typů.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>Simulace typů modelu COM ze spravovaného prostředku  
  
1.  Deklarujte typy v jazyce, který je kompatibilní se specifikací CLS (Common Language Specification), a soubor zkompilujte.  
  
2.  Exportujte sestavení obsahující typy pomocí [Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
3.  Exportovanou knihovnu typů modelu COM použijte jako základ pro deklaraci spravovaných typů orientovaných na model COM.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Vytvoření obálky volatelné za běhu (RCW)  
  
1.  Za předpokladu, že máte soubor IDL nebo soubor knihovny typů, se rozhodněte, které třídy a rozhraní budou zahrnuty do uživatelského objektu RCW. Je možné vyloučit jakékoli typy, které nechcete přímo nebo nepřímo použít v aplikaci.  
  
2.  Vytvořte zdrojový soubor v jazyce, který odpovídá specifikaci CLS a deklarujte typy. Zobrazit [sestavení souhrn převodu knihovny typů na](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)) úplný popis procesu převodu při importování. Efektivně, když vytváříte vlastní objekt RCW, provádíte ruční převod aktivity typu poskytovaných [Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Příklad v následující části zobrazuje typy v souboru IDL nebo souboru knihovny typů a odpovídající typy v kódu jazyka C#.  
  
3.  Po dokončení vytváření deklarací zkompilujte soubor jako jakýkoli jiný spravovaný zdrojový kód.  
  
4.  Stejně jako v případě typů, které jsou importovány pomocí nástroje Tlbimp.exe, vyžadují některé z nich dodatečné informace, které lze přidat přímo do kódu. Podrobnosti najdete v tématu [jak: Úprava sestavení vzájemné spolupráce](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující kód znázorňuje příklad rozhraní `ISATest` a třídy `SATest` v souboru IDL a odpovídající typy ve zdrojovém kódu jazyka C#.  
  
 **Soubor IDL nebo typ knihovny**  
  
```  
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]   
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 **Obálka ve spravovaném zdrojovém kódu**  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }   
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,   
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,   
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a>Viz také:
- [Přizpůsobení obálek Volatelných za běhu](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))
- [Datové typy COM](https://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061(v=vs.100))
- [Postupy: Úprava sestavení vzájemné spolupráce](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100))
- [Souhrn převodu sestavení knihovny typů na](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))
- [Tlbimp.exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportér knihovny typů)](../tools/tlbexp-exe-type-library-exporter.md)
