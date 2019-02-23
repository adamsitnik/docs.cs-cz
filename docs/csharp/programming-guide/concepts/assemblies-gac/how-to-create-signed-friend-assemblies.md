---
title: 'Postupy: Vytváření podepsaných přátelských sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 54307313eb7955a40e290218aacf27be320e745b
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746659"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="8b275-102">Postupy: Vytváření podepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="8b275-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="8b275-103">Tento příklad ukazuje způsob použití sestavení typu friend se sestaveními, která mít silné názvy.</span><span class="sxs-lookup"><span data-stu-id="8b275-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="8b275-104">Obě sestavení musí být silný název.</span><span class="sxs-lookup"><span data-stu-id="8b275-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="8b275-105">Přestože obě sestavení v tomto příkladu pomocí stejných klíčů, můžete použít různé klíče pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b275-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="8b275-106">Chcete-li vytvořit podepsané sestavení a sestavení typu friend</span><span class="sxs-lookup"><span data-stu-id="8b275-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="8b275-107">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="8b275-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="8b275-108">Použijte následující posloupnost příkazů s nástroj Strong Name keyfile generovat a zobrazit jeho veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="8b275-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="8b275-109">Další informace najdete v tématu [Sn.exe (nástroj Strong Name)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8b275-109">For more information, see [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1.  <span data-ttu-id="8b275-110">Vygenerování klíče se silným názvem v tomto příkladu a uložit ho do souboru FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="8b275-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="8b275-111">Extrahujte veřejný klíč z FriendAssemblies.snk a vložit ho do FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="8b275-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="8b275-112">Zobrazení veřejného klíče uložené v souboru FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="8b275-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="8b275-113">Vytvořte soubor jazyka C# s názvem `friend_signed_A` , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b275-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="8b275-114">Tento kód použije <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut pro deklaraci friend_signed_B jako sestavení typu friend.</span><span class="sxs-lookup"><span data-stu-id="8b275-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="8b275-115">Nástroj Strong Name vygeneruje nový veřejný klíč pokaždé, když ji spustí.</span><span class="sxs-lookup"><span data-stu-id="8b275-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="8b275-116">Proto je potřeba nahradit veřejný klíč v následujícím kódu veřejný klíč, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b275-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
    ```csharp  
    // friend_signed_A.cs  
    // Compile with:   
    // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    using System.Runtime.CompilerServices;  
  
    [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
    class Class1  
    {  
        public void Test()  
        {  
            System.Console.WriteLine("Class1.Test");  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="8b275-117">Kompilace a podepsání friend_signed_A pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="8b275-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="8b275-118">Vytvořte soubor jazyka C#, který je pojmenován `friend_signed_B` a obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b275-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="8b275-119">Protože friend_signed_A určuje friend_signed_B jako sestavení typu friend, můžete přístup ke kódu v friend_signed_B `internal` typy a členy z friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="8b275-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="8b275-120">Soubor obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b275-120">The file contains the following code.</span></span>  
  
    ```csharp  
    // friend_signed_B.cs  
    // Compile with:   
    // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            Class1 inst = new Class1();  
            inst.Test();  
        }  
    }  
    ```  
  
6.  <span data-ttu-id="8b275-121">Kompilace a podepsání friend_signed_B pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="8b275-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="8b275-122">Název sestavení generovaný kompilátorem musí odpovídat názvu sestavení typu friend předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8b275-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="8b275-123">Musíte explicitně zadat název výstupního sestavení (.exe nebo .dll) s použitím `/out` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8b275-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="8b275-124">Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="8b275-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="8b275-125">Spusťte soubor friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="8b275-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="8b275-126">Program zobrazí řetězec "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="8b275-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8b275-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8b275-127">.NET Framework Security</span></span>  
 <span data-ttu-id="8b275-128">Existují podobnost <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b275-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="8b275-129">Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může požadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda `internal` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="8b275-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b275-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b275-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="8b275-131">Sestavení v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="8b275-131">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="8b275-132">Přátelská sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="8b275-132">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)
- [<span data-ttu-id="8b275-133">Postupy: Vytváření nepodepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="8b275-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="8b275-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="8b275-134">/keyfile</span></span>](../../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="8b275-135">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="8b275-135">Sn.exe (Strong Name Tool)</span></span>](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="8b275-136">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="8b275-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="8b275-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8b275-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
