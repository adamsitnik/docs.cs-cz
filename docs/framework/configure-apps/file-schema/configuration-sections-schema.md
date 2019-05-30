---
title: Schéma konfigurace oddílů
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c7559a95099608ea462c838591ddb43e18d8f80c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301237"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="ebae8-102">Schéma konfigurace oddílů</span><span class="sxs-lookup"><span data-stu-id="ebae8-102">Configuration sections schema</span></span>

<span data-ttu-id="ebae8-103">Schéma konfigurace oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="ebae8-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="ebae8-104">Obecné informace o konfiguračních souborech a schémat, naleznete v tématu [schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebae8-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="ebae8-105">[ **\<Konfigurace >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ebae8-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="ebae8-106">[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="ebae8-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="ebae8-107">[ **\<Vymazat >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="ebae8-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="ebae8-108">[ **\<remove>** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="ebae8-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="ebae8-109">[ **\<část >** ](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="ebae8-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="ebae8-110"> *\*\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="ebae8-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="ebae8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ebae8-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ebae8-112"> *\*\<Vymazat >** pro  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="ebae8-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="ebae8-113">Vymaže všechny dříve definované oddíly a skupin oddílů.</span><span class="sxs-lookup"><span data-stu-id="ebae8-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="ebae8-114"> *\*\<Vymazat >** </span><span class="sxs-lookup"><span data-stu-id="ebae8-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="ebae8-115">Vymaže všechny dříve definované oddíly a skupin oddílů.</span><span class="sxs-lookup"><span data-stu-id="ebae8-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="ebae8-116"> *\*\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="ebae8-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="ebae8-117">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ebae8-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="ebae8-118"> *\*\<Odebrat >** pro  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="ebae8-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="ebae8-119">Odstraní předdefinované oddílu nebo skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="ebae8-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="ebae8-120"> *\*\<část >** pro  *\*\<configSections >** a  *\*\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="ebae8-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="ebae8-121">Obsahuje deklarace oddíl konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ebae8-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="ebae8-122"> *\*\<sectionGroup>** for *\*\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="ebae8-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="ebae8-123">Definuje obor názvů pro oddíly konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ebae8-123">Defines a namespace for configuration sections.</span></span> |
