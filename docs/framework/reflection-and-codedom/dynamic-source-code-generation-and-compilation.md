---
title: Dynamické vytváření a kompilování zdrojového kódu
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8feb94f3d57c25d634bd51b8f41eca42d5e5757a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220306"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="1eb63-102">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="1eb63-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="1eb63-103">Rozhraní .NET Framework obsahuje mechanismus volá se, kód modelu objektu dokumentu (CodeDOM), který umožňuje vývojářům aplikací, které generují zdrojový kód ke generování zdrojového kódu ve více programovacích jazyků v době běhu na základě jednoho modelu, který představuje kód k vykreslení.</span><span class="sxs-lookup"><span data-stu-id="1eb63-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="1eb63-104">K reprezentaci zdrojový kód, prvky CodeDOM jsou vzájemně propojit a k vytvoření datová struktura, označované jako graf CodeDOM, který modeluje struktura určitý zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="1eb63-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="1eb63-105">`System.CodeDom` Obor názvů definuje typy, které mohou představovat logické struktury zdrojového kódu, nezávisle na konkrétní programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="1eb63-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="1eb63-106">`System.CodeDom.Compiler` Obor názvů definuje typy pro generování zdrojového kódu z grafu modelu CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích.</span><span class="sxs-lookup"><span data-stu-id="1eb63-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="1eb63-107">Kompilátor dodavatelů nebo vývojáři rozšířit sadu podporované jazyky.</span><span class="sxs-lookup"><span data-stu-id="1eb63-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="1eb63-108">Modelování nezávislým na jazyku zdrojového kódu může být důležité, když program potřebuje ke generování zdrojového kódu pro model program v několika jazycích nebo neurčité cílový jazyk.</span><span class="sxs-lookup"><span data-stu-id="1eb63-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="1eb63-109">Například některé návrháře pomocí CodeDOM jako jazyk abstrakce rozhraní pro vytvoření zdrojového kódu ve správném programovacím jazyce, pokud je k dispozici podpora CodeDOM pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="1eb63-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="1eb63-110">Rozhraní .NET Framework obsahuje generátory kódu a kódu kompilátory pro <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="1eb63-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1eb63-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1eb63-111">In This Section</span></span>  
 [<span data-ttu-id="1eb63-112">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1eb63-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="1eb63-113">Popisuje běžné použití a ukazuje vytvoření jednoduchého objektu grafu pomocí CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1eb63-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="1eb63-114">Generování zdrojového kódu a kompilace programu grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1eb63-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="1eb63-115">Popisuje, jak generovat zdrojového kódu a kompilace generovaného kódu s externí kompilátoru pomocí tříd definovaných v `System.CodeDom.Compiler` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1eb63-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="1eb63-116">Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1eb63-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="1eb63-117">Popisuje, jak generovat kód, který se dokumentační komentáře XML a kompilace generovaného kódu tak, aby vytvořil výstupní dokumentace XML pomocí modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1eb63-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="1eb63-118">Postupy: Vytváření třídy pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1eb63-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="1eb63-119">Popisuje, jak vygenerovat třídu obsahující pole, vlastnosti, metody, konstruktor a vstupního bodu pomocí CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1eb63-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1eb63-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1eb63-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="1eb63-121">Definuje prvky, které představují prvky kódu v programovacích jazycích, které se zaměřují modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1eb63-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="1eb63-122">Definuje rozhraní pro generování a kompilace kódu za běhu.</span><span class="sxs-lookup"><span data-stu-id="1eb63-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1eb63-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1eb63-123">Related Sections</span></span>  
 <span data-ttu-id="1eb63-124">[CodeDOM – Stručná referenční příručka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1eb63-124">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>  
 <span data-ttu-id="1eb63-125">Poskytuje rychlý způsob, jak vývojářům usnadnit hledání prvky CodeDOM, které představují prvků zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1eb63-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
