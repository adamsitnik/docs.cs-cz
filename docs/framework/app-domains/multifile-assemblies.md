---
title: Vícesouborová sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e00ec239fbe5d5963edd3a7656961556792c6324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593546"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="04047-102">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="04047-102">Multifile Assemblies</span></span>

<span data-ttu-id="04047-103">Můžete vytvořit vícesouborové sestavení pomocí kompilátoru příkazového řádku nebo Visual Studio s jazykem Visual C++.</span><span class="sxs-lookup"><span data-stu-id="04047-103">You can create multifile assemblies using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="04047-104">Jeden soubor v sestavení musí obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="04047-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="04047-105">Vstupní bod, například pro metodu Main nebo WinMain musí obsahovat také sestavení, které spustí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="04047-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>

<span data-ttu-id="04047-106">Předpokládejme například, že máte aplikaci, která obsahuje dva moduly kódu, Client.cs a Stringer.cs.</span><span class="sxs-lookup"><span data-stu-id="04047-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="04047-107">Vytvoří Stringer.cs `myStringer` obor názvů, který se odkazuje pomocí kódu v Client.cs.</span><span class="sxs-lookup"><span data-stu-id="04047-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="04047-108">Obsahuje Client.cs `Main` metodu, která je vstupní bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="04047-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="04047-109">V tomto příkladu kompilaci dva moduly kódu a pak vytvořte třetí soubor, který obsahuje manifest sestavení, který spouští aplikaci.</span><span class="sxs-lookup"><span data-stu-id="04047-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="04047-110">Manifest sestavení odkazuje na i `Client` a `Stringer` moduly.</span><span class="sxs-lookup"><span data-stu-id="04047-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>

> [!NOTE]
> <span data-ttu-id="04047-111">Vícesouborová sestavení může mít pouze jeden vstupní bod, i v případě, že sestavení má více modulů kódu.</span><span class="sxs-lookup"><span data-stu-id="04047-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="04047-112">Existuje několik důvodů, proč že můžete chtít vytvořit vícesouborové sestavení:</span><span class="sxs-lookup"><span data-stu-id="04047-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="04047-113">Kombinování modulů napsaných v různých jazycích.</span><span class="sxs-lookup"><span data-stu-id="04047-113">To combine modules written in different languages.</span></span> <span data-ttu-id="04047-114">Toto je nejběžnějším důvodem pro vytvoření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="04047-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="04047-115">K optimalizaci stahování aplikace tak, že vložíte zřídka používané typy modulu, který se stáhne jenom v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="04047-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="04047-116">Pokud vytváříte aplikace, které budou staženy pomocí `<object>` značku Microsoft Internet Explorer, je důležité vytvořit vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="04047-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="04047-117">V tomto scénáři vytvoříte soubor odděleně od moduly kódu, které obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="04047-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="04047-118">Aplikace Internet Explorer nejprve stáhne manifest sestavení a pak vytvoří pracovních vláken pro stahování jakékoli další moduly nebo požadovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="04047-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="04047-119">Při stažení souboru, který obsahuje manifest sestavení aplikace Internet Explorer bude reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="04047-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="04047-120">Čím menší soubor obsahující manifest sestavení, tím méně času aplikace Internet Explorer nebude reagovat.</span><span class="sxs-lookup"><span data-stu-id="04047-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="04047-121">Kombinovat kód modulů napsaných několik vývojáři.</span><span class="sxs-lookup"><span data-stu-id="04047-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="04047-122">I když každý vývojář může každý modul kódu zkompilovat do sestavení, tato vynutí některé typy veřejně zpřístupní, které nejsou vystaveny, pokud všechny moduly jsou vloženy do vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="04047-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="04047-123">Po vytvoření sestavení lze podepsat soubor obsahující manifest sestavení (a tedy sestavení), nebo můžete poskytnout silného názvu souboru (a sestavení) a vložit ho do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="04047-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="04047-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04047-124">See also</span></span>

- [<span data-ttu-id="04047-125">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="04047-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="04047-126">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="04047-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)