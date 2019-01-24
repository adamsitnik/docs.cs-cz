---
title: Systém typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 1831028f9e659dab90ca3c8689d7ff2d5c0ee36a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554332"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="065ce-102">Systém typů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="065ce-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="065ce-103">podporuje několik typů:</span><span class="sxs-lookup"><span data-stu-id="065ce-103">supports a number of types:</span></span>  
  
-   <span data-ttu-id="065ce-104">(Jednoduchý) primitivní typy, jako `Int32` a `String.`</span><span class="sxs-lookup"><span data-stu-id="065ce-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
-   <span data-ttu-id="065ce-105">Nominální typy, které jsou definovány ve schématu, jako například <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, a <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="065ce-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
-   <span data-ttu-id="065ce-106">Anonymní typy, které nejsou explicitně definovány ve schématu: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, a <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="065ce-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="065ce-107">Tato část pojednává o anonymních typů, které nejsou explicitně definovány ve schématu však není podporovaná [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="065ce-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="065ce-108">Informace o typech primitivní a nominální najdete v tématu [koncepční Model typy (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4).</span><span class="sxs-lookup"><span data-stu-id="065ce-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="065ce-109">Řádky</span><span class="sxs-lookup"><span data-stu-id="065ce-109">Rows</span></span>  
 <span data-ttu-id="065ce-110">Struktura řádek závisí na pořadí zadaném a pojmenované členy, které se skládá z řádku.</span><span class="sxs-lookup"><span data-stu-id="065ce-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="065ce-111">Typ řádku nemá žádná identita a nejde ji zdědit z.</span><span class="sxs-lookup"><span data-stu-id="065ce-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="065ce-112">Instance stejného typu řádku jsou rovnocenné, pokud jsou v uvedeném pořadí ekvivalentních členy.</span><span class="sxs-lookup"><span data-stu-id="065ce-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="065ce-113">Řádky mít žádné chování, mimo jejich ekvivalence strukturální a nemají žádný ekvivalent v modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="065ce-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="065ce-114">Struktury obsahující řádky nebo kolekce řádků může způsobit dotazů.</span><span class="sxs-lookup"><span data-stu-id="065ce-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="065ce-115">Rozhraní API vazby mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy a jazyk hostitelského definuje, jak jsou realizované řádků v dotazu, který vytváří výsledek.</span><span class="sxs-lookup"><span data-stu-id="065ce-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="065ce-116">Informace o tom, jak vytvořit instanci řádku najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="065ce-116">For information on how to construct a row instance, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="065ce-117">Kolekce</span><span class="sxs-lookup"><span data-stu-id="065ce-117">Collections</span></span>  
 <span data-ttu-id="065ce-118">Typy kolekce představují nula nebo víc instancí jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="065ce-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="065ce-119">Informace o tom, jak vytvořit kolekci, najdete v části [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="065ce-119">For information on how to construct collection, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="065ce-120">Odkazy</span><span class="sxs-lookup"><span data-stu-id="065ce-120">References</span></span>  
 <span data-ttu-id="065ce-121">Odkaz je logický ukazatel na konkrétní entitu v sadě konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="065ce-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="065ce-122">podporuje následující operátory sestavit, dekonstruovat a procházejte odkazy:</span><span class="sxs-lookup"><span data-stu-id="065ce-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
-   [<span data-ttu-id="065ce-123">REF</span><span class="sxs-lookup"><span data-stu-id="065ce-123">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [<span data-ttu-id="065ce-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="065ce-124">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [<span data-ttu-id="065ce-125">KEY</span><span class="sxs-lookup"><span data-stu-id="065ce-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [<span data-ttu-id="065ce-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="065ce-126">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 <span data-ttu-id="065ce-127">Odkaz můžete procházet pomocí operátoru přístupu (tečka) člena (`.`).</span><span class="sxs-lookup"><span data-stu-id="065ce-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="065ce-128">Následující fragment kódu extrahuje Vlastnost Id (pořadí) tak, že přejdete prostřednictvím vlastnosti r (odkaz).</span><span class="sxs-lookup"><span data-stu-id="065ce-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="065ce-129">Pokud je hodnota odkaz null nebo cílem odkazu ještě neexistuje, výsledek je null.</span><span class="sxs-lookup"><span data-stu-id="065ce-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065ce-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="065ce-130">See also</span></span>
- [<span data-ttu-id="065ce-131">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="065ce-131">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="065ce-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="065ce-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="065ce-133">CAST</span><span class="sxs-lookup"><span data-stu-id="065ce-133">CAST</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)
- [<span data-ttu-id="065ce-134">Specifikace CSDL, SSDL a MSL</span><span class="sxs-lookup"><span data-stu-id="065ce-134">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
