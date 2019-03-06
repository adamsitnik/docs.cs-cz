---
title: <remove> – element pro element bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: a04cca3e57af5cc422776c5b2444a140e86f98b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354255"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="392a0-102">\<Odebrat > – Element pro bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="392a0-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="392a0-103">Odebere ze seznamu obcházení proxy IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="392a0-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="392a0-104">\<Konfigurace > \\</span><span class="sxs-lookup"><span data-stu-id="392a0-104">\<configuration>\\</span></span>
<span data-ttu-id="392a0-105">\<system.net>\\</span><span class="sxs-lookup"><span data-stu-id="392a0-105">\<system.net>\\</span></span>
<span data-ttu-id="392a0-106">\<defaultProxy>\\</span><span class="sxs-lookup"><span data-stu-id="392a0-106">\<defaultProxy>\\</span></span>
<span data-ttu-id="392a0-107">\<bypasslist – > \\</span><span class="sxs-lookup"><span data-stu-id="392a0-107">\<bypasslist>\\</span></span>
<span data-ttu-id="392a0-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="392a0-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="392a0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="392a0-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="392a0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="392a0-110">Attributes and Elements</span></span>

<span data-ttu-id="392a0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="392a0-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="392a0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="392a0-112">Attributes</span></span>

|<span data-ttu-id="392a0-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="392a0-113">**Attribute**</span></span>|<span data-ttu-id="392a0-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="392a0-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="392a0-115">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="392a0-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="392a0-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="392a0-116">Child Elements</span></span>

<span data-ttu-id="392a0-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="392a0-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="392a0-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="392a0-118">Parent Elements</span></span>

|<span data-ttu-id="392a0-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="392a0-119">**Element**</span></span>|<span data-ttu-id="392a0-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="392a0-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="392a0-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="392a0-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="392a0-122">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="392a0-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="392a0-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="392a0-123">Remarks</span></span>

<span data-ttu-id="392a0-124">`remove` Element odebere regulární výrazy popisující IP adres nebo názvů DNS serverů v seznamu adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="392a0-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="392a0-125">Adresy byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii configuration.</span><span class="sxs-lookup"><span data-stu-id="392a0-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="392a0-126">Hodnota `address` atribut musí být regulární výraz, který popisuje sadu IP adres nebo názvů hostitele.</span><span class="sxs-lookup"><span data-stu-id="392a0-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="392a0-127">Další informace o formátování regulárních výrazů naleznete v tématu. [Regulárních výrazech .NET Frameworku](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="392a0-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="392a0-128">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="392a0-128">Configuration Files</span></span>

<span data-ttu-id="392a0-129">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="392a0-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="392a0-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="392a0-130">Example</span></span>

<span data-ttu-id="392a0-131">Následující příklad odebere všechny předchozí definice pro doménu společnosti adventure works.com a pak přidá do seznamu obcházení doménu contoso.com.</span><span class="sxs-lookup"><span data-stu-id="392a0-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="392a0-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="392a0-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="392a0-133">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="392a0-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
