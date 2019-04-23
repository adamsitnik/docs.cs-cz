---
title: Typové datové sady
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 92ed3f8fd392238785fd2d205668f14fe477f2b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098647"
---
# <a name="typed-datasets"></a><span data-ttu-id="fb714-102">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="fb714-102">Typed DataSets</span></span>
<span data-ttu-id="fb714-103">Spolu s pozdní vazbou přístup k hodnotám prostřednictvím slabě typované proměnné <xref:System.Data.DataSet> poskytuje přístup k datům prostřednictvím metafora silného typu.</span><span class="sxs-lookup"><span data-stu-id="fb714-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="fb714-104">Tabulky a sloupce, které jsou součástí **datovou sadu** lze přistupovat pomocí uživatelsky přívětivých názvů a silně typované proměnné.</span><span class="sxs-lookup"><span data-stu-id="fb714-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="fb714-105">Zadaný **datovou sadu** je třída, která je odvozena z **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="fb714-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="fb714-106">V důsledku toho dědí všechny metody, události a vlastnosti **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="fb714-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="fb714-107">Kromě toho typovaného **datovou sadu** poskytuje silného typu metody, události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fb714-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="fb714-108">To znamená, že se zobrazí tabulky a sloupce podle názvu, namísto použití metody založené na kolekci.</span><span class="sxs-lookup"><span data-stu-id="fb714-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="fb714-109">Kromě lepší čitelnost kódu, typovaného **datovou sadu** také umožňuje kódu sady Visual Studio .NET editoru při psaní automaticky dokončit řádky.</span><span class="sxs-lookup"><span data-stu-id="fb714-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="fb714-110">Kromě toho silnými typy **datovou sadu** poskytuje přístup k hodnotám jako správného typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="fb714-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="fb714-111">Se silnými typy **datovou sadu**, jsou zachyceny chyby neshoda typu, pokud kód je zkompilován spíše než v čas spuštění.</span><span class="sxs-lookup"><span data-stu-id="fb714-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb714-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fb714-112">In This Section</span></span>  
 [<span data-ttu-id="fb714-113">Generování datových sad se silnými typy</span><span class="sxs-lookup"><span data-stu-id="fb714-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="fb714-114">Popisuje, jak vytvořit a používat silného typu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="fb714-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="fb714-115">Zadávání poznámek k typovým datovým sadám</span><span class="sxs-lookup"><span data-stu-id="fb714-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="fb714-116">Popisuje postup přidání poznámek ke jazyk (XSD) schématu definice schématu XML sloužící ke generování silného typu **datovou sadu**, abyste **datovou sadu** popisné názvy prvků beze změny podkladového schématu.</span><span class="sxs-lookup"><span data-stu-id="fb714-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb714-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb714-117">See also</span></span>

- [<span data-ttu-id="fb714-118">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="fb714-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="fb714-119">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="fb714-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
