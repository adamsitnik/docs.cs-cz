---
title: '&lt;Identifikátor URI&gt; – Element (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 48769298246dd71e040aac1c682e0fddfb5de89b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655540"
---
# <a name="lturigt-element-uri-settings"></a><span data-ttu-id="f3ef3-102">&lt;Identifikátor URI&gt; – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="f3ef3-102">&lt;Uri&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="f3ef3-103">Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="f3ef3-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="f3ef3-104">Schema Hierarchy</span><span class="sxs-lookup"><span data-stu-id="f3ef3-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="f3ef3-105">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="f3ef3-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="f3ef3-106">\<uri></span><span class="sxs-lookup"><span data-stu-id="f3ef3-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="f3ef3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3ef3-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3ef3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3ef3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3ef3-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3ef3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3ef3-110">Attributes</span></span>  
 <span data-ttu-id="f3ef3-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3ef3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3ef3-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3ef3-112">Child Elements</span></span>  
  
|<span data-ttu-id="f3ef3-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="f3ef3-113">**Element**</span></span>|<span data-ttu-id="f3ef3-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f3ef3-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3ef3-115">idn</span><span class="sxs-lookup"><span data-stu-id="f3ef3-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="f3ef3-116">Určuje, pokud analýza mezinárodních názvů domén (IDN) platí pro názvy domén.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="f3ef3-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="f3ef3-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="f3ef3-118">Určuje, pokud analýze International Resource Identifier (IRI) se použije k <xref:System.Uri> a určuje, zda by měl použít IRI pravidel pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="f3ef3-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="f3ef3-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="f3ef3-120">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3ef3-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3ef3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f3ef3-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="f3ef3-122">**Element**</span></span>|<span data-ttu-id="f3ef3-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f3ef3-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3ef3-124">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f3ef3-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f3ef3-125">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3ef3-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3ef3-126">Remarks</span></span>  
 <span data-ttu-id="f3ef3-127">`uri` Element obsahuje nastavení pro členy programu <xref:System.Uri> třídy používané třídami oboru <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="f3ef3-128">Nastavení konfigurace podpory pro IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ef3-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3ef3-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f3ef3-130">Popis</span><span class="sxs-lookup"><span data-stu-id="f3ef3-130">Description</span></span>  
 <span data-ttu-id="f3ef3-131">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýza IRI a názvy IDN.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="f3ef3-132">V příkladu rovněž vymaže všechna nastavení schéma a pak přidává podporu pro není uvozovací znaky oddělovače procentuálně zakódovaný cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="f3ef3-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f3ef3-133">Kód</span><span class="sxs-lookup"><span data-stu-id="f3ef3-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3ef3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3ef3-134">See also</span></span>
- [<span data-ttu-id="f3ef3-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f3ef3-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
