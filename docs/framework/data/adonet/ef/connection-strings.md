---
title: Připojovací řetězce v ADO.NET Entity Framework
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 55097e4977111c56cb06c590e305e31ed681fd31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606770"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>Připojovací řetězce v ADO.NET Entity Framework

Připojovací řetězec obsahuje informace o inicializaci, která je předána jako parametr od poskytovatele dat ke zdroji dat. Syntaxe závisí na poskytovateli dat a připojovací řetězec je analyzován při pokusu o otevření připojení. Připojovací řetězec používaný Entity Framework obsahují informace, které slouží pro připojení k podkladové zprostředkovatele dat ADO.NET, který podporuje rozhraní Entity Framework. Obsahují také informace o požadované modelu a souborů mapování.

Připojovací řetězec se používá zprostředkovatel EntityClient při přístupu k modelu a mapování metadata a připojování k objektu data source. Připojovací řetězec můžete přistupovat ani je nastavit prostřednictvím <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> vlastnost <xref:System.Data.EntityClient.EntityConnection>. <xref:System.Data.EntityClient.EntityConnectionStringBuilder> Třídy je možné programově vytvořit nebo získat přístup k parametrů v připojovacím řetězci. Další informace najdete v tématu [jak: Vytvoření připojovacího řetězce EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).

