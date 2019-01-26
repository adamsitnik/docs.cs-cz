---
title: Schéma konfiguračního souboru pro rozhraní .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: 37600331ac52add60a98c9fd573591dc34b94f5f
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083961"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="27304-102">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="27304-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="27304-103">Konfigurační soubory jsou standardní soubory XML, které můžete použít ke změně nastavení a nastavit zásady pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="27304-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="27304-104">Schéma konfigurace rozhraní .NET Framework obsahuje prvky používané v konfiguračních souborech pro řízení chování aplikací.</span><span class="sxs-lookup"><span data-stu-id="27304-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="27304-105">Obsah této části odráží hierarchii schématu pro spuštění, runtime, síť a další typy nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="27304-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="27304-106">Informace o typech, formátu a umístění konfiguračních souborů, najdete v článku [konfigurace aplikace](~/docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="27304-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="27304-107">Seznamte se s XML Pokud chcete upravovat konfigurační soubory přímo.</span><span class="sxs-lookup"><span data-stu-id="27304-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27304-108">XML tagy a atributy v konfiguračních souborech jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="27304-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="27304-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="27304-109">In this section</span></span>

<span data-ttu-id="27304-110">[**\<Konfigurace >** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) popisuje `<configuration>` element, který je element nejvyšší úrovně pro všechny konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="27304-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="27304-111">[**\<assemblybinding – >** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Určuje zásady vazeb sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="27304-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="27304-112">[**\<linkedconfiguration – >** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Určuje konfigurační soubor, který chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="27304-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="27304-113">[Schéma nastavení spouštění](~/docs/framework/configure-apps/file-schema/startup/index.md) popisuje elementy, které určují, která verze common language runtime používat.</span><span class="sxs-lookup"><span data-stu-id="27304-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="27304-114">[Schéma nastavení běhového prostředí](~/docs/framework/configure-apps/file-schema/runtime/index.md) popisuje prvky, které konfigurují vazby a modul runtime chování sestavení.</span><span class="sxs-lookup"><span data-stu-id="27304-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="27304-115">[Schéma nastavení sítě](~/docs/framework/configure-apps/file-schema/network/index.md) popisuje elementy, které určují, jak rozhraní .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="27304-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="27304-116">[Schéma nastavení šifrování](~/docs/framework/configure-apps/file-schema/cryptography/index.md) popisuje elementy, které mapují popisné názvy algoritmů tříd, které implementují algoritmy šifrování.</span><span class="sxs-lookup"><span data-stu-id="27304-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="27304-117">[Schéma konfigurace oddílů](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) popisuje elementy používané k vytvoření a použití konfiguračních oddílů pro vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="27304-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="27304-118">[Trasování a ladění schématu nastavení](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) popisuje elementy určující přepínače trasování a posluchače.</span><span class="sxs-lookup"><span data-stu-id="27304-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="27304-119">[Schéma nastavení poskytovatele jazyka a kompilátoru](~/docs/framework/configure-apps/file-schema/compiler/index.md) popisuje prvky, které určují kompilátor konfigurace pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="27304-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="27304-120">[Schéma nastavení aplikace](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) popisuje elementy, které umožňují aplikace Windows Forms nebo technologii ASP.NET ukládat a načítat nastavení s rozsahem aplikace a nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="27304-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="27304-121">[Schéma nastavení aplikace](~/docs/framework/configure-apps/file-schema/appsettings/index.md) obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="27304-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="27304-122">[Schéma nastavení webu](~/docs/framework/configure-apps/file-schema/web/index.md) všechny elementy ve schématu nastavení webu, který obsahuje prvky pro konfiguraci spolupráce rozhraní ASP.NET s hostitelskou aplikací, například službou IIS.</span><span class="sxs-lookup"><span data-stu-id="27304-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="27304-123">Použít v *Aspnet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="27304-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="27304-124">[Konfigurační schéma pro Windows Forms](winforms/index.md) všechny prvky v konfiguračním oddílu aplikace Windows Forms, který obsahuje vlastní nastavení, jako je podpora více monitorů a vysoké rozlišení DPI.</span><span class="sxs-lookup"><span data-stu-id="27304-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="27304-125">[Konfigurační schéma služby WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) všechny elementy, které je možné nakonfigurovat služeb a klientských aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="27304-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="27304-126">[Syntaxe direktivy WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) popisuje `@ServiceHost` směrnice, který definuje atributy specifické pro stránku používané kompilátorem .svc.</span><span class="sxs-lookup"><span data-stu-id="27304-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="27304-127">[Schématu konfigurace WIF](windows-identity-foundation/index.md) všechny prvky schématu konfigurace technologie Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="27304-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="27304-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="27304-128">Related sections</span></span>

<span data-ttu-id="27304-129">[Schéma nastavení vzdálené komunikace](https://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) popisuje prvky, které konfigurují klientské a serverové aplikace, které implementují vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="27304-129">[Remoting Settings Schema](https://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="27304-130">[Schéma nastavení technologie ASP.NET](https://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) popisuje elementy, které řídí chování webových aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="27304-130">[ASP.NET Settings Schema](https://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="27304-131">[Webové služby nastavení schématu](https://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) popisuje elementy, které řídí chování webových služeb ASP.NET a jejich klientů.</span><span class="sxs-lookup"><span data-stu-id="27304-131">[Web Services Settings Schema](https://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="27304-132">[Konfigurace aplikací .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) popisuje postup konfigurace zabezpečení, vazby sestavení a vzdálené komunikace v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27304-132">[Configuring .NET Framework Apps](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
