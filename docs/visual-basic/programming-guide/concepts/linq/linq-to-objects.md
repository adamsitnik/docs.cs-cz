---
title: LINQ to Objects (Visual Basic)
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: c1e2e8fbaaf984fec69322a459fc7c55890965ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326876"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="456ee-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ee-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="456ee-103">Termín "LINQ na objekty" odkazuje na použití odkazu LINQ dotazy s žádným <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekce přímo, bez použití zprostředkující zprostředkovatele LINQ nebo rozhraní API, jako [technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="456ee-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="456ee-104">LINQ můžete použít k dotazování všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601>, <xref:System.Array>, nebo <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="456ee-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="456ee-105">Kolekce může být uživatelem definované nebo mohou být vráceny rozhraní API .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="456ee-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="456ee-106">V základní smysl představuje LINQ to Objects nový přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="456ee-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="456ee-107">Starý způsob jste museli psát složité `For Each` smyček, které zadaná jak načíst data z kolekce.</span><span class="sxs-lookup"><span data-stu-id="456ee-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="456ee-108">U přístupu s LINQ napíšete deklarativního kódu, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="456ee-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="456ee-109">Kromě toho dotazů LINQ nabízejí tři hlavní výhody oproti tradičním `For Each` smyček:</span><span class="sxs-lookup"><span data-stu-id="456ee-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="456ee-110">Jsou stručnějším a čitelnějším, zejména v případě, že filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="456ee-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="456ee-111">Poskytují efektivní filtrování, řazení a seskupování schopností minimální kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="456ee-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="456ee-112">Může být přenést k jiným zdrojům dat s téměř nebo vůbec žádné změny.</span><span class="sxs-lookup"><span data-stu-id="456ee-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="456ee-113">Obecně platí, tím složitější operace, které chcete provést na datech, další výhody značným s využitím jazyka LINQ místo iterace tradiční techniky.</span><span class="sxs-lookup"><span data-stu-id="456ee-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="456ee-114">Cílem této části je předvést přístup LINQ s příklady vyberte.</span><span class="sxs-lookup"><span data-stu-id="456ee-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="456ee-115">Není určena být vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="456ee-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="456ee-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="456ee-116">In This Section</span></span>  
 [<span data-ttu-id="456ee-117">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ee-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="456ee-118">Tento článek vysvětluje použití LINQ na dotazování a transformaci řetězce a kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="456ee-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="456ee-119">Obsahuje také odkazy na témata, která ukazují tyto zásady.</span><span class="sxs-lookup"><span data-stu-id="456ee-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="456ee-120">LINQ a reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ee-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="456ee-121">Obsahuje odkazy na ukázky, která ukazuje, jak LINQ používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="456ee-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="456ee-122">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ee-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="456ee-123">Vysvětluje, jak lze pomocí LINQ komunikovat se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="456ee-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="456ee-124">Obsahuje také odkazy na témata, které předvádějí koncepce.</span><span class="sxs-lookup"><span data-stu-id="456ee-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="456ee-125">Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ee-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="456ee-126">Demonstruje postup vytvoření dotazu na ArrayList v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="456ee-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="456ee-127">Postupy: Přidávání vlastních metod do dotazů LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ee-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="456ee-128">Vysvětluje, jak rozšířit sadu metod, které můžete použít pro LINQ dotazy přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="456ee-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="456ee-129">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ee-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="456ee-130">Obsahuje odkazy na témata, která vysvětlují LINQ a příklady kódu, které provádějí dotazy.</span><span class="sxs-lookup"><span data-stu-id="456ee-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
