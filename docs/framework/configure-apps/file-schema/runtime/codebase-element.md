---
title: '&lt;základ kódu&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7e52899a953644fc3cf7189bf557f5ade2863161
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613151"
---
# <a name="ltcodebasegt-element"></a><span data-ttu-id="81690-102">&lt;základ kódu&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="81690-102">&lt;codeBase&gt; Element</span></span>
<span data-ttu-id="81690-103">Určuje, kde najít sestavení modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="81690-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="81690-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="81690-104">\<configuration></span></span>  
<span data-ttu-id="81690-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="81690-105">\<runtime></span></span>  
<span data-ttu-id="81690-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="81690-106">\<assemblyBinding></span></span>  
<span data-ttu-id="81690-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="81690-107">\<dependentAssembly></span></span>  
<span data-ttu-id="81690-108">\<codeBase ></span><span class="sxs-lookup"><span data-stu-id="81690-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81690-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81690-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81690-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="81690-110">Attributes and Elements</span></span>  
 <span data-ttu-id="81690-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="81690-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81690-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="81690-112">Attributes</span></span>  
  
|<span data-ttu-id="81690-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="81690-113">Attribute</span></span>|<span data-ttu-id="81690-114">Popis</span><span class="sxs-lookup"><span data-stu-id="81690-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="81690-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="81690-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="81690-116">Určuje adresu URL, kde modul runtime může najít zadanou verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="81690-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="81690-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="81690-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="81690-118">Určuje verzi sestavení, ve kterém základu kódu se vztahuje na.</span><span class="sxs-lookup"><span data-stu-id="81690-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="81690-119">Číslo verze sestavení má *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="81690-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="81690-120">verze atribut</span><span class="sxs-lookup"><span data-stu-id="81690-120">version Attribute</span></span>  
  
|<span data-ttu-id="81690-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="81690-121">Value</span></span>|<span data-ttu-id="81690-122">Popis</span><span class="sxs-lookup"><span data-stu-id="81690-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81690-123">Platné hodnoty pro každou část čísla verze jsou 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="81690-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="81690-124">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="81690-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81690-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="81690-125">Child Elements</span></span>  
 <span data-ttu-id="81690-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="81690-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81690-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="81690-127">Parent Elements</span></span>  
  
|<span data-ttu-id="81690-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="81690-128">Element</span></span>|<span data-ttu-id="81690-129">Popis</span><span class="sxs-lookup"><span data-stu-id="81690-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="81690-130">Definuje kolekci zprostředkovatelů sestavení používá ke kompilaci soubory vlastních prostředků.</span><span class="sxs-lookup"><span data-stu-id="81690-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="81690-131">Můžete mít libovolný počet poskytovatelé sestavení.</span><span class="sxs-lookup"><span data-stu-id="81690-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="81690-132">Nakonfiguruje všechna nastavení kompilace, která používá ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="81690-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="81690-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81690-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="81690-134">Určuje kořenový element části o konfiguraci technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="81690-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81690-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81690-135">Remarks</span></span>  
 <span data-ttu-id="81690-136">Pro modul runtime pro použití  **\<codeBase >** nastavení v konfiguračním souboru počítače nebo soubor zásad vydavatele, soubor musíte také vytvořit přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="81690-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="81690-137">Konfigurační soubory aplikace mohou mít nastavení základu kódu bez přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="81690-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="81690-138">Po určení verze sestavení, které chcete použít, se vztahuje nastavení základu kódu ze souboru, který určuje verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="81690-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="81690-139">Pokud je uveden žádný základ kódu, modul runtime sondy pro sestavení obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="81690-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="81690-140">Pokud sestavení se silným názvem, nastavení základu kódu může být kdekoli na místním intranetu nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="81690-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="81690-141">Je-li soukromé sestavení je sestavení, nastavení základu kódu musí být cesta relativní k adresáři vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="81690-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="81690-142">Pro sestavení bez silného názvu, verze ignorovány a používá zavaděč první výskyt \<codebase > uvnitř \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="81690-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="81690-143">Pokud existuje položka v konfiguračním souboru aplikace, který přesměrovává vazby na jiné sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neshoduje požadavek na vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="81690-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81690-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="81690-144">Example</span></span>  
 <span data-ttu-id="81690-145">Následující příklad ukazuje, jak určit, kde najít sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="81690-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81690-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="81690-146">See Also</span></span>  
- [<span data-ttu-id="81690-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="81690-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="81690-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="81690-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="81690-149">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="81690-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
- [<span data-ttu-id="81690-150">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="81690-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
