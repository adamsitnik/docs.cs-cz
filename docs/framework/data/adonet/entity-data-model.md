---
title: Entity Data Model
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 8e96890d97f652295a3fdb67c48ec37710280eec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197916"
---
# <a name="entity-data-model"></a>Entity Data Model
Entity Data Model (EDM) je sada koncepty, které popisují strukturu dat, bez ohledu na jeho uložených formuláře. Vypůjčí modelu EDM z relace Entity Model popsal Peter Svoboda v 1976, ale také založený na modelu relace Entity a rozšíří jeho tradiční použití.  
  
 EDM řeší výzvy související s daty uloženými v mnoha formách jsou vyvolány. Představte si třeba firma, která ukládá data v relačních databází, textové soubory, soubory XML, tabulky a sestavy. To představuje důležité výzvy při modelování dat, návrh aplikace a přístup k datům. Při navrhování aplikace orientované na data, před obrovskou výzvou – je efektivní a udržovatelný kód napsat bez omezení účinný data access, úložiště a škálovatelnosti. Pokud data obsahují relační struktury, jsou velmi efektivní přístup k datům, úložiště a škálovatelnosti, ale vytváření efektivní a udržovatelného kódu bude obtížnější. Pokud data obsahují objektovou strukturu, jsou obrácený kompromisy konfigurace: Zápis efektivní a udržovatelný kód obsahuje za cenu efektivní datové úložiště a škálovatelnosti. I když můžete najít správnou rovnováhu mezi těmito kompromisy, nové výzvy vzniknout, když jsou data přesouvána mezi jeden formulář do jiného. Modelu Entity Data Model řeší tyto problémy popisuje strukturu dat z hlediska entit a vztahů, které nezávisí na žádné schéma úložiště. Díky tomu formuláři uložených dat relevantní pro vývoj a návrh aplikace. A protože entitami a relacemi popisují strukturu dat, jako používá se v aplikaci (ne jeho uložené formulář), můžete vyvíjet s vyvíjí aplikace.  
  
 A `conceptual model` je konkrétní reprezentace strukturu dat jako entit a vztahů a je obecně podle jazyka specifického pro doménu (DSL), který implementuje koncepty modelu EDM. [Konceptuální schéma definici jazyka (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) je příkladem takových jazyka specifického pro doménu. Entity a relace je popsáno v konceptuálním modelu můžete představit jako abstrakce objektů a přidružení v aplikaci. To umožňuje vývojářům soustředit se na konceptuální model bez obav o schéma úložiště a umožňuje psát kód s efektivitu a udržovatelnosti v úvahu. Mezitím návrháři schéma úložiště soustředit se na efektivitu přístup k datům, úložiště a škálovatelnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Témata v této části popisují koncepty modelu Entity Data Model. Koncepty popsané tady by měl obsahovat všechny DSL, která implementuje modelu EDM. Všimněte si, že [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL používá k definování konceptuálních modelů. Další informace najdete v tématu [specifikace CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Model Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Model Entity Data Model: Primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Model Entity Data Model: Dědičnost](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [association end](../../../../docs/framework/data/adonet/association-end.md)  
  
 [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [association set](../../../../docs/framework/data/adonet/association-set.md)  
  
 [association set end](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [association type](../../../../docs/framework/data/adonet/association-type.md)  
  
 [complex type](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [entity container](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [entity key](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [entity set](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [entity type](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [facet](../../../../docs/framework/data/adonet/facet.md)  
  
 [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [model-declared function](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [model-defined function](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [navigation property](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [property](../../../../docs/framework/data/adonet/property.md)  
  
 [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Viz také:

- [Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Přehled souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Specifikace CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
