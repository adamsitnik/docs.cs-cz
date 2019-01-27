---
title: Vlastní element pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 232ad7527e65fd38fa471cccc917752aef766a88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628835"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="61061-102">Vlastní element pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="61061-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="61061-103">Definuje nastavení, v části vlastní konfigurace, který je definován</span><span class="sxs-lookup"><span data-stu-id="61061-103">Defines settings in a custom configuration section that is defined by a</span></span> <section> <span data-ttu-id="61061-104">element a používá <xref:System.Configuration.SingleTagSectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="61061-104">element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="61061-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="61061-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="61061-106">&nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="61061-106">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="61061-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61061-107">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="61061-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="61061-108">Attributes</span></span>

<span data-ttu-id="61061-109">Atributy a hodnoty atributů jsou definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="61061-109">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="61061-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="61061-110">Parent element</span></span>

|     | <span data-ttu-id="61061-111">Popis</span><span class="sxs-lookup"><span data-stu-id="61061-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="61061-112">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="61061-112">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="61061-113">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61061-113">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="61061-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="61061-114">Child elements</span></span>

<span data-ttu-id="61061-115">Žádná</span><span class="sxs-lookup"><span data-stu-id="61061-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="61061-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61061-116">Remarks</span></span>

<span data-ttu-id="61061-117"> *\*\<SectionName >** prvek je prvek vlastní, určené [  *\*\<části >** ](~/docs/framework/configure-apps/file-schema/section-element.md) značku [  *\*\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="61061-117">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="61061-118">Konfigurační systém vrátí <xref:System.Collections.IDictionary> objektu při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="61061-118">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="61061-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="61061-119">Example</span></span>

<span data-ttu-id="61061-120">Následující příklad deklaruje vlastní prvek s názvem  **\<sampleSection >** , který obsahuje nastavení přečtou <xref:System.Configuration.SingleTagSectionHandler> třídy:</span><span class="sxs-lookup"><span data-stu-id="61061-120">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="61061-121">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="61061-121">Configuration file</span></span>

<span data-ttu-id="61061-122">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="61061-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="61061-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61061-123">See also</span></span>

- [<span data-ttu-id="61061-124">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61061-124">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
