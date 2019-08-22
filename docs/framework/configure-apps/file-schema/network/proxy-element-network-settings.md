---
title: <proxy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: a183c4160c4cd55b05c5c23f7a10e3a1d1c74ea4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659292"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="47388-102">\<> – element proxy (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="47388-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="47388-103">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="47388-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="47388-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="47388-104">\<configuration></span></span>  
<span data-ttu-id="47388-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="47388-105">\<system.net></span></span>  
<span data-ttu-id="47388-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="47388-106">\<defaultProxy></span></span>  
<span data-ttu-id="47388-107">\<proxy></span><span class="sxs-lookup"><span data-stu-id="47388-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47388-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47388-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47388-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="47388-109">Attributes and Elements</span></span>  
 <span data-ttu-id="47388-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="47388-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47388-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="47388-111">Attributes</span></span>  
  
|<span data-ttu-id="47388-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="47388-112">**Attribute**</span></span>|<span data-ttu-id="47388-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="47388-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="47388-114">Určuje, jestli se proxy server automaticky detekuje.</span><span class="sxs-lookup"><span data-stu-id="47388-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="47388-115">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="47388-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="47388-116">Určuje, jestli se proxy server pro místní prostředky obejít.</span><span class="sxs-lookup"><span data-stu-id="47388-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="47388-117">Místní prostředky zahrnují místní server`http://localhost`(, `http://loopback`, nebo `http://127.0.0.1`) a identifikátor URI bez tečky (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="47388-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="47388-118">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="47388-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="47388-119">Určuje identifikátor URI proxy serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="47388-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="47388-120">Určuje umístění konfiguračního skriptu.</span><span class="sxs-lookup"><span data-stu-id="47388-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="47388-121">Nepoužívejte `bypassonlocal` atribut s tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="47388-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="47388-122">Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="47388-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="47388-123">Pokud je nastaveno `true`na, budou následující atributy přepsat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="47388-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="47388-124">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="47388-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47388-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="47388-125">Child Elements</span></span>  
 <span data-ttu-id="47388-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="47388-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47388-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="47388-127">Parent Elements</span></span>  
  
|<span data-ttu-id="47388-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="47388-128">**Element**</span></span>|<span data-ttu-id="47388-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="47388-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="47388-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="47388-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="47388-131">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="47388-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="47388-132">Textová hodnota</span><span class="sxs-lookup"><span data-stu-id="47388-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47388-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47388-133">Remarks</span></span>  
 <span data-ttu-id="47388-134">`proxy` Prvek definuje proxy server pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47388-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="47388-135">Pokud tento prvek v konfiguračním souboru chybí, .NET Framework použije nastavení proxy serveru v Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="47388-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="47388-136">Hodnota `proxyaddress` atributu musí být ve správném formátu (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="47388-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="47388-137">`scriptLocation` Atribut odkazuje na automatické zjišťování skriptů konfigurace proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="47388-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="47388-138">Třída se pokusí najít konfigurační skript (obvykle nazvaný WPAD. dat), pokud je v aplikaci Internet Explorer vybraná možnost **použít skript automatické konfigurace.** <xref:System.Net.WebProxy></span><span class="sxs-lookup"><span data-stu-id="47388-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="47388-139">Pokud `bypassonlocal` je nastavená na libovolnou hodnotu `scriptLocation` , ignoruje se.</span><span class="sxs-lookup"><span data-stu-id="47388-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="47388-140">`usesystemdefault` Použijte atribut pro aplikace .NET Framework verze 1,1, které migrují na verzi 2,0.</span><span class="sxs-lookup"><span data-stu-id="47388-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="47388-141">Pokud `proxyaddress` atribut specifikuje neplatný výchozí proxy server, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="47388-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="47388-142"><xref:System.Exception.InnerException%2A> Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="47388-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="47388-143">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="47388-143">Configuration Files</span></span>  
 <span data-ttu-id="47388-144">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="47388-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="47388-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="47388-145">Example</span></span>  
 <span data-ttu-id="47388-146">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup.</span><span class="sxs-lookup"><span data-stu-id="47388-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47388-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47388-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="47388-148">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="47388-148">Network Settings Schema</span></span>](index.md)
