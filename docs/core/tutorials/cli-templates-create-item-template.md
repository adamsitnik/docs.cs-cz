---
title: Vytvoření šablony položky pro dotnet New-.NET Core CLI
description: Naučte se vytvořit šablonu položky pro příkaz dotnet New. Šablony položek mohou obsahovat libovolný počet souborů.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5183781d6a131aa395cf7c1fd8a09e05ed0bd71d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926155"
---
# <a name="tutorial-create-an-item-template"></a>Kurz: Vytvoření šablony položky

Pomocí .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory i prostředky. Tento kurz je první částí série, která vás seznámí s postupem vytvoření, instalace a odinstalace šablon pro použití s `dotnet new` příkazem.

V této části série se naučíte:

> [!div class="checklist"]
>
> * Vytvoření třídy pro šablonu položky
> * Vytvoření konfigurační složky a souboru šablony
> * Nainstalovat šablonu z cesty k souboru
> * Testování šablony položky
> * Odinstalace šablony položky

## <a name="prerequisites"></a>Požadavky

* [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
* Přečtěte si referenční článek [vlastní šablony pro dotnet New](../tools/custom-templates.md).

  Referenční článek vysvětluje základní informace o šablonách a způsobu jejich spojování. Některé z těchto informací se tady opakují.

* Otevřete terminál a přejděte do složky _working\templates\\_  .

## <a name="create-the-required-folders"></a>Vytvoření požadovaných složek

Tato série používá pracovní složku, ve které je zdroj šablony obsažený, a "testovací složka" sloužící k testování vašich šablon. Pracovní složka a složka pro testování by měly být ve stejné nadřazené složce.

Nejprve vytvořte nadřazenou složku, na které název nezáleží. Pak vytvořte podsložku s názvem _Work_. V _pracovní_ složce vytvořte podsložku s názvem _Templates_.

Dále v nadřazené složce vytvořte složku s názvem _test_. Struktura složky by měla vypadat takto:

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Vytvoření šablony položky

Šablona položky je konkrétní typ šablony, která obsahuje jeden nebo více souborů. Tyto typy šablon jsou užitečné, pokud chcete vygenerovat něco jako soubor s konfigurací, kódem nebo souborem řešení. V tomto příkladu vytvoříte třídu, která přidá metodu rozšíření k typu řetězce.

V terminálu přejděte do složky _working\templates\\_  a vytvořte novou podsložku s názvem _rozšíření_. Zadejte složku.

```console
working
└───templates
    └───extensions
```

Vytvořte nový soubor s názvem _CommonExtensions.cs_ a otevřete ho ve svém oblíbeném textovém editoru. Tato třída poskytne metodu rozšíření s názvem `Reverse` , která bude měnit obsah řetězce. Vložte následující kód a soubor uložte:

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

Teď, když máte vytvořený obsah šablony, je nutné vytvořit šablonu config v kořenové složce šablony.

## <a name="create-the-template-config"></a>Vytvoření šablony konfigurace

Šablony jsou v rozhraní .NET Core rozpoznány pomocí speciální složky a konfiguračního souboru, který se nachází v kořenovém adresáři šablony. V tomto kurzu se složka šablony nachází na adrese _working\templates\extensions\\_ .

Když vytvoříte šablonu, všechny soubory a složky ve složce šablon budou zahrnuty jako součást šablony kromě speciální konfigurační složky. Tato konfigurační složka má název _. template. config_.

Nejprve vytvořte novou podsložku s názvem _. template. config_a zadejte ji. Pak vytvořte nový soubor s názvem _template. JSON_. Struktura vaší složky by měla vypadat takto:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Otevřete _template. JSON_ s oblíbeným textovým editorem a vložte následující kód JSON a uložte ho:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

Tento konfigurační soubor obsahuje všechna nastavení pro šablonu. Můžete zobrazit základní nastavení, `name` například a `shortName`, `tags/type` ale existuje také hodnota nastavená na `item`. Tato šablona kategorizuje šablonu jako šablonu položky. Typ šablony, kterou jste vytvořili, není nijak omezen. Hodnoty `item` a`project` jsou běžné názvy, které doporučuje .NET Core, aby uživatelé mohli snadno filtrovat typ šablony, kterou hledají.

Položka představuje sloupec **značky** , který se zobrazí při spuštění `dotnet new` a získání seznamu šablon. `classifications` Uživatelé můžou vyhledávat i na základě klasifikačních značek. Nepleťte `tags` si vlastnost \*v souboru `classifications` . JSON se seznamem značek. Existují dvě různé věci, které se nazývají podobně. Úplné schéma pro soubor *template. JSON* najdete v [úložišti schémat JSON](http://json.schemastore.org/template). Další informace o souboru *template. JSON* najdete v tématu [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).

Teď, když máte platný soubor _. template. config/Template. JSON_ , je vaše šablona připravená k instalaci. V terminálu přejděte do složky _rozšíření_ a spusťte následující příkaz, který nainstaluje šablonu umístěnou v aktuální složce:

* **Ve Windows**:`dotnet new -i .\`
* **V systému Linux nebo MacOS**:`dotnet new -i ./`

Tento příkaz vypíše seznam nainstalovaných šablon, které by měly obsahovat vaše.

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a>Testování šablony položky

Teď, když máte nainstalovanou šablonu položky, otestujte ji. Přejděte do složky _test/_ Folder a vytvořte novou konzolovou aplikaci pomocí `dotnet new console`nástroje. Tím se vygeneruje pracovní projekt, který lze snadno otestovat `dotnet run` pomocí příkazu.

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

Dále spusťte příkaz `dotnet new stringext` , který vygeneruje _CommonExtensions.cs_ ze šablony.

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

Změňte kód v _program.cs_ a převratte `"Hello World"` řetězec s metodou rozšíření poskytnutou šablonou.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Spusťte program znovu a uvidíte, že výsledek je obrácený.

```console
C:\test> dotnet run
!dlroW olleH
```

Blahopřejeme! Vytvořili jste a nasadili šablonu položky pomocí .NET Core. Při přípravě na další část této série kurzů musíte odinstalovat šablonu, kterou jste vytvořili. Přesvědčte se, zda jsou všechny soubory odstraněny také z _testovací_ složky. Tím se vrátíte zpět do připraveného stavu pro další hlavní část tohoto kurzu.

## <a name="uninstall-the-template"></a>Odinstalace šablony

Vzhledem k tomu, že jste nainstalovali šablonu podle cesty k souboru, je nutné ji odinstalovat s **absolutní** cestou k souboru. Seznam nainstalovaných šablon můžete zobrazit spuštěním `dotnet new -u` příkazu. Vaše šablona by měla být uvedena jako poslední. Použijte cestu uvedenou k odinstalaci šablony pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Další postup

V tomto kurzu jste vytvořili šablonu položky. Pokud se chcete dozvědět, jak vytvořit šablonu projektu, pokračujte v této sérii kurzů.

> [!div class="nextstepaction"]
> [Vytvoření šablony projektu](cli-templates-create-project-template.md)
