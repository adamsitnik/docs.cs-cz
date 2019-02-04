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
ms.openlocfilehash: 6ebb6487136bff567c57143e3000a20270c1f87e
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674903"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schéma konfiguračního souboru pro rozhraní .NET Framework

Konfigurační soubory jsou standardní soubory XML, které můžete použít ke změně nastavení a nastavit zásady pro vaše aplikace. Schéma konfigurace rozhraní .NET Framework obsahuje prvky používané v konfiguračních souborech pro řízení chování aplikací. Obsah této části odráží hierarchii schématu pro spuštění, runtime, síť a další typy nastavení konfigurace.

Informace o typech, formátu a umístění konfiguračních souborů, najdete v článku [konfigurace aplikace](~/docs/framework/configure-apps/index.md). Seznamte se s XML Pokud chcete upravovat konfigurační soubory přímo.

> [!IMPORTANT]
> XML tagy a atributy v konfiguračních souborech jsou malá a velká písmena.

## <a name="in-this-section"></a>V tomto oddílu

[**\<Konfigurace >** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) popisuje `<configuration>` element, který je element nejvyšší úrovně pro všechny konfigurační soubory.

[**\<assemblybinding – >** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Určuje zásady vazeb sestavení na úrovni konfigurace.

[**\<linkedconfiguration – >** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Určuje konfigurační soubor, který chcete zahrnout.

[Schéma nastavení spouštění](~/docs/framework/configure-apps/file-schema/startup/index.md) popisuje elementy, které určují, která verze common language runtime používat.

[Schéma nastavení běhového prostředí](~/docs/framework/configure-apps/file-schema/runtime/index.md) popisuje prvky, které konfigurují vazby a modul runtime chování sestavení.

[Schéma nastavení sítě](~/docs/framework/configure-apps/file-schema/network/index.md) popisuje elementy, které určují, jak rozhraní .NET Framework připojí k Internetu.

[Schéma nastavení šifrování](~/docs/framework/configure-apps/file-schema/cryptography/index.md) popisuje elementy, které mapují popisné názvy algoritmů tříd, které implementují algoritmy šifrování.

[Schéma konfigurace oddílů](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) popisuje elementy používané k vytvoření a použití konfiguračních oddílů pro vlastní nastavení.

[Trasování a ladění schématu nastavení](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) popisuje elementy určující přepínače trasování a posluchače.

[Schéma nastavení poskytovatele jazyka a kompilátoru](~/docs/framework/configure-apps/file-schema/compiler/index.md) popisuje prvky, které určují kompilátor konfigurace pro zprostředkovatele dostupných poskytovatelů jazyka.

[Schéma nastavení aplikace](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) popisuje elementy, které umožňují aplikace Windows Forms nebo technologii ASP.NET ukládat a načítat nastavení s rozsahem aplikace a nastavení uživatele.

[Schéma nastavení aplikace](~/docs/framework/configure-apps/file-schema/appsettings/index.md) obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.

[Schéma nastavení webu](~/docs/framework/configure-apps/file-schema/web/index.md) všechny elementy ve schématu nastavení webu, který obsahuje prvky pro konfiguraci spolupráce rozhraní ASP.NET s hostitelskou aplikací, například službou IIS. Použít v *Aspnet.config* soubory.

[Konfigurační schéma pro Windows Forms](winforms/index.md) všechny prvky v konfiguračním oddílu aplikace Windows Forms, který obsahuje vlastní nastavení, jako je podpora více monitorů a vysoké rozlišení DPI.

[Konfigurační schéma služby WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) všechny elementy, které je možné nakonfigurovat služeb a klientských aplikací WCF.

[Syntaxe direktivy WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) popisuje `@ServiceHost` směrnice, který definuje atributy specifické pro stránku používané kompilátorem .svc.

[Schématu konfigurace WIF](windows-identity-foundation/index.md) všechny prvky schématu konfigurace technologie Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Související oddíly

[Schéma nastavení vzdálené komunikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) popisuje prvky, které konfigurují klientské a serverové aplikace, které implementují vzdálené komunikace.

[Schéma nastavení technologie ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) popisuje elementy, které řídí chování webových aplikací ASP.NET.

[Webové služby nastavení schématu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) popisuje elementy, které řídí chování webových služeb ASP.NET a jejich klientů.

[Konfigurace aplikací .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) popisuje postup konfigurace zabezpečení, vazby sestavení a vzdálené komunikace v rozhraní .NET Framework.
