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
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="5e431-102">Postupy: Zachycení výjimky nekompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="5e431-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="5e431-103">Některé jazyky .NET, včetně C++vyhodnocovací, povolit objekty k vyvolání výjimky, které nejsou odvozeny od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="5e431-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="5e431-104">Takové výjimky jsou volány *-kompatibilní se Specifikací výjimky* nebo *nejsou výjimkami*.</span><span class="sxs-lookup"><span data-stu-id="5e431-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="5e431-105">V jazyce C# nelze vyvolat výjimky neodpovídající specifikaci CLS, ale je možné zachytit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="5e431-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="5e431-106">V rámci `catch (RuntimeWrappedException e)` bloku.</span><span class="sxs-lookup"><span data-stu-id="5e431-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="5e431-107">Ve výchozím nastavení nastavení sestavení Visual C# zachytává výjimky neodpovídající specifikaci CLS jako zabalené výjimky.</span><span class="sxs-lookup"><span data-stu-id="5e431-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="5e431-108">Tuto metodu použijte, pokud potřebujete přístup k původní výjimku, která je přístupná prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5e431-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5e431-109">Postup dále v tomto tématu vysvětluje, jak zachytávat výjimky tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="5e431-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="5e431-110">V rámci obecný zachytávací blok (blok catch bez zadaný typ výjimky), který je umístit za všechny ostatní `catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="5e431-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="5e431-111">Tuto metodu použijte, pokud chcete provést určitou akci (jako je například zápis do souboru protokolu) v reakci na výjimky neodpovídající specifikaci CLS a nepotřebujete přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="5e431-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="5e431-112">Ve výchozím nastavení modul common language runtime zabalí všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="5e431-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="5e431-113">Chcete-li toto chování zakázat, přidejte tento atribut úrovně sestavení kódu, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="5e431-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="5e431-114">K zachycení výjimky neodpovídající specifikaci CLS</span><span class="sxs-lookup"><span data-stu-id="5e431-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="5e431-115">V rámci `catch(RuntimeWrappedException e)` blokovat, přístup k původní výjimky prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5e431-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e431-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e431-116">Example</span></span>  
 <span data-ttu-id="5e431-117">Následující příklad ukazuje, jak zachytit výjimku kompilace neodpovídající specifikaci CLS, která byla vyvolána z knihovny tříd napsané v C++vyhodnocovací.</span><span class="sxs-lookup"><span data-stu-id="5e431-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="5e431-118">Všimněte si, že v tomto příkladu kódu klienta jazyka C# pozná, předem, jestli je typ výjimky vyvolané <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e431-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5e431-119">Můžete přetypovat <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost zpátky původního stavu, dokud tento typ je přístupný z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="5e431-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e431-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e431-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="5e431-121">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="5e431-121">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