[Nástroje modelu Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) generovat připojovací řetězec, který je uložený v konfiguračním souboru aplikace. <xref:System.Data.Objects.ObjectContext> načte informace o tomto připojení automaticky při vytváření objektu dotazy. <xref:System.Data.EntityClient.EntityConnection> Používané <xref:System.Data.Objects.ObjectContext> instance je přístupný z <xref:System.Data.Objects.ObjectContext.Connection%2A> vlastnost. Další informace najdete v tématu [Správa připojení a transakce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce

Další informace o obecnou syntaxi pro připojovací řetězce, naleznete v tématu [syntaxe připojovacího řetězce | Připojovací řetězce v ADO.NET](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Parametry připojovacího řetězce

V následující tabulce jsou uvedeny platné názvy pro hodnoty – klíčové slovo v <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.

|Klíčové slovo|Popis|
|-------------|-----------------|
|`Provider`|Požadováno pokud `Name` – klíčové slovo není zadán. Název zprostředkovatele, který se používá k načtení <xref:System.Data.Common.DbProviderFactory> objekt pro příslušný prostředkovatel. Tato hodnota je konstantní.<br /><br /> Když `Name` – klíčové slovo není součástí připojovacího řetězce služby entity, neprázdná hodnota pro `Provider` – klíčové slovo je povinný. Toto klíčové slovo je vzájemně se vylučuje s `Name` – klíčové slovo.|
|`Provider Connection String`|Volitelné. Určuje, který je předán do podkladového zdroje dat specifické pro zprostředkovatele připojovací řetězec. Tento připojovací řetězec obsahuje dvojice platný – klíčové slovo/hodnota pro poskytovatele dat. Neplatný `Provider Connection String` způsobí chybu za běhu při vyhodnocování ve zdroji dat.<br /><br /> Toto klíčové slovo je vzájemně se vylučuje s `Name` – klíčové slovo.<br /><br /> Ujistěte se, že řídicí hodnotu podle Obecná syntaxe nástroje [připojovací řetězce ADO.NET](../../../../../docs/framework/data/adonet/connection-strings.md). Zvažte například následující připojovací řetězec: `Server=serverName; User ID = userID`. Musí být uvozena, protože obsahuje středníkem. Protože neobsahuje dvojitých uvozovek, mohou být použity pro uvození:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|Požadováno pokud `Name` – klíčové slovo není zadán. Kanál oddělený seznam adresářů, souborů a umístění prostředků, ve kterém se hledá informace mapování a metadat. Následuje příklad:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Mezer na každé straně kanálu oddělovače jsou ignorovány.<br /><br /> Toto klíčové slovo je vzájemně se vylučuje s `Name` – klíčové slovo.|
|`Name`|Aplikace můžete volitelně zadat název připojení v konfiguračním souboru aplikace, který obsahuje hodnoty požadované klíčové slovo/hodnotu připojovacího řetězce. V takovém případě je nelze zadat přímo v připojovacím řetězci. `Name` – Klíčové slovo není povolený v konfiguračním souboru.<br /><br /> Když `Name` – klíčové slovo není zahrnutý v připojovacím řetězci, neprázdný hodnoty pro zprostředkovatele – klíčové slovo je povinný.<br /><br /> Toto klíčové slovo je vzájemně se vylučuje s všechny další připojovací řetězec klíčová slova.|

Následující je příklad připojovacího řetězce pro [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) uložené v konfiguračním souboru aplikace:

## <a name="model-and-mapping-file-locations"></a>Model a mapování umístění souborů

`Metadata` Parametr obsahuje seznam umístění pro `EntityClient` poskytovatele vyhledávání modelu a souborů mapování. Modelu a souborů mapování se často nasazuje ve stejném adresáři jako spustitelný soubor aplikace. Tyto soubory můžete také nasadit v konkrétním umístění nebo zahrnutý jako vložený prostředek v aplikaci.

Vložené prostředky jsou určené následujícím způsobem:

```
Metadata=res://<assemblyFullName>/<resourceName>.
```

Pro definování umístění vložený prostředek k dispozici jsou následující možnosti:

|Možnost|Popis|
|-|-|
|`assemblyFullName`|Celý název sestavení s integrovaný prostředek. Název obsahuje jednoduchý název, název verze, podporované jazykové verze a veřejný klíč, následujícím způsobem:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Prostředky může být vložen do libovolné sestavení, která je přístupná aplikací.<br /><br /> Je-li zadat zástupný znak (\*) pro `assemblyFullName`, modul runtime rozhraní Entity Framework bude vyhledávat prostředky v těchto umístěních, v tomto pořadí:<br /><br /> 1.  Volající sestavení.<br />2.  Odkazovaná sestavení.<br />3.  Sestavení v adresáři bin aplikace.<br /><br /> Pokud soubory nejsou v jednom z těchto umístění, bude vyvolána výjimka. **Poznámka:**  Při použití zástupných znaků (*), musí si projít všechna sestavení prostředků s správný název Entity Framework. Ke zlepšení výkonu, zadejte název sestavení namísto zástupného znaku.|
|`resourceName`|Název zahrnutých prostředků, jako je například AdventureWorksModel.csdl. Metadatových služeb se jenom vyhledejte soubory nebo prostředkům s jedním z těchto přípon: .csdl, .ssdl nebo .msl. Pokud `resourceName` není zadán, se načtou všechny prostředky metadat. Prostředky by měly mít jedinečné názvy v rámci sestavení. Pokud se více souborů se stejným názvem, které jsou definovány v různých adresářích v sestavení, `resourceName` musí zahrnout před název prostředku, třeba FolderName.FileName.csdl strukturu složek.<br /><br /> `resourceName` není vyžadován při zadávání zástupný znak (*) pro `assemblyFullName`.|

> [!NOTE]
> Kvůli zvýšení výkonu se prostředky pro vložení do volajícího sestavení s výjimkou v mimo Web scénářích tam, kde není žádná reference na základní mapování a metadat souborů v volající sestavení.

Následující příklad načte všechny modelu a souborů mapování v volajícího sestavení, odkazovaná sestavení a jiných sestavení v adresáři bin aplikace.

```
Metadata=res://*/
```

Následující příklad načte soubor model.csdl ze sestavení AdventureWorks a načte soubory model.ssdl a model.msl z výchozí adresář spuštěné aplikaci.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

Následující příklad načte tři zadané prostředky z konkrétního sestavení.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

Následující příklad načte všechny vložené prostředky pomocí rozšíření .csdl, .msl a .ssdl ze sestavení.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

Následující příklad načte všechny prostředky v cestě k souboru relativní plus "datadir\metadata\\" z umístění načteného sestavení.

```
Metadata=datadir\metadata\
```

Následující příklad načte všechny prostředky v relativní cesta k souboru z umístění načteného sestavení.

```
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Podpora &#124;DataDirectory&#124; náhradní řetězec a webovou aplikaci Root (~) – operátor

`DataDirectory` a ~ – operátor se používají v <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> jako součást `Metadata` a `Provider Connection String` klíčová slova. <xref:System.Data.EntityClient.EntityConnection> Předává `DataDirectory` a ~ operátor <xref:System.Data.Metadata.Edm.MetadataWorkspace> a zprostředkovatele úložiště, v uvedeném pořadí.

|Termín|Popis|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Přeloží na relativní cesta k souborům mapování a metadat. Jedná se o hodnotu, která je nastavena prostřednictvím `AppDomain.SetData("DataDirectory", objValue)` metody. `DataDirectory` Náhradní řetězec musejí být uzavřeny do kanálu znaků a nesmí být žádné prázdné znaky mezi jeho jméno a znaky svislé čáry. `DataDirectory` Název není malá a velká písmena.<br /><br /> Pokud mají být předány jako člena seznamu cest metadat má fyzický adresář s názvem "DataDirectory", přidejte do jednoho nebo obou stranách název prázdné znaky. Například: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Aplikace ASP.NET řeší &#124;DataDirectory&#124; k "\<kořenový adresář aplikace > / app_data" složky.|
|~|Přeloží na kořenový adresář webové aplikace. ~ Znak na počáteční pozici je vždy interpretováno jako operátor kořenové webové aplikace (~), i když to může představovat platný místní podadresáře. K odkazování na místní podadresáře, musí uživatel explicitně předávat `./~`.|

`DataDirectory` a ~ – operátor by měl lze zadat pouze na začátku cesty nejsou přeložit v jakékoliv pozici. Entity Framework se pokusí přeložit `~/data`, ale bude zacházet s `/data/~` jako fyzická cesta.

Cestu, která začíná `DataDirectory` nebo ~ – operátor nelze přeložit na fyzickou cestu mimo větev `DataDirectory` a ~ – operátor. Například lze vyřešit následující cesty: `~` , `~/data` , `~/bin/Model/SqlServer`. Řešení se nezdaří následující cesty: `~/..`, `~/../other`.

`DataDirectory` a ~ – operátor je možné rozšířit na zahrnout podsložky, následujícím způsobem: `|DataDirectory|\Model`, `~/bin/Model`

Rozlišení `DataDirectory` náhradní řetězec a ~ – operátor je nerekurzivní. Například když `DataDirectory` zahrnuje `~` znaků, dojde k výjimce. To zabraňuje nekonečnou rekurzi.

## <a name="see-also"></a>Viz také:

- [Práce se zprostředkovateli dat](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
- [Důležité informace o nasazení](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Správa připojení a transakce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Připojovací řetězce](../../../../../docs/framework/data/adonet/connection-strings.md)
