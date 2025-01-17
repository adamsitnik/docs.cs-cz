---
title: Přístup k prostředkům datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: d18ec4fd57f2437ca936074e8dcf70f17f09b877
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991109"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Přístup k prostředkům datové služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)][!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] podporuje a zpřístupňuje vaše data jako informační kanál s prostředky, které jsou adresovatelné pomocí identifikátorů URI. Tyto prostředky jsou reprezentovány podle konvencí vztahů mezi entitami [model EDM (Entity Data Model)](../adonet/entity-data-model.md). V tomto modelu entity představují provozní jednotky dat, které jsou typy dat v doméně aplikace, jako jsou například zákazníci, objednávky, položky a produkty. Data entit jsou přístupná a se mění pomocí sémantiky representational state transfer (REST), konkrétně standardní příkazy HTTP GET, PUT, POST a DELETE.  
  
## <a name="addressing-resources"></a>Adresování prostředků  
 V [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]je třeba adresovat všechna data, která jsou zpřístupněna datovým modelem pomocí identifikátoru URI. Například následující identifikátor URI vrátí informační kanál, který je sadou entit Customers, která obsahuje položky pro všechny instance typu entity zákazníka:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers>
  
 Entity mají speciální vlastnosti označované jako klíče entit. Klíč entity se používá k jednoznačné identifikaci jedné entity v sadě entit. To umožňuje adresovat konkrétní instanci typu entity v sadě entit. Například následující identifikátor URI vrátí položku pro konkrétní instanci typu entity zákazníka, která má hodnotu `ALFKI`klíče:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')>
  
 Základní a komplexní vlastnosti instance entity lze také jednotlivě adresovat. Například následující identifikátor URI vrátí element XML, který obsahuje `ContactName` hodnotu vlastnosti pro konkrétního zákazníka:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName>
  
 Pokud zahrnete `$value` koncový bod do předchozího identifikátoru URI, vrátí se do zprávy odpovědi jenom hodnota primitivní vlastnosti. Následující příklad vrátí pouze řetězec "Marie Anders" bez elementu XML:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value>
  
 Vztahy mezi entitami jsou definované v datovém modelu podle přidružení. Tato přidružení umožňují adresovat související entity pomocí navigačních vlastností instance entity. Navigační vlastnost může v případě vztahu 1: n vracet buď jednu související entitu, v případě vztahu n:n, nebo v sadě souvisejících entit. Například následující identifikátor URI vrátí informační kanál, který je sadou všech objednávek vztahujících se na konkrétního zákazníka:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders>
  
 Vztahy, které jsou obvykle obousměrně, jsou reprezentovány dvojicí vlastností navigace. Jako opak vztahu uvedeného v předchozím příkladu vrátí následující identifikátor URI odkaz na entitu zákazníka, na kterou patří konkrétní objednávka objednávky:  
  
<https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer>
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]také umožňuje adresovat prostředky na základě výsledků výrazů dotazů. Díky tomu je možné filtrovat sady prostředků na základě vyhodnoceného výrazu. Například následující identifikátor URI filtruje prostředky, aby vracely pouze objednávky zadaného zákazníka, které byly odeslány od 22. září 1997:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers( ' ALFKI ')/Orders? $filter = DatumOdeslání gt DateTime ' 1997-09-22T00:00:00 ' >
  
 Další informace najdete v tématu [OData: Konvence](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)identifikátoru URI.
  
## <a name="system-query-options"></a>Možnosti systémových dotazů  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definuje sadu možností systémových dotazů, které můžete použít k provádění tradičních operací dotazů na prostředky, jako je filtrování, řazení a stránkování. Například následující identifikátor URI vrátí sadu všech `Order` entit spolu se souvisejícími `Order_Detail` entitami, poštovní kódy, `100`které nekončí:  
  
