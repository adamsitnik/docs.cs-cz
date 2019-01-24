---
title: Souhrn procesu odvození schématu datové sady
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 1eb12fd9c983bc0013b5dc528e0b3389250bdbe2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527650"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="2cc42-102">Souhrn procesu odvození schématu datové sady</span><span class="sxs-lookup"><span data-stu-id="2cc42-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="2cc42-103">Procesu odvození nejdřív zjistí, z dokumentu XML, prvky, které se odvodit jako tabulka.</span><span class="sxs-lookup"><span data-stu-id="2cc42-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="2cc42-104">Ze zbývajících XML určuje proces odvození sloupce pro tyto tabulky.</span><span class="sxs-lookup"><span data-stu-id="2cc42-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="2cc42-105">Pro vnořené tabulky procesu odvození generuje vnořené <xref:System.Data.DataRelation> a <xref:System.Data.ForeignKeyConstraint> objekty.</span><span class="sxs-lookup"><span data-stu-id="2cc42-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="2cc42-106">Tady je stručný přehled odvozených pravidel:</span><span class="sxs-lookup"><span data-stu-id="2cc42-106">Following is a brief summary of inference rules:</span></span>  
  
-   <span data-ttu-id="2cc42-107">Prvky, které mají atributy jsou odvozeny jako tabulka.</span><span class="sxs-lookup"><span data-stu-id="2cc42-107">Elements that have attributes are inferred as tables.</span></span>  
  
-   <span data-ttu-id="2cc42-108">Prvky, které mají podřízené prvky jsou odvozeny jako tabulka.</span><span class="sxs-lookup"><span data-stu-id="2cc42-108">Elements that have child elements are inferred as tables.</span></span>  
  
-   <span data-ttu-id="2cc42-109">Prvky, které se opakují jsou odvozeny jako jednu tabulku.</span><span class="sxs-lookup"><span data-stu-id="2cc42-109">Elements that repeat are inferred as a single table.</span></span>  
  
-   <span data-ttu-id="2cc42-110">Pokud má element dokumentu nebo kořenový, atributy a žádné podřízené prvky, které by odvodit jako sloupce, je odvozený jako <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2cc42-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="2cc42-111">V opačném případě je element dokumentu odvozen jako tabulku.</span><span class="sxs-lookup"><span data-stu-id="2cc42-111">Otherwise, the document element is inferred as a table.</span></span>  
  
-   <span data-ttu-id="2cc42-112">Atributy jsou odvozeny jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="2cc42-112">Attributes are inferred as columns.</span></span>  
  
-   <span data-ttu-id="2cc42-113">Prvky, které mají žádné atributy nebo podřízené prvky a, které se neopakují, jsou odvozeny jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="2cc42-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
-   <span data-ttu-id="2cc42-114">Pro prvky, které jsou odvozeny jako vnořené tabulky v rámci další prvky, které jsou odvozeny také jako tabulky, vnořený **DataRelation** je vytvořen mezi dvěma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="2cc42-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="2cc42-115">Nové, primární klíčový sloupec s názvem **TableName_Id** bude přidána do obou tabulek a používá **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="2cc42-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="2cc42-116">A **Objekt ForeignKeyConstraint** je vytvořen mezi dvěma tabulkami pomocí **TableName_Id** sloupce.</span><span class="sxs-lookup"><span data-stu-id="2cc42-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
-   <span data-ttu-id="2cc42-117">Pro prvky, které jsou odvozeny jako tabulky a které obsahují text, ale mít žádné podřízené prvky, nový sloupec s názvem **TableName_Text** je vytvořená pro text jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="2cc42-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="2cc42-118">Pokud element je odvozen jako tabulku a obsahuje text, ale má také podřízené prvky, text se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2cc42-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc42-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cc42-119">See also</span></span>
- [<span data-ttu-id="2cc42-120">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="2cc42-120">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="2cc42-121">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="2cc42-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="2cc42-122">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="2cc42-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="2cc42-123">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="2cc42-123">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="2cc42-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="2cc42-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="2cc42-125">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2cc42-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
