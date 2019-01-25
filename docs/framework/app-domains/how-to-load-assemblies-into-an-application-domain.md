---
title: 'Postupy: Načtení sestavení do domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6b816c3a2c4f684993117deb38b40f4436a627c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653798"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="55a50-102">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="55a50-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="55a50-103">Existuje několik způsobů, jak načíst sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="55a50-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="55a50-104">Doporučeným způsobem je použít `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.Load%2A> metodu <xref:System.Reflection.Assembly?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="55a50-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="55a50-105">Další způsoby, které lze načíst sestavení patří:</span><span class="sxs-lookup"><span data-stu-id="55a50-105">Other ways assemblies can be loaded include:</span></span>  
  
-   <span data-ttu-id="55a50-106"><xref:System.Reflection.Assembly.LoadFrom%2A> Metodu <xref:System.Reflection.Assembly> třídy načte sestavení zadané umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="55a50-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="55a50-107">Načtení sestavení se tato metoda používá různé zatížení kontext.</span><span class="sxs-lookup"><span data-stu-id="55a50-107">Loading assemblies with this method uses a different load context.</span></span>  
  
-   <span data-ttu-id="55a50-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody načtení sestavení do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="55a50-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="55a50-109">Sestavení zavedených v tomto kontextu můžete prověřit, ale nebyl proveden, umožňující zkoumání sestavení, které se zaměřují na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="55a50-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="55a50-110">Zobrazit [jak: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="55a50-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55a50-111">Kontextu pouze pro reflexi je v rozhraní .NET Framework verze 2.0 nová.</span><span class="sxs-lookup"><span data-stu-id="55a50-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
-   <span data-ttu-id="55a50-112">Metody jako <xref:System.AppDomain.CreateInstance%2A> a <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> z <xref:System.AppDomain> třídy lze načíst sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="55a50-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
-   <span data-ttu-id="55a50-113"><xref:System.Type.GetType%2A> Metodu <xref:System.Type> třídy lze načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="55a50-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
-   <span data-ttu-id="55a50-114"><xref:System.AppDomain.Load%2A> Metodu <xref:System.AppDomain?displayProperty=nameWithType> třídy lze načíst sestavení, ale používá se především pro interoperabilitu COM.</span><span class="sxs-lookup"><span data-stu-id="55a50-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="55a50-115">Není vhodné používat k načtení sestavení do domény aplikace, ze kterého se označuje jako domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="55a50-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55a50-116">Od verze rozhraní .NET Framework verze 2.0, nenačte modul runtime, který byl zkompilován s verzí rozhraní .NET Framework, která má vyšší číslo verze než aktuálně zavedený modul runtime sestavení.</span><span class="sxs-lookup"><span data-stu-id="55a50-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="55a50-117">To platí pro kombinaci hlavní a vedlejší součásti číslo verze.</span><span class="sxs-lookup"><span data-stu-id="55a50-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="55a50-118">Můžete zadat tak, jak just-in-time (JIT) kompilaci kódu z načtených sestavení jsou sdílena mezi doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="55a50-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="55a50-119">Další informace najdete v tématu [doménám a sestavením aplikací](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).</span><span class="sxs-lookup"><span data-stu-id="55a50-119">For more information, see [Application Domains and Assemblies](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55a50-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="55a50-120">Example</span></span>  
 <span data-ttu-id="55a50-121">Následující kód načte sestavení do aktuální domény aplikace s názvem "example.exe" nebo "example.dll" získá typ s názvem `Example` ze sestavení, získá konstruktor bez parametrů metodu s názvem `MethodA` u tohoto typu a provede metodu.</span><span class="sxs-lookup"><span data-stu-id="55a50-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="55a50-122">Úplné informace o získání informací z načtené sestavení, naleznete v tématu [dynamické načtení a použití typů](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="55a50-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="55a50-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55a50-123">See also</span></span>
- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="55a50-124">Programování pomocí domén aplikace</span><span class="sxs-lookup"><span data-stu-id="55a50-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="55a50-125">Reflexe</span><span class="sxs-lookup"><span data-stu-id="55a50-125">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="55a50-126">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="55a50-126">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
- [<span data-ttu-id="55a50-127">Postupy: Načtení sestavení do kontextu pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="55a50-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="55a50-128">Domény a sestavení aplikací</span><span class="sxs-lookup"><span data-stu-id="55a50-128">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