<https://services.odata.org/Northwind/Northwind.svc/Orders? $filter = not EndsWith (ShipPostalCode; ' 100 ') & $expand = Order_Details & $orderby = ShipCity >
  
 Položky ve vráceném informačním kanálu jsou řazeny také podle hodnoty vlastnosti ShipCity objednávek.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje následující [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] možnosti systémových dotazů:  
  
|Možnost dotazu|Popis|  
|------------------|-----------------|  
|`$orderby`|Definuje výchozí pořadí řazení entit ve vráceném kanálu. Následující dotaz vyřadí vracené zákazníky podle okresu a města:<br /><br /> <https://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City>|  
|`$top`|Určuje počet entit, které se mají zahrnout do vráceného kanálu. Následující příklad přeskočí prvních 10 zákazníků a potom vrátí následující 10:<br /><br /> <https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10>|  
|`$skip`|Určuje počet entit, které se mají přeskočit před začátkem vrácení entit v informačním kanálu. Následující příklad přeskočí prvních 10 zákazníků a potom vrátí následující 10:<br /><br /> <https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10>|  
|`$filter`|Definuje výraz, který filtruje entity vracené v informačním kanálu na základě určitých kritérií. Tato možnost dotazu podporuje sadu logických relačních operátorů, aritmetické operátory a předdefinované funkce dotazů, které se používají k vyhodnocení výrazu filtru. Následující příklad vrátí všechny poštovní směrovací kódy, které nekončí na 100:<br /><br /> <https://services.odata.org/Northwind/Northwind.svc/Orders? $filter = not EndsWith (ShipPostalCode; ' 100 ') >|  
|`$expand`|Určuje, které související entity jsou vráceny dotazem. Související entity jsou zahrnuté jako informační kanál nebo položka vložená s entitou vrácenou dotazem. Následující příklad vrátí objednávku pro zákazníka ' ALFKI ' společně s podrobnostmi o položce pro každé pořadí:<br /><br /> <https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details>|  
|`$select`|Určuje projekci, která definuje vlastnosti entity, které se vrátí v projekci. Ve výchozím nastavení jsou všechny vlastnosti entity vraceny v informačním kanálu. Následující dotaz vrátí pouze tři vlastnosti `Customer` entity:<br /><br /> <https://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City>|  
|`$inlinecount`|Vyžaduje, aby byl v informačním kanálu zahrnut počet entit vrácených v informačním kanálu.|  
  
## <a name="addressing-relationships"></a>Adresování vztahů  
 Kromě adresování sad entit a instancí [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] entit taky můžete řešit přidružení, která prezentují vztahy mezi entitami. Tato funkce vyžaduje, aby bylo možné vytvořit nebo změnit relaci mezi dvěma instancemi entit, jako je přepravce, který souvisí s daným pořadím v ukázkové databázi Northwind. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]`$link` podporuje operátor pro specifickou adresování přidružení mezi entitami. Například následující identifikátor URI je zadán ve zprávě požadavku HTTP PUT ke změně přepravce pro zadané pořadí na nového přepravce.  
  
<https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper>
  
 Další informace najdete v části `3.2. Addressing Links between Entries` na [OData: Konvence](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)identifikátoru URI.
  
## <a name="consuming-the-returned-feed"></a>Využívání vráceného kanálu  
 Identifikátor URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prostředku umožňuje adresovat data entity, která služba zveřejňuje. Když zadáte identifikátor URI do pole Adresa webového prohlížeče, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] vrátí se reprezentace informačního kanálu požadovaného prostředku. Další informace najdete v tématu [rychlý start WCF Data Services](quickstart-wcf-data-services.md). I když může být webový prohlížeč užitečný při testování, že prostředek datové služby vrací očekávaná data, služba produkčních dat, která může také vytvářet, aktualizovat a odstraňovat data, je obecně dostupná pomocí kódu aplikace nebo skriptovacích jazyků na webové stránce. Další informace najdete v tématu [použití datové služby v klientské aplikaci](using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Otevřít web datového protokolu](https://www.odata.org/)
