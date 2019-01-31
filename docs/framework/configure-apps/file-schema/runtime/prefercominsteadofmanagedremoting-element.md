---
title: Element <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f143429c1f579ae98a03fd69a8cf3dcdd26ad2c2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260357"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="d4096-102">\<PreferComInsteadOfManagedRemoting> Element</span><span class="sxs-lookup"><span data-stu-id="d4096-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="d4096-103">Určuje, zda modul runtime použijí komunikace s objekty COM místo vzdálené komunikace pro všechna volání napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4096-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="d4096-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d4096-104">\<configuration></span></span>  
<span data-ttu-id="d4096-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="d4096-105">\<runtime></span></span>  
<span data-ttu-id="d4096-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="d4096-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4096-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4096-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4096-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4096-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d4096-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4096-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4096-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4096-110">Attributes</span></span>  
  
|<span data-ttu-id="d4096-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4096-111">Attribute</span></span>|<span data-ttu-id="d4096-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d4096-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d4096-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d4096-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d4096-114">Určuje, zda modul runtime použije komunikace s objekty COM místo vzdálené komunikace přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="d4096-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d4096-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="d4096-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d4096-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d4096-116">Value</span></span>|<span data-ttu-id="d4096-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d4096-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d4096-118">Modul runtime bude používat vzdálenou komunikaci přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="d4096-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="d4096-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="d4096-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d4096-120">Modul runtime použije komunikace s objekty COM přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="d4096-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4096-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4096-121">Child Elements</span></span>  
 <span data-ttu-id="d4096-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4096-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4096-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4096-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d4096-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4096-124">Element</span></span>|<span data-ttu-id="d4096-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d4096-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d4096-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4096-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d4096-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d4096-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4096-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4096-128">Remarks</span></span>  
 <span data-ttu-id="d4096-129">Při nastavení `enabled` atribut `true`, modul runtime chová takto:</span><span class="sxs-lookup"><span data-stu-id="d4096-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="d4096-130">Modul runtime nevolá [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní, kdy [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) rozhraní přejde do domény prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d4096-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="d4096-131">Místo toho vytvoří [obálka volatelná za běhu](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) kolem objektu.</span><span class="sxs-lookup"><span data-stu-id="d4096-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="d4096-132">Modul runtime E_NOINTERFACE vrátí, když přijme `QueryInterface` volání pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní pro všechny [obálka volatelná aplikacemi COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW), který se vytvořil v této doméně.</span><span class="sxs-lookup"><span data-stu-id="d4096-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="d4096-133">Tyto dvě chování Ujistěte se, že všechna volání přes COM rozhraní mezi spravovanými objekty napříč použití hranice domény aplikace modelu COM a interoperabilitu COM místo vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="d4096-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4096-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4096-134">Example</span></span>  
 <span data-ttu-id="d4096-135">Následující příklad ukazuje, jak určit, že modul runtime by měl používat COM interop přes hranice izolace:</span><span class="sxs-lookup"><span data-stu-id="d4096-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4096-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4096-136">See also</span></span>
- [<span data-ttu-id="d4096-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d4096-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d4096-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d4096-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
