---
title: <settings> – Element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: a1733803d1f5a5bf64aeb69d0360cef3de3b3a69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096924"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="56c9d-102">\<Nastavení > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="56c9d-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="56c9d-103">Nakonfiguruje možnosti základní sítě pro <xref:System.Net?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="56c9d-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="56c9d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="56c9d-104">\<configuration></span></span>  
<span data-ttu-id="56c9d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="56c9d-105">\<system.net></span></span>  
<span data-ttu-id="56c9d-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="56c9d-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c9d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56c9d-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56c9d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="56c9d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="56c9d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="56c9d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56c9d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="56c9d-110">Attributes</span></span>  
 <span data-ttu-id="56c9d-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="56c9d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="56c9d-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="56c9d-112">Child Elements</span></span>  
  
|<span data-ttu-id="56c9d-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="56c9d-113">Element</span></span>|<span data-ttu-id="56c9d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="56c9d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56c9d-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="56c9d-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="56c9d-116">Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="56c9d-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="56c9d-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="56c9d-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="56c9d-118">Přizpůsobí parametrů webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="56c9d-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="56c9d-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="56c9d-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="56c9d-120">Umožňuje Internet Protocol verze 6 (IPv6) podporují.</span><span class="sxs-lookup"><span data-stu-id="56c9d-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="56c9d-121">\<performanceCounter > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="56c9d-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="56c9d-122">Umožňuje síťovým čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="56c9d-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="56c9d-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="56c9d-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="56c9d-124">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="56c9d-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="56c9d-125">soket</span><span class="sxs-lookup"><span data-stu-id="56c9d-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="56c9d-126">Určuje, zda operace soketu používat porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="56c9d-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="56c9d-127">\<webproxyscript – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="56c9d-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="56c9d-128">Konfiguruje vlastnosti souboru, který používá ke zjišťování webové proxy servery.</span><span class="sxs-lookup"><span data-stu-id="56c9d-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56c9d-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="56c9d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="56c9d-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="56c9d-130">Element</span></span>|<span data-ttu-id="56c9d-131">Popis</span><span class="sxs-lookup"><span data-stu-id="56c9d-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56c9d-132">system.net</span><span class="sxs-lookup"><span data-stu-id="56c9d-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="56c9d-133">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="56c9d-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56c9d-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56c9d-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="56c9d-135">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="56c9d-135">Configuration Files</span></span>  
 <span data-ttu-id="56c9d-136">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="56c9d-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c9d-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56c9d-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="56c9d-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="56c9d-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
