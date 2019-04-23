---
title: Tvar stromu příkazů
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 08a67c8d181188cbc14c6f60876a7e26cd6de25a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980080"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="12f36-102">Tvar stromu příkazů</span><span class="sxs-lookup"><span data-stu-id="12f36-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="12f36-103">Modul generování SQL je zodpovědný za generování back-endu konkrétní dotaz SQL na základě daný vstupní dotaz příkaz stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="12f36-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="12f36-104">Tato část popisuje vlastnosti, vlastnosti a struktuře stromu příkazů dotazů.</span><span class="sxs-lookup"><span data-stu-id="12f36-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="12f36-105">Přehled stromů příkaz dotazu</span><span class="sxs-lookup"><span data-stu-id="12f36-105">Query Command Trees Overview</span></span>

<span data-ttu-id="12f36-106">Dotaz stromu příkazů je reprezentaci modelu objektu dotazu.</span><span class="sxs-lookup"><span data-stu-id="12f36-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="12f36-107">Stromy příkazů dotazů mají dva účely:</span><span class="sxs-lookup"><span data-stu-id="12f36-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="12f36-108">Vyjádřit vstupní dotaz, který je zadán proti [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12f36-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>

- <span data-ttu-id="12f36-109">Vyjádřit dotaz výstup, který je uveden na poskytovatele a popisuje dotazu na back-endu.</span><span class="sxs-lookup"><span data-stu-id="12f36-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="12f36-110">Dotazování příkazu stromů podporu bohatší sémantiku než SQL:1999 kompatibilní s dotazy, včetně podpory pro práci s vnořené kolekce a typ operace, jako je kontrola, jestli je entita určitého typu nebo filtrování podle typu sady.</span><span class="sxs-lookup"><span data-stu-id="12f36-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="12f36-111">Vlastnost DBQueryCommandTree.Query je kořenem stromu výrazů, který popisuje logiku dotazu.</span><span class="sxs-lookup"><span data-stu-id="12f36-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="12f36-112">Vlastnost DBQueryCommandTree.Parameters obsahuje seznam parametrů, které se používají v dotazu.</span><span class="sxs-lookup"><span data-stu-id="12f36-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="12f36-113">Strom výrazu se skládá z DbExpression objekty.</span><span class="sxs-lookup"><span data-stu-id="12f36-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="12f36-114">Objekt DbExpression představuje některé výpočtu.</span><span class="sxs-lookup"><span data-stu-id="12f36-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="12f36-115">Jsou k dispozici v několika druhů výrazy [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro sestavení výrazy dotazu, včetně konstant, proměnné, funkce, konstruktory a standardní relační operátory, jako je filtrování a spojení.</span><span class="sxs-lookup"><span data-stu-id="12f36-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="12f36-116">Každý objekt DbExpression má vlastnost ResultType, který představuje typ výsledku vytvořeného tento výraz.</span><span class="sxs-lookup"><span data-stu-id="12f36-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="12f36-117">Tento typ je vyjádřen jako vlastnost TypeUsage.</span><span class="sxs-lookup"><span data-stu-id="12f36-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="12f36-118">Tvary stromu příkazů výstup dotazu</span><span class="sxs-lookup"><span data-stu-id="12f36-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="12f36-119">Stromy příkazů výstup dotazu představují relačních dotazů (SQL) a dodržovat pravidla mnohem větší než ty, které se vztahují na stromy příkaz dotazu.</span><span class="sxs-lookup"><span data-stu-id="12f36-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="12f36-120">Obvykle obsahují konstrukce, které jsou snadno do kódu SQL.</span><span class="sxs-lookup"><span data-stu-id="12f36-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="12f36-121">Vstupní příkaz stromové struktury jsou vyjádřeny proti konceptuální model, který podporuje navigačních vlastností asociace mezi entitami a dědičnost.</span><span class="sxs-lookup"><span data-stu-id="12f36-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="12f36-122">Výstup příkazu stromů jsou vyjádřeny pro model úložiště.</span><span class="sxs-lookup"><span data-stu-id="12f36-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="12f36-123">Vstupní příkaz stromů umožňují vnořené kolekce projektů, ale výstup příkazu stromů tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="12f36-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="12f36-124">Stromy příkazů výstup dotazu jsou sestaveny na základě podmnožinu dostupných objektů DbExpression a dokonce i některé výrazy v ní mají omezený využití.</span><span class="sxs-lookup"><span data-stu-id="12f36-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="12f36-125">Typ operace, jako je kontrola, zda je daný výraz určitého typu nebo filtrování sady na základě typu, nejsou zadány ve výstupu příkazu stromu.</span><span class="sxs-lookup"><span data-stu-id="12f36-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="12f36-126">Ve výstupu příkazu stromu se používají pouze výrazy, které vracejí logické hodnoty pro projekce a pouze pro predikáty ve výrazech vyžadující predikátu, jako je filtr nebo příkazy case.</span><span class="sxs-lookup"><span data-stu-id="12f36-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="12f36-127">Kořenové stromů příkazů výstup dotazu je objekt DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="12f36-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="12f36-128">Typy výrazů není k dispozici v stromů příkazů výstup dotazu</span><span class="sxs-lookup"><span data-stu-id="12f36-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="12f36-129">Následující typy výrazů nejsou platné ve výstupu stromu příkaz dotazu a není nutné ošetřit zprostředkovatelé:</span><span class="sxs-lookup"><span data-stu-id="12f36-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="12f36-130">Objekt DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-130">DbDerefExpression</span></span>

- <span data-ttu-id="12f36-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="12f36-132">Třída DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="12f36-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-133">DbIsOfExpression</span></span>

- <span data-ttu-id="12f36-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="12f36-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-135">DbRefExpression</span></span>

- <span data-ttu-id="12f36-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="12f36-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="12f36-138">Výraz omezení a poznámky</span><span class="sxs-lookup"><span data-stu-id="12f36-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="12f36-139">Mnoho výrazů jde použít jenom s omezeným přístupem způsobem v stromů příkazů výstup dotazu:</span><span class="sxs-lookup"><span data-stu-id="12f36-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="12f36-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-140">DbFunctionExpression</span></span>

<span data-ttu-id="12f36-141">Je možné předat následující typy funkcí:</span><span class="sxs-lookup"><span data-stu-id="12f36-141">The following function types can be passed:</span></span>

- <span data-ttu-id="12f36-142">Kanonické funkce, které jsou rozpoznány modulem pro obor názvů Edm.</span><span class="sxs-lookup"><span data-stu-id="12f36-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="12f36-143">Funkce integrované (úložiště), které jsou rozpoznány modulem BuiltInAttribute.</span><span class="sxs-lookup"><span data-stu-id="12f36-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="12f36-144">Uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="12f36-144">User-defined functions.</span></span>

<span data-ttu-id="12f36-145">Kanonické funkce (naleznete v tématu [kanonické funkce](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Další informace) jsou určené jako součást [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], a poskytovatelé by mělo nabízet implementace pro kanonické funkce na základě těchto specifikací.</span><span class="sxs-lookup"><span data-stu-id="12f36-145">Canonical functions (see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="12f36-146">Funkce Store jsou založeny na specifikacích v manifestu zprostředkovatele, odpovídající.</span><span class="sxs-lookup"><span data-stu-id="12f36-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="12f36-147">Uživatelem definované funkce jsou založeny na specifikacích SSDL.</span><span class="sxs-lookup"><span data-stu-id="12f36-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="12f36-148">Funkce s atributem NiladicFunction také nemají žádné argumenty a bez závorky na konci by měl přeložit.</span><span class="sxs-lookup"><span data-stu-id="12f36-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="12f36-149">To znamená do  *\<functionName >* místo  *\<functionName > ()*.</span><span class="sxs-lookup"><span data-stu-id="12f36-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="12f36-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="12f36-151">DbNewInstanceExpression může vyskytovat jenom v těchto dvou případů:</span><span class="sxs-lookup"><span data-stu-id="12f36-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="12f36-152">Jako vlastnost projekce DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="12f36-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="12f36-153">Pokud se použije jako takové platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="12f36-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="12f36-154">Typ výsledku musí být typu řádku.</span><span class="sxs-lookup"><span data-stu-id="12f36-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="12f36-155">Každá z jejích argumentů je výraz, který vytváří výsledek s primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="12f36-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="12f36-156">Obvykle každý argument je skalární výraz, stejně jako PropertyExpression DbVariableReferenceExpression, volání funkce nebo pro aritmetické výpočtu DbPropertyExpression přes DbVariableReferenceExpression nebo volání funkce .</span><span class="sxs-lookup"><span data-stu-id="12f36-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="12f36-157">Ale představující poddotaz skalární výraz může vzniknout také v seznamu argumentů DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="12f36-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="12f36-158">Strom výrazů, který představuje poddotazu, která vrací přesně jeden řádek a jeden sloupec primitivní typ objektu kořenovou DbElementExpression je výraz, který reprezentuje skalární poddotazu</span><span class="sxs-lookup"><span data-stu-id="12f36-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="12f36-159">S návratovým typem kolekce v takovém případě definuje novou kolekci výrazů zadané jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="12f36-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="12f36-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="12f36-161">DbVariableReferenceExpression musí být podřízeným uzlem DbPropertyExpression uzlu.</span><span class="sxs-lookup"><span data-stu-id="12f36-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="12f36-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-162">DbGroupByExpression</span></span>

<span data-ttu-id="12f36-163">Vlastnost agregace Dbgroupaggregate může obsahovat pouze prvky typu DbFunctionAggregate.</span><span class="sxs-lookup"><span data-stu-id="12f36-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="12f36-164">Nejsou žádné další typy agregátů.</span><span class="sxs-lookup"><span data-stu-id="12f36-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="12f36-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-165">DbLimitExpression</span></span>

<span data-ttu-id="12f36-166">Vlastnost Limit může být pouze objekt DbConstantExpression nebo DbParameterReferenceExpression.</span><span class="sxs-lookup"><span data-stu-id="12f36-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="12f36-167">Také vlastnost WithTies má vždy hodnotu false od verze rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="12f36-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="12f36-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="12f36-168">DbScanExpression</span></span>

<span data-ttu-id="12f36-169">Při použití ve výstupu příkazu stromu, DbScanExpression efektivně představuje kontrolu nad tabulky, zobrazení nebo dotaz úložiště, reprezentovaný EntitySetBase::Target.</span><span class="sxs-lookup"><span data-stu-id="12f36-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="12f36-170">Pokud vlastnost metadat "Definice dotazu" cíle je jiná než null, pak představuje dotaz, text dotazu, pro který je součástí této vlastnosti metadat v poskytovatele konkrétní jazyk (nebo dialekt), jak je uvedeno v definici schématu úložiště.</span><span class="sxs-lookup"><span data-stu-id="12f36-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="12f36-171">V opačném případě cíl představuje tabulku nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="12f36-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="12f36-172">Jeho předpona schématu je buď ve vlastnosti metadat "Schéma", pokud není null, jinak je název kontejneru entity.</span><span class="sxs-lookup"><span data-stu-id="12f36-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="12f36-173">Název tabulky nebo zobrazení je buď vlastnost metadat "Table", pokud není null, jinak nastavte základní vlastnosti název entity.</span><span class="sxs-lookup"><span data-stu-id="12f36-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="12f36-174">Všechny tyto vlastnosti pocházejí z definice odpovídající objekt EntitySet v souboru definice schématu úložiště (SSDL).</span><span class="sxs-lookup"><span data-stu-id="12f36-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="12f36-175">Primitivní typy</span><span class="sxs-lookup"><span data-stu-id="12f36-175">Using Primitive Types</span></span>

<span data-ttu-id="12f36-176">Pokud se ve výstupu příkazu stromů odkazuje primitivní typy, jsou obvykle odkazovány v primitivních typech Koncepční model.</span><span class="sxs-lookup"><span data-stu-id="12f36-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="12f36-177">Pro některé výrazy musí poskytovatelé primitivní typ odpovídající úložiště.</span><span class="sxs-lookup"><span data-stu-id="12f36-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="12f36-178">Tyto výrazy příklady DbCastExpression a případně DbNullExpression, pokud zprostředkovatel potřebuje k přetypování hodnoty null na typ odpovídající.</span><span class="sxs-lookup"><span data-stu-id="12f36-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="12f36-179">V těchto případech poskytovatelů proveďte mapování na základě typ primitivní typ a její omezující vlastnosti typu zprostředkovatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12f36-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="12f36-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12f36-180">See also</span></span>

- [<span data-ttu-id="12f36-181">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="12f36-181">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
