---
title: extern – modifikátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: d860f1a3c6917238a529093672dc5f2abc5ae066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620189"
---
# <a name="extern-c-reference"></a><span data-ttu-id="e0983-102">extern (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e0983-102">extern (C# Reference)</span></span>

<span data-ttu-id="e0983-103">`extern` Modifikátor se používá k deklaraci metody, která je implementována externě.</span><span class="sxs-lookup"><span data-stu-id="e0983-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="e0983-104">Běžně `extern` modifikátor se `DllImport` atribut, pokud používáte služby Interop pro volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e0983-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="e0983-105">V takovém případě metoda musí být deklarovány také jako `static`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e0983-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="e0983-106">`extern` – Klíčové slovo lze také definovat alias externího sestavení, který umožňuje odkazovat na různé verze stejné součásti v rámci jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0983-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="e0983-107">Další informace najdete v tématu [externí alias](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="e0983-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="e0983-108">Jedná se o chybu používat [abstraktní](abstract.md) a `extern` modifikátory pro změny stejného členu.</span><span class="sxs-lookup"><span data-stu-id="e0983-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="e0983-109">Použití `extern` modifikátor znamená, že je metoda implementována mimo kód jazyka C#, zatímco použití `abstract` modifikátor znamená, že implementace metody není k dispozici ve třídě.</span><span class="sxs-lookup"><span data-stu-id="e0983-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="e0983-110">Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="e0983-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="e0983-111">Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="e0983-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="e0983-112">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="e0983-112">Example 1</span></span>

<span data-ttu-id="e0983-113">V tomto příkladu program přijme od uživatele řetězec a zobrazí ho v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e0983-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="e0983-114">Program používá `MessageBox` metoda naimportované z knihovny User32.dll.</span><span class="sxs-lookup"><span data-stu-id="e0983-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="e0983-115">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="e0983-115">Example 2</span></span>

<span data-ttu-id="e0983-116">Tento příklad znázorňuje program C#, který volá knihovnu jazyka C (nativní knihovnu DLL).</span><span class="sxs-lookup"><span data-stu-id="e0983-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="e0983-117">Vytvořte následující soubor C s názvem `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="e0983-117">Create the following C file and name it `cmdll.c`:</span></span>

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. <span data-ttu-id="e0983-118">Otevřete okno příkazového řádku nativních nástrojů x64 (nebo x32) sady Visual Studio z adresáře instalace sady Visual Studio a zkompilovat `cmdll.c` souboru tak, že zadáte **cl -LD cmdll.c** příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e0983-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="e0983-119">Ve stejném adresáři vytvořte následující soubor C# a pojmenujte ho `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="e0983-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

```csharp
// cm.cs
using System;
using System.Runtime.InteropServices;
public class MainClass
{
    [DllImport("Cmdll.dll")]
      public static extern int SampleMethod(int x);

    static void Main()
    {
        Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
    }
}
```

4. <span data-ttu-id="e0983-120">Otevřete okno příkazového řádku nativních nástrojů x64 (nebo x32) sady Visual Studio z adresáře instalace sady Visual Studio a zkompilovat `cm.cs` souboru tak, že zadáte:</span><span class="sxs-lookup"><span data-stu-id="e0983-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

> <span data-ttu-id="e0983-121">**CSC cm.cs** (pro x64 příkazového řádku) – nebo – **csc-platform: x 86 cm.cs** (pro x32 příkazového řádku)</span><span class="sxs-lookup"><span data-stu-id="e0983-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

<span data-ttu-id="e0983-122">Tím se vytvoří spustitelný soubor `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="e0983-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="e0983-123">Spusťte `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="e0983-123">Run `cm.exe`.</span></span> <span data-ttu-id="e0983-124">`SampleMethod` Metoda předává hodnota 5 souboru knihovny DLL, která vrací hodnotu vynásobenou 10.</span><span class="sxs-lookup"><span data-stu-id="e0983-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="e0983-125">Program vygeneruje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e0983-125">The program produces the following output:</span></span>

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a><span data-ttu-id="e0983-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0983-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e0983-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0983-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="e0983-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0983-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0983-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e0983-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0983-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0983-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e0983-131">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="e0983-131">Modifiers</span></span>](modifiers.md)
