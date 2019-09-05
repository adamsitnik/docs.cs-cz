---
title: Element <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581b19cf74dcb5c2d5c4a549847629503fe0b6ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252361"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="18c5a-102">\<qualifyAssembly – element ></span><span class="sxs-lookup"><span data-stu-id="18c5a-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="18c5a-103">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="18c5a-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="18c5a-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="18c5a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="18c5a-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="18c5a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="18c5a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="18c5a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="18c5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly>**</span><span class="sxs-lookup"><span data-stu-id="18c5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18c5a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18c5a-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18c5a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="18c5a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="18c5a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="18c5a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18c5a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="18c5a-111">Attributes</span></span>  
  
|<span data-ttu-id="18c5a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="18c5a-112">Attribute</span></span>|<span data-ttu-id="18c5a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="18c5a-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="18c5a-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="18c5a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="18c5a-115">Určuje částečný název sestavení, jak se zobrazí v kódu.</span><span class="sxs-lookup"><span data-stu-id="18c5a-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="18c5a-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="18c5a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="18c5a-117">Určuje úplný název sestavení, který se zobrazí v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="18c5a-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18c5a-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="18c5a-118">Child Elements</span></span>  
 <span data-ttu-id="18c5a-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="18c5a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18c5a-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="18c5a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="18c5a-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="18c5a-121">Element</span></span>|<span data-ttu-id="18c5a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="18c5a-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="18c5a-123">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="18c5a-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="18c5a-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18c5a-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="18c5a-125">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="18c5a-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18c5a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18c5a-126">Remarks</span></span>  
 <span data-ttu-id="18c5a-127"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> Volání metody pomocí částečných názvů sestavení způsobí, že modul CLR (Common Language Runtime) hledá sestavení pouze v základním adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="18c5a-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="18c5a-128">Použijte **qualifyAssembly > element v konfiguračním souboru aplikace k poskytnutí úplných informací o sestavení (název, verze, token veřejného klíče a jazyková verze) a způsobí, že modul CLR (Common Language Runtime) vyhledá sestavení v \<** globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="18c5a-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="18c5a-129">Atribut **FullName** musí zahrnovat čtyři pole identity sestavení: název, verze, token veřejného klíče a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="18c5a-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="18c5a-130">Atribut **Partial** musí odkazovat na sestavení částečně.</span><span class="sxs-lookup"><span data-stu-id="18c5a-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="18c5a-131">Je nutné zadat alespoň textový název sestavení (Nejběžnější případ), ale můžete také zahrnout verze, token veřejného klíče nebo jazykovou verzi (nebo libovolnou kombinaci čtyř, ale ne všech čtyř).</span><span class="sxs-lookup"><span data-stu-id="18c5a-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="18c5a-132">Parametr **Partial** se musí shodovat s názvem zadaným ve vašem volání.</span><span class="sxs-lookup"><span data-stu-id="18c5a-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="18c5a-133">Například nemůžete zadat `"math"` jako atribut **Partial** do konfiguračního souboru a volat `Assembly.Load("math, Version=3.3.3.3")` do kódu.</span><span class="sxs-lookup"><span data-stu-id="18c5a-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18c5a-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="18c5a-134">Example</span></span>  
 <span data-ttu-id="18c5a-135">Následující příklad logicky přepíná volání `Assembly.Load("math")` do. `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`</span><span class="sxs-lookup"><span data-stu-id="18c5a-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18c5a-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18c5a-136">See also</span></span>

- [<span data-ttu-id="18c5a-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="18c5a-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="18c5a-138">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="18c5a-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="18c5a-139">[Odkazy na částečné sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="18c5a-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
