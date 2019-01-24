---
title: x:Static – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 5dd454cb323d4dc2ab9b4ebd8b233ffda3e77820
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619318"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="69ec7-102">x:Static – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="69ec7-102">x:Static Markup Extension</span></span>
<span data-ttu-id="69ec7-103">Odkazuje na entitu kód statickou hodnotou, která je definována v [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– kompatibilní způsobem.</span><span class="sxs-lookup"><span data-stu-id="69ec7-103">References any static by-value code entity that is defined in a [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]–compliant way.</span></span> <span data-ttu-id="69ec7-104">Statická vlastnost, která je popsána slouží k poskytnutí hodnoty vlastností v XAML.</span><span class="sxs-lookup"><span data-stu-id="69ec7-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="69ec7-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="69ec7-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="69ec7-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="69ec7-106">XAML Values</span></span>  
  
| | |  
|-|-|  
|`prefix`|<span data-ttu-id="69ec7-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="69ec7-107">Optional.</span></span> <span data-ttu-id="69ec7-108">Předpona, která odkazuje na mapovanou, jiné než výchozí obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="69ec7-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="69ec7-109">`prefix` je zobrazena explicitně ve využití vzhledem k tomu, že odkazujete zřídka statické vlastnosti, které pocházejí z výchozí obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="69ec7-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="69ec7-110">Viz poznámky.</span><span class="sxs-lookup"><span data-stu-id="69ec7-110">See Remarks.</span></span>|  
|`typeName`|<span data-ttu-id="69ec7-111">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="69ec7-111">Required.</span></span> <span data-ttu-id="69ec7-112">Název typu, který definuje požadovaný statický člen.</span><span class="sxs-lookup"><span data-stu-id="69ec7-112">The name of the type that defines the desired static member.</span></span>|  
|`staticMemberName`|<span data-ttu-id="69ec7-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="69ec7-113">Required.</span></span> <span data-ttu-id="69ec7-114">Jméno člena požadovanou statickou hodnotu (konstantu, statické vlastnosti, pole nebo hodnoty výčtu).</span><span class="sxs-lookup"><span data-stu-id="69ec7-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69ec7-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69ec7-115">Remarks</span></span>  

<span data-ttu-id="69ec7-116">Kód entita, na který odkazuje musí být jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="69ec7-116">The code entity that is referenced must be one of the following:</span></span>  
  
-   <span data-ttu-id="69ec7-117">Konstanta</span><span class="sxs-lookup"><span data-stu-id="69ec7-117">A constant</span></span>  
-   <span data-ttu-id="69ec7-118">Statická vlastnost</span><span class="sxs-lookup"><span data-stu-id="69ec7-118">A static property</span></span>  
-   <span data-ttu-id="69ec7-119">Pole</span><span class="sxs-lookup"><span data-stu-id="69ec7-119">A field</span></span>  
-   <span data-ttu-id="69ec7-120">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="69ec7-120">An enumeration value</span></span>

<span data-ttu-id="69ec7-121">Určení jiné kód entitě, jako je například nestatické vlastnosti způsobí chybu kompilace při kompilaci kódu nebo výjimku během načítání analýzy XAML XAML.</span><span class="sxs-lookup"><span data-stu-id="69ec7-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>  

<span data-ttu-id="69ec7-122">Můžete provést `x:Static` odkazy na statické pole nebo vlastnosti, které nejsou ve výchozím oboru názvů XAML pro aktuální dokument XAML; to však vyžaduje mapování předpony.</span><span class="sxs-lookup"><span data-stu-id="69ec7-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="69ec7-123">Obory názvů XAML jsou téměř vždy definována na kořenový element dokumentu XAML.</span><span class="sxs-lookup"><span data-stu-id="69ec7-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>  

<span data-ttu-id="69ec7-124">Operace vyhledávání pro statické vlastnosti lze provést pomocí rozhraní .NET Framework XAML Services a jeho XAML čtečky a zapisovače XAML, když jsou spuštěné s výchozí kontext schématu XAML.</span><span class="sxs-lookup"><span data-stu-id="69ec7-124">The lookup operations for static properties can be performed by .NET Framework XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="69ec7-125">Tento kontext schématu XAML můžete CLR reflexe uvést nezbytné statické hodnoty pro vytváření grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="69ec7-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="69ec7-126">`typeName` Zadejte je ve skutečnosti XAML název typu, nikoli název typu CLR, i když tyto jsou v podstatě stejný název, při použití výchozí kontext schématu XAML nebo při použití všech stávajících architektur implementace XAML založené na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="69ec7-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>  

<span data-ttu-id="69ec7-127">Buďte opatrní při provedení `x:Static` odkazů, které nejsou přímo typ hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69ec7-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="69ec7-128">V XAML zpracování pořadí, zadané hodnoty z rozšíření značek není vyvolat převod další hodnoty.</span><span class="sxs-lookup"><span data-stu-id="69ec7-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="69ec7-129">To platí i v případě vaší `x:Static` vytvoří odkaz na textový řetězec a převod hodnoty pro atribut hodnoty založené na textový řetězec obvykle dochází u tohoto konkrétního člena nebo pro všechny hodnoty členů návratového typu.</span><span class="sxs-lookup"><span data-stu-id="69ec7-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>  

<span data-ttu-id="69ec7-130">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="69ec7-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="69ec7-131">Řetězec s tokenem uvedený za `x:Static` řetězec identifikátoru je přiřazen jako <xref:System.Windows.Markup.StaticExtension.Member%2A> hodnoty základního <xref:System.Windows.Markup.StaticExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="69ec7-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>  

<span data-ttu-id="69ec7-132">Existují dva další použití XAML, které je technicky možný.</span><span class="sxs-lookup"><span data-stu-id="69ec7-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="69ec7-133">Tato použití jsou však méně častý, protože je zbytečně podrobný:</span><span class="sxs-lookup"><span data-stu-id="69ec7-133">However, these usages are less common because they are unnecessarily verbose:</span></span>  

1.  <span data-ttu-id="69ec7-134">Syntaxe elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="69ec7-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2.  <span data-ttu-id="69ec7-135">Atribut syntaxi pomocí explicitní vlastnost člena pro inicializačního řetězce.</span><span class="sxs-lookup"><span data-stu-id="69ec7-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="69ec7-136">V implementaci rozhraní .NET Framework XAML Services zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.StaticExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="69ec7-136">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>  

<span data-ttu-id="69ec7-137">`x:Static` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="69ec7-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="69ec7-138">Všechna rozšíření značek XAML používá `{` a `}` znaků v syntaxi atributu, což je konvence, podle kterého procesoru XAML rozpozná, že rozšíření značek musí poskytovat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="69ec7-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="69ec7-139">Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek XAML přehled](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="69ec7-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="69ec7-140">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="69ec7-140">WPF Usage Notes</span></span>  
 <span data-ttu-id="69ec7-141">Výchozí obor názvů XAML můžete použít pro programování WPF obsahuje mnoho užitečných statické vlastnosti, a většina užitečné statické vlastnosti mají podporu například převaděče typů, které usnadňují použití bez nutnosti `{x:Static}` .</span><span class="sxs-lookup"><span data-stu-id="69ec7-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="69ec7-142">Pro statické vlastnosti je nutné mapovat předponu pro obor názvů XAML, pokud platí jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="69ec7-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>  
  
-   <span data-ttu-id="69ec7-143">Odkazujete na typ, který existuje ve WPF, ale není součástí výchozí obor názvů XAML pro WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="69ec7-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]).</span></span> <span data-ttu-id="69ec7-144">Toto je celkem běžné scénáře použití `x:Static`.</span><span class="sxs-lookup"><span data-stu-id="69ec7-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="69ec7-145">Například můžete použít `x:Static` odkaz s XAML mapování oboru názvů <xref:System> CLR obor názvů a mscorlib sestavení, aby bylo možné odkazovat statické vlastnosti <xref:System.Environment> třídy.</span><span class="sxs-lookup"><span data-stu-id="69ec7-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>  
  
-   <span data-ttu-id="69ec7-146">Typ se odkazuje z vlastního sestavení.</span><span class="sxs-lookup"><span data-stu-id="69ec7-146">You are referencing a type from a custom assembly.</span></span>  
  
-   <span data-ttu-id="69ec7-147">Typ, který existuje v sestavení WPF, se odkazuje, ale tento typ je v oboru názvů CLR, který nebyl namapován jako součást výchozí WPF XAML obor názvů.</span><span class="sxs-lookup"><span data-stu-id="69ec7-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="69ec7-148">Mapování oborů názvů CLR do výchozí obor názvů XAML pro WPF se provádí pomocí definice v různých sestaveních WPF (Další informace o tento koncept najdete v tématu [obory názvů XAML a mapování Namespace pro WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="69ec7-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="69ec7-149">Mapované na jiných oborů názvů CLR může existovat, pokud se tento obor názvů CLR skládá převážně z definice tříd, které nejsou určeny obvykle pro XAML, jako například <xref:System.Windows.Threading>.</span><span class="sxs-lookup"><span data-stu-id="69ec7-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>  
  
 <span data-ttu-id="69ec7-150">Další informace o tom, jak používat předpony a obory názvů XAML pro WPF naleznete v tématu [obory názvů XAML a mapování Namespace pro WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="69ec7-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69ec7-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69ec7-151">See also</span></span>
- [<span data-ttu-id="69ec7-152">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="69ec7-152">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)
- [<span data-ttu-id="69ec7-153">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="69ec7-153">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
