---
title: <defaultProxy> – Element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: ce08dadb0fb7b986c0573b1514f9ecbbe2961c3a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228339"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="21cdc-102">\<defaultProxy > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="21cdc-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="21cdc-103">Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="21cdc-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="21cdc-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="21cdc-104">\<configuration></span></span>  
<span data-ttu-id="21cdc-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="21cdc-105">\<system.net></span></span>  
<span data-ttu-id="21cdc-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="21cdc-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cdc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21cdc-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21cdc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21cdc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="21cdc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21cdc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21cdc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="21cdc-110">Attributes</span></span>  
  
|**<span data-ttu-id="21cdc-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="21cdc-111">Element</span></span>**|**<span data-ttu-id="21cdc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="21cdc-112">Description</span></span>**|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="21cdc-113">Určuje, zda se používá webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="21cdc-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="21cdc-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="21cdc-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="21cdc-115">Určuje, zda výchozí přihlašovací údaje pro tohoto hostitele se používají pro přístup webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="21cdc-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="21cdc-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="21cdc-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21cdc-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21cdc-117">Child Elements</span></span>  
  
|**<span data-ttu-id="21cdc-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="21cdc-118">Element</span></span>**|**<span data-ttu-id="21cdc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="21cdc-119">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="21cdc-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="21cdc-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="21cdc-121">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="21cdc-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="21cdc-122">module</span><span class="sxs-lookup"><span data-stu-id="21cdc-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="21cdc-123">Přidá nový modul proxy serveru do aplikace.</span><span class="sxs-lookup"><span data-stu-id="21cdc-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="21cdc-124">proxy server</span><span class="sxs-lookup"><span data-stu-id="21cdc-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="21cdc-125">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="21cdc-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21cdc-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21cdc-126">Parent Elements</span></span>  
  
|**<span data-ttu-id="21cdc-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="21cdc-127">Element</span></span>**|**<span data-ttu-id="21cdc-128">Popis</span><span class="sxs-lookup"><span data-stu-id="21cdc-128">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="21cdc-129">system.net</span><span class="sxs-lookup"><span data-stu-id="21cdc-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="21cdc-130">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="21cdc-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21cdc-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21cdc-131">Remarks</span></span>  
 <span data-ttu-id="21cdc-132">Pokud defaultProxy – element je prázdný, použije se nastavení proxy serveru z aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="21cdc-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="21cdc-133">Toto chování se liší od verze 1.1 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21cdc-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="21cdc-134">Pokud je vyvolána výjimka [modulu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) prvek určuje neveřejný typ, typ není odvozený od <xref:System.Net.IWebProxy> došlo k výjimce z výchozího konstruktoru tohoto objektu třídy, nebo došlo k výjimce při načítání systému zadat výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="21cdc-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="21cdc-135"><xref:System.Exception.InnerException%2A> Vlastnosti výjimky by měl mít další informace o hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="21cdc-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="21cdc-136">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="21cdc-136">Configuration Files</span></span>  
 <span data-ttu-id="21cdc-137">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="21cdc-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21cdc-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="21cdc-138">Example</span></span>  
 <span data-ttu-id="21cdc-139">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="21cdc-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21cdc-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21cdc-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="21cdc-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="21cdc-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
