---
title: '&lt;Vlastnost assemblyIdentity&gt; – Element pro &lt;modulu runtime&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b32e0da554622eb84b5569b5a1db04447fdc2940
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612553"
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a><span data-ttu-id="1749e-102">&lt;Vlastnost assemblyIdentity&gt; – Element pro &lt;modulu runtime&gt;</span><span class="sxs-lookup"><span data-stu-id="1749e-102">&lt;assemblyIdentity&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="1749e-103">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="1749e-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="1749e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="1749e-104">\<configuration></span></span>  
<span data-ttu-id="1749e-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="1749e-105">\<runtime></span></span>  
<span data-ttu-id="1749e-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="1749e-106">\<assemblyBinding></span></span>  
<span data-ttu-id="1749e-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="1749e-107">\<dependentAssembly></span></span>  
<span data-ttu-id="1749e-108">\<Vlastnost assemblyIdentity ></span><span class="sxs-lookup"><span data-stu-id="1749e-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1749e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1749e-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1749e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1749e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1749e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1749e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1749e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1749e-112">Attributes</span></span>  
  
|<span data-ttu-id="1749e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1749e-113">Attribute</span></span>|<span data-ttu-id="1749e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1749e-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="1749e-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1749e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="1749e-116">Název sestavení</span><span class="sxs-lookup"><span data-stu-id="1749e-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="1749e-117">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1749e-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1749e-118">Řetězec, který určuje jazyk a zemi/oblast sestavení.</span><span class="sxs-lookup"><span data-stu-id="1749e-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="1749e-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1749e-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1749e-120">Šestnáctková hodnota, která udává silný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="1749e-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="1749e-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1749e-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1749e-122">Jedna z hodnot "x86", "amd64", "msil" nebo "ia64" zadání sestavení, která obsahuje kód závislý na procesoru na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="1749e-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="1749e-123">Hodnoty nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="1749e-123">The values are not case-sensitive.</span></span> <span data-ttu-id="1749e-124">Pokud je atribut přiřadit jinou hodnotu, celý `<assemblyIdentity>` prvek je ignorován.</span><span class="sxs-lookup"><span data-stu-id="1749e-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="1749e-125">Viz <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="1749e-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="1749e-126">Vlastnost processorArchitecture atribut</span><span class="sxs-lookup"><span data-stu-id="1749e-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="1749e-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1749e-127">Value</span></span>|<span data-ttu-id="1749e-128">Popis</span><span class="sxs-lookup"><span data-stu-id="1749e-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="1749e-129">AMD pouze architektura x86 – x 64.</span><span class="sxs-lookup"><span data-stu-id="1749e-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="1749e-130">Pouze Intel Itanium architekturu.</span><span class="sxs-lookup"><span data-stu-id="1749e-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="1749e-131">Neutrální s ohledem na procesor a bits slova.</span><span class="sxs-lookup"><span data-stu-id="1749e-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="1749e-132">32-bit x86 procesor, buď native nebo ve Windows v prostředí Windows (WOW) na 64bitové platformě.</span><span class="sxs-lookup"><span data-stu-id="1749e-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1749e-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1749e-133">Child Elements</span></span>  
 <span data-ttu-id="1749e-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="1749e-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1749e-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1749e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1749e-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="1749e-136">Element</span></span>|<span data-ttu-id="1749e-137">Popis</span><span class="sxs-lookup"><span data-stu-id="1749e-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="1749e-138">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="1749e-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="1749e-139">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1749e-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="1749e-140">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="1749e-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="1749e-141">Použijte jednu `<dependentAssembly>` – element pro každé sestavení.</span><span class="sxs-lookup"><span data-stu-id="1749e-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="1749e-142">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1749e-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1749e-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1749e-143">Remarks</span></span>  
 <span data-ttu-id="1749e-144">Každý  **\<dependentAssembly >** element musí mít jeden  **\<assemblyIdentity >** podřízený element.</span><span class="sxs-lookup"><span data-stu-id="1749e-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="1749e-145">Pokud `processorArchitecture` atribut je k dispozici, `<assemblyIdentity>` element platí pouze pro sestavení s odpovídající architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="1749e-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="1749e-146">Pokud `processorArchitecture` atribut není k dispozici, `<assemblyIdentity>` element můžete použít pro sestavení jakékoli architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="1749e-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="1749e-147">Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, jejichž cílem dvě různé dvě architektury procesoru, a jejichž verze ještě nebyla zachována synchronizována. Když se aplikace spustí na x86 platformy první `<assemblyIdentity>` vztahuje k elementu a druhý je ignorován.</span><span class="sxs-lookup"><span data-stu-id="1749e-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="1749e-148">Pokud aplikace provádí na platformě jiné než x86 nebo ia64, obě jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="1749e-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="1749e-149">Pokud konfigurační soubor obsahuje `<assemblyIdentity>` element bez `processorArchitecture` atribut a neobsahuje element, který odpovídá platformě elementu bez `processorArchitecture` atribut se používá.</span><span class="sxs-lookup"><span data-stu-id="1749e-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1749e-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="1749e-150">Example</span></span>  
 <span data-ttu-id="1749e-151">Následující příklad ukazuje, jak poskytnout informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="1749e-151">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1749e-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="1749e-152">See Also</span></span>  
- [<span data-ttu-id="1749e-153">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="1749e-153">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="1749e-154">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="1749e-154">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="1749e-155">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="1749e-155">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
