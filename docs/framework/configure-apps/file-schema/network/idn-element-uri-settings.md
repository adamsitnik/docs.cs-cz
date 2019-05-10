---
title: <idn> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 369decf8551c76293ca513b8a3e58b4142a74773
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592750"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="ad3f5-102">\<IDN > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="ad3f5-102">\<idn> Element (Uri Settings)</span></span>
<span data-ttu-id="ad3f5-103">Určuje, pokud analýza mezinárodních názvů domén (IDN) se použije na název domény.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="ad3f5-104">Schema Hierarchy</span><span class="sxs-lookup"><span data-stu-id="ad3f5-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="ad3f5-105">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="ad3f5-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="ad3f5-106">\<Identifikátor URI > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="ad3f5-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="ad3f5-107">\<idn></span><span class="sxs-lookup"><span data-stu-id="ad3f5-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="ad3f5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad3f5-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad3f5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ad3f5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ad3f5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad3f5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ad3f5-111">Attributes</span></span>  
  
|<span data-ttu-id="ad3f5-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="ad3f5-112">**Element**</span></span>|<span data-ttu-id="ad3f5-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ad3f5-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ad3f5-114">Určuje, že jestli parsování mezinárodních názvů domén (IDN) se použije pro název domény výchozí hodnota je none.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad3f5-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ad3f5-115">Child Elements</span></span>  
 <span data-ttu-id="ad3f5-116">Žádný</span><span class="sxs-lookup"><span data-stu-id="ad3f5-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad3f5-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ad3f5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ad3f5-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="ad3f5-118">**Element**</span></span>|<span data-ttu-id="ad3f5-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ad3f5-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ad3f5-120">uri</span><span class="sxs-lookup"><span data-stu-id="ad3f5-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="ad3f5-121">Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad3f5-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad3f5-122">Remarks</span></span>  
 <span data-ttu-id="ad3f5-123">Existující <xref:System.Uri> bylo rozšířeno třídy v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="ad3f5-124">3.0 SP1 a 2.0 SP1 s podporou International Resource identifikátory (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="ad3f5-125">Aktuální uživatelé neuvidí žádné změny v chování rozhraní .NET Framework 2.0, pokud výslovně povolit IRI a IDN podporovat.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="ad3f5-126">Tím se zajistí kompatibilitu aplikací se staršími verzemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ad3f5-127">Povolení podpory pro IRI, jsou požadovány následující dvě změny:</span><span class="sxs-lookup"><span data-stu-id="ad3f5-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="ad3f5-128">Přidejte následující řádek do souboru machine.config, v adresáři rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="ad3f5-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="ad3f5-129">Zadejte, jestli chcete parsování mezinárodních názvů domén (IDN) k názvu domény a určuje, zda by měl použít IRI pravidel pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="ad3f5-130">To můžete udělat v souboru machine.config nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="ad3f5-131">Existují tři možné hodnoty pro IDN v závislosti na servery DNS, které se používají:</span><span class="sxs-lookup"><span data-stu-id="ad3f5-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
- <span data-ttu-id="ad3f5-132">IDN, povoleno = All</span><span class="sxs-lookup"><span data-stu-id="ad3f5-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="ad3f5-133">Tato hodnota se převede názvy domén, Unicode na jejich ekvivalenty kódování Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
- <span data-ttu-id="ad3f5-134">IDN, povoleno = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="ad3f5-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="ad3f5-135">Tato hodnota se převede všechny názvy domén Unicode nejsou v místním intranetu používat kódování Punycode ekvivalenty (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="ad3f5-136">V tomto případě zpracování mezinárodních názvů na místní Intranet, které se používají pro intranetové servery DNS by měly podporovat překlad kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
- <span data-ttu-id="ad3f5-137">IDN, povoleno = None</span><span class="sxs-lookup"><span data-stu-id="ad3f5-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="ad3f5-138">Tato hodnota neprovede konverzi názvy domén, Unicode používat kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="ad3f5-139">Toto je výchozí hodnota je shodný se chování rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="ad3f5-140">Povolení IDN převede všechny popisky kódování Unicode v názvu domény na jejich ekvivalenty kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="ad3f5-141">Kódování Punycode názvy obsahovat pouze znaky ASCII a vždy začínají předponou xn –.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="ad3f5-142">Důvodem je k podpoře existujících serverů DNS na Internetu, protože většina servery DNS podporují jenom znaky ASCII (viz RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="ad3f5-143">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ad3f5-143">Configuration Files</span></span>  
 <span data-ttu-id="ad3f5-144">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad3f5-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad3f5-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ad3f5-146">Popis</span><span class="sxs-lookup"><span data-stu-id="ad3f5-146">Description</span></span>  
 <span data-ttu-id="ad3f5-147">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýza IRI a názvy IDN.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ad3f5-148">Kód</span><span class="sxs-lookup"><span data-stu-id="ad3f5-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad3f5-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad3f5-149">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="ad3f5-150">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ad3f5-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
