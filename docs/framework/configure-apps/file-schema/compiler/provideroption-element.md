---
title: '&lt;Hodnota providerOption&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7f4394afe81b03e44ea98514c15fb4bacafa49c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707576"
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="3ceab-102">&lt;Hodnota providerOption&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="3ceab-103">Určuje atributy verze kompilátoru poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="3ceab-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="3ceab-104">\<Konfigurace Element ></span><span class="sxs-lookup"><span data-stu-id="3ceab-104">\<configuration Element></span></span>  
<span data-ttu-id="3ceab-105">\<system.codedom Element></span><span class="sxs-lookup"><span data-stu-id="3ceab-105">\<system.codedom Element></span></span>  
<span data-ttu-id="3ceab-106">\<compilers Element></span><span class="sxs-lookup"><span data-stu-id="3ceab-106">\<compilers Element></span></span>  
<span data-ttu-id="3ceab-107">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-107">\<compiler> Element</span></span>  
<span data-ttu-id="3ceab-108">\<provideroption – > – Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ceab-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ceab-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ceab-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ceab-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ceab-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ceab-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ceab-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ceab-112">Attributes</span></span>  
  
|<span data-ttu-id="3ceab-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ceab-113">Attribute</span></span>|<span data-ttu-id="3ceab-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3ceab-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="3ceab-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3ceab-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="3ceab-116">Určuje název možnosti; například "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="3ceab-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="3ceab-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3ceab-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="3ceab-118">Určuje hodnotu parametru; například "v3.5".</span><span class="sxs-lookup"><span data-stu-id="3ceab-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ceab-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ceab-119">Child Elements</span></span>  
 <span data-ttu-id="3ceab-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ceab-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ceab-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ceab-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3ceab-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ceab-122">Element</span></span>|<span data-ttu-id="3ceab-123">Popis</span><span class="sxs-lookup"><span data-stu-id="3ceab-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ceab-124">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="3ceab-125">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ceab-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="3ceab-126">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="3ceab-127">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="3ceab-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="3ceab-128">\<Kompilátory > – Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="3ceab-129">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více `<compiler>` elementy.</span><span class="sxs-lookup"><span data-stu-id="3ceab-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="3ceab-130">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="3ceab-131">Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="3ceab-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ceab-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ceab-132">Remarks</span></span>  
 <span data-ttu-id="3ceab-133">V rozhraní .NET Framework verze 3.5, poskytovatelů kód Code Document Object Model (CodeDOM) může podporovat možnosti specifické pro zprostředkovatele s použitím `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3ceab-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="3ceab-134">Rozhraní .NET Framework 3.5 zahrnuje aktualizované sestavení rozhraní .NET Framework 2.0 a poskytuje nové sestavení verze 3.5, které obsahují nové typy.</span><span class="sxs-lookup"><span data-stu-id="3ceab-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="3ceab-135">Poskytovatelé kód Microsoft C# a Visual Basic jsou obsaženy v sestavení rozhraní .NET Framework 2.0, ale byla aktualizována o podporu kompilátory verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="3ceab-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="3ceab-136">Ve výchozím nastavení poskytovatelů aktualizovaný kód generování kódu pro verze 2.0 kompilátory.</span><span class="sxs-lookup"><span data-stu-id="3ceab-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="3ceab-137">Můžete použít `<providerOption>` prvek, který chcete změnit cílovou verzi kompilátoru 3.5.</span><span class="sxs-lookup"><span data-stu-id="3ceab-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="3ceab-138">Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v3.5" pro `value` atribut.</span><span class="sxs-lookup"><span data-stu-id="3ceab-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="3ceab-139">Musí předcházet číslo verze, s malá "v".</span><span class="sxs-lookup"><span data-stu-id="3ceab-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="3ceab-140">Specifikace verze můžete globální provést přidáním `<providerOption>` prvků rozhraní .NET Framework 2.0 Machine.config nebo kořenový soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="3ceab-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="3ceab-141">Pokud aktualizujete verzi kompilátoru výchozí až 3.5 v souboru Machine.config, můžete změnit ji zpět do 2.0 na základě jednotlivých aplikací s použitím `<providerOption>` prvku v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ceab-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="3ceab-142">Implementátoři poskytovatele codeDOM kód může zpracovávat vlastní možnosti tím, že poskytuje konstruktor s daným počtem `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="3ceab-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ceab-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ceab-143">Example</span></span>  
 <span data-ttu-id="3ceab-144">Následující příklad ukazuje, jak zadat verzi 3.5 zprostředkovatele kódu C# má být použita.</span><span class="sxs-lookup"><span data-stu-id="3ceab-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ceab-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ceab-145">See also</span></span>
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="3ceab-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3ceab-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="3ceab-147">\<Kompilátory > – Element</span><span class="sxs-lookup"><span data-stu-id="3ceab-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [<span data-ttu-id="3ceab-148">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="3ceab-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [<span data-ttu-id="3ceab-149">Kompilátor – Element pro kompilátory compilation (schéma nastavení technologie ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="3ceab-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
