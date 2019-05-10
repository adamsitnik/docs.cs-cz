---
title: 'Postupy: Zachycení výjimky nekompatibilní se specifikací CLS'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 27b36d85b2ece957c8ef3fce70a6fd794bb3d4e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595669"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Postupy: Zachycení výjimky nekompatibilní se specifikací CLS
Některé jazyky .NET, včetně C++vyhodnocovací, povolit objekty k vyvolání výjimky, které nejsou odvozeny od <xref:System.Exception>. Takové výjimky jsou volány *-kompatibilní se Specifikací výjimky* nebo *nejsou výjimkami*. V jazyce C# nelze vyvolat výjimky neodpovídající specifikaci CLS, ale je možné zachytit dvěma způsoby:  
  
- V rámci `catch (RuntimeWrappedException e)` bloku.
  
     Ve výchozím nastavení nastavení sestavení Visual C# zachytává výjimky neodpovídající specifikaci CLS jako zabalené výjimky. Tuto metodu použijte, pokud potřebujete přístup k původní výjimku, která je přístupná prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost. Postup dále v tomto tématu vysvětluje, jak zachytávat výjimky tímto způsobem.  
  
- V rámci obecný zachytávací blok (blok catch bez zadaný typ výjimky), který je umístit za všechny ostatní `catch` bloky.
  
     Tuto metodu použijte, pokud chcete provést určitou akci (jako je například zápis do souboru protokolu) v reakci na výjimky neodpovídající specifikaci CLS a nepotřebujete přístup k informacím o výjimce. Ve výchozím nastavení modul common language runtime zabalí všechny výjimky. Chcete-li toto chování zakázat, přidejte tento atribut úrovně sestavení kódu, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>K zachycení výjimky neodpovídající specifikaci CLS  
  
V rámci `catch(RuntimeWrappedException e)` blokovat, přístup k původní výjimky prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachytit výjimku kompilace neodpovídající specifikaci CLS, která byla vyvolána z knihovny tříd napsané v C++vyhodnocovací. Všimněte si, že v tomto příkladu kódu klienta jazyka C# pozná, předem, jestli je typ výjimky vyvolané <xref:System.String?displayProperty=nameWithType>. Můžete přetypovat <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost zpátky původního stavu, dokud tento typ je přístupný z vašeho kódu.  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)
