---
title: Element <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: 7cdea10cc6e0562f6062470240b01743aa439bde
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658942"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="170d4-102">\<bindingRedirect – element ></span><span class="sxs-lookup"><span data-stu-id="170d4-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="170d4-103">Přesměruje jednu verzi sestavení k jiné.</span><span class="sxs-lookup"><span data-stu-id="170d4-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="170d4-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="170d4-104">\<configuration></span></span>  
<span data-ttu-id="170d4-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="170d4-105">\<runtime></span></span>  
<span data-ttu-id="170d4-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="170d4-106">\<assemblyBinding></span></span>  
<span data-ttu-id="170d4-107">\<> dependentAssembly</span><span class="sxs-lookup"><span data-stu-id="170d4-107">\<dependentAssembly></span></span>  
<span data-ttu-id="170d4-108">\<bindingRedirect></span><span class="sxs-lookup"><span data-stu-id="170d4-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="170d4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="170d4-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="170d4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="170d4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="170d4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="170d4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="170d4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="170d4-112">Attributes</span></span>  
  
|<span data-ttu-id="170d4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="170d4-113">Attribute</span></span>|<span data-ttu-id="170d4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="170d4-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="170d4-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="170d4-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="170d4-116">Určuje verzi sestavení, která byla původně požadována.</span><span class="sxs-lookup"><span data-stu-id="170d4-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="170d4-117">Formát čísla verze sestavení je *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="170d4-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="170d4-118">Platné hodnoty pro jednotlivé části tohoto čísla verze jsou 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="170d4-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="170d4-119">Můžete také zadat rozsah verzí v tomto formátu:</span><span class="sxs-lookup"><span data-stu-id="170d4-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="170d4-120">*n. n. n. n. n-n. n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="170d4-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="170d4-121">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="170d4-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="170d4-122">Určuje verzi sestavení, která se má použít místo původně požadované verze ve formátu: *n. n. n.* n</span><span class="sxs-lookup"><span data-stu-id="170d4-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="170d4-123">Tato hodnota může specifikovat starší verzi než `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="170d4-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="170d4-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="170d4-124">Child Elements</span></span>  
  
|<span data-ttu-id="170d4-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="170d4-125">Element</span></span>|<span data-ttu-id="170d4-126">Popis</span><span class="sxs-lookup"><span data-stu-id="170d4-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="170d4-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="170d4-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="170d4-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="170d4-128">Parent Elements</span></span>  
  
|<span data-ttu-id="170d4-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="170d4-129">Element</span></span>|<span data-ttu-id="170d4-130">Popis</span><span class="sxs-lookup"><span data-stu-id="170d4-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="170d4-131">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="170d4-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="170d4-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="170d4-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="170d4-133">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="170d4-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="170d4-134">Používá pro jednotlivá sestavení jeden prvek dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="170d4-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="170d4-135">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="170d4-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="170d4-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="170d4-136">Remarks</span></span>  
 <span data-ttu-id="170d4-137">Při sestavování aplikace rozhraní .NET Framework v rámci sestavení se silným názvem používá aplikace ve výchozím nastavení při spuštění zmíněnou verzi, a to i tehdy, pokud je k dispozici nová verze.</span><span class="sxs-lookup"><span data-stu-id="170d4-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="170d4-138">Aplikaci však můžete nastavit tak, aby se spustila v rámci novější verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="170d4-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="170d4-139">Podrobnosti o tom, jak modul runtime používá tyto soubory k určení verze sestavení, která se má použít, najdete v tématu [jak modul runtime vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="170d4-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="170d4-140">Můžete přesměrovat více než jednu verzi sestavení zahrnutím `bindingRedirect` více prvků `dependentAssembly` do prvku.</span><span class="sxs-lookup"><span data-stu-id="170d4-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="170d4-141">Můžete také vytvořit přesměrování z novější verze na starší verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="170d4-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="170d4-142">Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="170d4-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="170d4-143">To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran.</span><span class="sxs-lookup"><span data-stu-id="170d4-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="170d4-144">Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>na.</span><span class="sxs-lookup"><span data-stu-id="170d4-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="170d4-145">Další informace naleznete v tématu [oprávnění zabezpečení přesměrování vazby sestavení](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="170d4-145">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="170d4-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="170d4-146">Example</span></span>  
 <span data-ttu-id="170d4-147">Následující příklad znázorňuje způsob přesměrování jedné verze sestavení na jinou.</span><span class="sxs-lookup"><span data-stu-id="170d4-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="170d4-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="170d4-148">See also</span></span>

- [<span data-ttu-id="170d4-149">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="170d4-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="170d4-150">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="170d4-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="170d4-151">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="170d4-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
