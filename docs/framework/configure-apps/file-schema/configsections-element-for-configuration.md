---
title: <configSections> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6024144b6f12df22369366f04c3cbad02c5011d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119017"
---
# <a name="configsections-element-for-configuration"></a>\<> configSections – element pro \<konfigurace >

Obsahuje konfigurační oddíl a deklarace oboru názvů.

[**konfigurační >\<** ](configuration-element.md)   
&nbsp;&nbsp; **\<configSections >**

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**Konfigurace \<** ](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**oddíl \<** ](section-element.md) | Obsahuje deklaraci konfiguračního oddílu. |
| [ **> \<sectionGroup**](sectiongroup-element-for-configsections.md) | Definuje obor názvů pro konfigurační oddíly. |
| [ **\<odebrat >** ](remove-element-for-configsections.md) | Odebere předdefinovanou sekci nebo skupinu oddílů. |
| [ **\<vymazat >** ](clear-element-for-configsections.md) | Vymaže všechny dříve definované oddíly a skupiny oddílů. |

## <a name="remarks"></a>Poznámky

Pokud je tento prvek v konfiguračním souboru, musí být prvním podřízeným prvkem prvku **\<> Konfigurace** .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:

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

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
